---
layout: page
title: News
---

<div class="news-section">
  <h2>Latest News & Publications</h2>
  
  <p>Stay updated with my latest research publications, conference presentations, and announcements.</p>
  
  <div class="news-feed">
    {% assign news_posts = site.posts | where_exp: "post", "post.categories contains 'news' or post.categories contains 'publications' or post.categories contains 'announcements'" %}
    
    {% if news_posts.size > 0 %}
      {% for post in news_posts %}
        <article class="news-item">
          <h3 class="news-title">
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </h3>
          <div class="news-meta">
            <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date_to_string }}</time>
            {% if post.categories %}
              <span class="news-category">• {{ post.categories | first }}</span>
            {% endif %}
          </div>
          <p class="news-excerpt">{{ post.excerpt | strip_html }}</p>
        </article>
      {% endfor %}
    {% else %}
      <p class="no-news">No news items yet. Check back soon for updates!</p>
    {% endif %}
  </div>
  
  <div class="news-categories">
    <h3>Categories</h3>
    <ul>
      <li><a href="/news/publications/">Publications</a></li>
      <li><a href="/news/conferences/">Conferences</a></li>
      <li><a href="/news/announcements/">Announcements</a></li>
    </ul>
  </div>
</div>
