---
title: "Strange html page"
date: 2008-11-03
forum: General Help
---

### Post by Nonno Bassotto on 2008-11-03
I'm trying to customize Konqueror start page for a live cd I am creating. It seems that the default page is located under
```

/usr/share/apps/konqueror/about/launch.html

```
The problem is that I don't understand how to edit that page since each content is replaced by a %1
For example you have
```

<td valign="bottom">
<a href="%1">
<img src="%1" height="%1" width="%1" /></a>
</td>
<td valign="bottom">
<a href="%1">%1</a>
<br>
<span id="subtext"><nobr>%1</span>
</td>

```
and so on.

What do all these %1 mean?

---

### Post by dcstar on 2008-11-03
> **Nonno Bassotto said:**
> I'm trying to customize Konqueror start page for a live cd I am creating.
........

Ignore it and just create you own HTML page.

---

### Post by Nonno Bassotto on 2008-11-03
Well, it should work as the normal splash page for Konqueror, except for the Help about Kubuntu section, so I'd rather understand where these %1 take their content and change just this little bits (two links and two labels).

---

