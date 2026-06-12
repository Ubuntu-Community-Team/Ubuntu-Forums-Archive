---
title: "Multimedia keys on thinkpad T60 don't work"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by thexander on 2007-06-13
I've got tpb (XEvents set to off) and xmodmap running at the same time. tpb lets me use the "ThinkVantage" button to launch a program, but the multimedia keys work incorrectly.

When I try to configure a shortcut, and it tells me to press the key combination I want to use, I push Fn+Up or whatever combination and the program will show me the correct keystroke. However, when I try to use that key stroke outside of the configuration dialog, nothing happens.

Attached is a picture of the Amarok configuration window as an example. All the XF86 Keys are my configured media keys. They look to be configured fine, but when I press them nothing happens.

anyone have a fix to this problem?

---

### Post by thexander on 2007-06-13
bump... anyone know anything about this?

---

### Post by BrowneR on 2007-06-22
If its just your multimedia buttons you are having problems with then its a known issue and this should sort you out. 

I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

