---
title: "aterm transparency"
date: 2008-08-21
forum: General Help
---

### Post by 19bab79 on 2008-08-21
i am having a little trouble getting my aterm transparency to work properly. i have put aterm in the lower right hand corner of my desktop, but it displays the upper left hand corner of my desktop. i am posting my .Xdefaults below. here is a [screenshot]("http://i523.photobucket.com/albums/w358/19bab79/Screenshot3.png") so you can see exactly what i am talking about. any help would be greatly appreciated as google has turned up nothing after two days of searching.

```
aterm*geometry: 70x20+750+500
aterm*transparent: true
aterm*scrollBar: false
aterm*borderLess: true
aterm*internalBorder: 0
aterm*borderWidth: 0
```

---

### Post by conundrumx on 2008-08-21
Aterm appears to be doing exactly what you want.  It is in the bottom right corner, with no scrollbar or decorations.  Conky is in the upper left.  Is that what you mean?

---

### Post by 19bab79 on 2008-08-21
if you look at the image that the transparency is using, it is using the image of the upper left hand corner of my wallpaper. it needs to be using the lower right hand corner of my wallpaper. here is the [wallpaper]("http://i523.photobucket.com/albums/w358/19bab79/Shattered_Concentration_by_narada.jpg") i am using. notice it doesn't show what it is supposed to.

---

### Post by 19bab79 on 2008-09-18
the problem has been fixed. last night i ran updates and when i rebooted this morning the proper portion of desktop was showing behind aterm. updates fixed the problem.

---

