---
title: "Help me get rid of the orange theme"
date: 2008-09-10
forum: General Help
---

### Post by Louis de Broglie on 2008-09-10
Hi,

I really don't like the default orange theme in hardy. 

I looked into gnome-look and gnome art. They have some cool themes. But installing them seemed too complicated to me:(

For example, to get that appealing result that i see many users in this has forum has got, you need the theme, the icons and others which i don't know. 

Can you share your experience with me and help me get cool desktop like yours ? :lolflag:

---

### Post by ooobuntooo on 2008-09-10
> **Louis de Broglie said:**
> Hi,

I really don't like the default orange theme in hardy. 

I looked into gnome-look and gnome art. They have some cool themes. But installing them seemed too complicated to me:(

For example, to get that appealing result that i see many users in this has forum has got, you need the theme, the icons and others which i don't know. 

Can you share your experience with me and help me get cool desktop like yours ? :lolflag:

*right click*>Change Desktop Background>Theme>drag the downloaded theme into the box with the other themes.

Same for Icons etc..

For Emerald themes you need Emerald Theme Manager and you can use that to import themes.

---

### Post by Neobuntu on 2008-09-10
> sudo apt-get install kubuntu-desktop

:)

---

### Post by Louis de Broglie on 2008-09-10
I installed emerald. Then downloaded this package : 

[http://www.gnome-look.org/content/show.php/Aqua+aero.?content=72934](http://www.gnome-look.org/content/show.php/Aqua+aero.?content=72934)

Then imported it using emerald. But nothing happens.:confused:

---

### Post by robz0rz on 2008-09-10
You're probably still using Metacity. Metacity and Emerald are two different "window decorators", programs that control the way your window borders look through themes.


In order to run Emerald, press Alt+F2 and type in ```
emerald --replace
```

If you feel like going back to Metacity, press Alt+F2 again, and this time type in ```
gtk-window-decorator --replace
```

---

### Post by Louis de Broglie on 2008-09-11
Thanks it worked.:)

---

