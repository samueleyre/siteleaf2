---
title: Articles
permalink: "/articles/"
layout: page
---


<section class="section">
  <div class="container">
    {% for post in paginator.articles %}
      <article class="media">
        <div class="media-content">
          <h1 class="title">
            <a href="{{ post.url | absolute_url }}">{{ post.title }}</a>
          </h1>
          <h2 class="subtitle">
            {{ post.date | date: site.date_format }}
          </h2>
          <div class="content">
            <div class="field">
              {{ post.excerpt }}
            </div>
            <div class="field">
              <div class="level">
                <div class="level-left">
                  <a class="button is-secondary" href="{{ post.url | absolute_url }}">Read more...</a>
                </div>
                <div class="level-right">
                  {% include share-button.html %}
                </div>
              </div>
            </div>
          </div>
        </div>
      </article>
    {% endfor %}
  </div>
</section>

<section class="section">
  <div class="container">
    <nav class="pagination is-centered" role="navigation" aria-label="pagination">
      {% if paginator.previous_page %}
        <a href="{{ paginator.previous_page_path }}" class="pagination-previous">Previous</a>
      {% else %}
        <a class="pagination-previous" disabled>Previous</a>
      {% endif %}
      {% if paginator.next_page %}
        <a href="{{ paginator.next_page_path }}" class="pagination-next">Next</a>
      {% else %}
        <a class="pagination-next" disabled>Next</a>
      {% endif %}
      <ul class="pagination-list">
        {% for page in (1..paginator.total_pages) %}
          {% if page == paginator.page %}
            <a class="pagination-link is-current">{{ page }}</a>
          {% elsif page == 1 %}
            <a class="pagination-link" href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">{{ page }}</a>
          {% else %}
            <a class="pagination-link" href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
          {% endif %}
        {% endfor %}
      </ul>
    </nav>
  </div>
</section>