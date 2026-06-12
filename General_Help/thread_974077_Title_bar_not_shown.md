---
title: "Title bar not shown"
date: 2008-11-07
forum: General Help
---

### Post by sionghua on 2008-11-07
sometimes the title bar is hidden, see attached, how to solve this?

---

### Post by keplerspeed on 2008-11-07
Seems like a windows decorator issue. do you have compiz enabled? possibly try a different theme, system>preferences>appearance and select a different theme. I had similar issues with ubuntu 8.04 with the default theme.

---

### Post by sionghua on 2008-11-07
No compiz not enabled, tried human-clearlooks theme still the same, solved with crux theme, is this considered a bug?

---

### Post by dhtj on 2008-11-07
I had the same problem when I enable the desktop effects.
When desktop effects are disabled the titlebar is showing.
I use for windows decorator "Gtk window decorator" and i have installed emerald too
When I change the theme, problem is still runing ;(

---

### Post by zipperback on 2008-11-07
> **sionghua said:**
> No compiz not enabled, tried human-clearlooks theme still the same, solved with crux theme, is this considered a bug?

I looked at your screenshot that you provided.

Thats a similar problem that I encounter on occasion.

I believe that compiz is active on your system.

Next time that happens type the following into a terminal window.

> 
killall compiz.real &
metacity --replace &


That will disable compiz for your current session.

If the display resets itself and the titlebars suddenly appear, then YES you're having the same problem that I was, and YES it is compiz related somehow.

- zipperback
:popcorn:

I hope this helps you.

---

### Post by sionghua on 2008-11-07
same problem after changed theme, solved with all visual effect disabled.

---

