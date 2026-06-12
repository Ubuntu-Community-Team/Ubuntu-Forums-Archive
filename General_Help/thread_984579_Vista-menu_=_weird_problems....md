---
title: "Vista-menu = weird problems..."
date: 2008-11-16
forum: General Help
---

### Post by Virtualboxbuntu on 2008-11-16
Hello everybody,

I have converted my parents to Linux Mint. They are okay with everything except that they would prefer the Windows XP or Vista look & feel. I've tried to copy XP as much as I can using various different window, icon and cursor themes.

To get the XP-style cursor to work properly, I had to go to ccsm and use the flat backend or whatever it is. So I log out of my parents' account and back in, and everything works fine, except there are no window borders. No Minimize/Maximize/Close, nothing like that. So I go back to ccsm and choose the Gconf backend. 

The window borders are now back to normal, but if I log out and back in, the vista-menu (it can look like XP's menu so it's very important) disappears. Everything is normal, except there's no Start button. Same thing if I use flat backend but with emerald --replace added in Sessions.

What's wrong with vista-menu? Why can't it coexist with window borders? What can I do about it?

Thanks in advance! :)

---

### Post by QB89Dragon on 2008-12-08
I made this from the remains of the now incompatible vista menu source, and it is a lightweight implementation of the XP part of the menu. It should give you almost none of the issues you were having before and be a fair bit faster.

[http://www.gtk-apps.org/content/show.php/XP+Start+Menu?content=93807]("http://www.gtk-apps.org/content/show.php/XP+Start+Menu?content=93807")

Vista menu will resurface as gnomenu in a few months.

---

