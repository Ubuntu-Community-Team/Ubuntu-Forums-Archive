---
title: "gtkrc - force alternating row colours"
date: 2008-10-13
forum: General Help
---

### Post by HyperHacker on 2008-10-13
I set the rules in my .gtkrc-2.0 to have alternating row colours for lists:```
style "default"
{
GtkTreeView::odd_row_color = "#FFFFFF"
GtkTreeView::even_row_color = "#F0F0FF"
}

class "GtkWidget" style "default"
```

This only affects certain programs; others are using the even colour for every row. The GTK+ documentation says it's possible to force this:
> This function tells GTK+ that the user interface for your application requires users to read across tree rows and associate cells with one another. By default, GTK+ will then render the tree with alternating row colors. Do not use it just because you prefer the appearance of the ruled tree; that's a question for the theme. Some themes will draw tree rows in alternating colors even when rules are turned off, and users who prefer that appearance all the time can choose those themes. You should call this function only as a semantic hint to the theme engine that your tree makes alternating colors useful from a functional standpoint (since it has lots of columns, generally).So how do I do this in .gtkrc-2.0?

---

