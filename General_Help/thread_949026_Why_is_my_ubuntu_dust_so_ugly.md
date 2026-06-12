---
title: "Why is my ubuntu dust so ugly?"
date: 2008-10-15
forum: General Help
---

### Post by robcalewar on 2008-10-15
I just tried to install the Dust-0.2 theme and the window border looks fine, however the insides look ugly. heres a screenshot. Can someone help me? Is there a certain engine I need to install?

[[IMG]http://img413.imageshack.us/img413/3277/screenshot1tu5.th.png[/IMG]](http://img413.imageshack.us/my.php?image=screenshot1tu5.png)[[IMG]http://img413.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Genius314 on 2008-10-15
It's either one of two things:

A: Install the Murrine engine:
> sudo apt-get install gtk2-engines-murrine

OR

B: The programs can't find the theme. Copy /home/username/.themes/Dust to /usr/share/themes/Dust (you need root privileges).

Hope that helps.

---

### Post by RuarriS on 2008-10-15
Trying running the appearance program as root:

```
 sudo gnome-appearance-properties %F 
```

Then install the theme and select it.

---

### Post by robcalewar on 2008-10-16
tried both and still not working. :(

---

### Post by perlluver on 2008-10-16
Looks like it is trying to use the Aurora engine, which isn't available by default.  Go to System>Preferences>Appearance Then click customize under theme, and see if on the firs tab, if it says it is using dust-aurora, and switch it to dust.

---

### Post by robcalewar on 2008-10-16
I've tried doing what you said, perlluver and this is what I come up with
[URL="http://i35.tinypic.com/2rfy4yb.png"]
[IMG]http://i35.tinypic.com/2rfy4yb_th.png[/IMG][/URL]

and thats with the "dust" not "dust aurora"

---

### Post by perlluver on 2008-10-16
> **robcalewar said:**
> I've tried doing what you said, perlluver and this is what I come up with
[URL="http://i35.tinypic.com/2rfy4yb.png"]
[IMG]http://i35.tinypic.com/2rfy4yb_th.png[/IMG][/URL]

and thats with the "dust" not "dust aurora"

Looks a lot like mine, other than it is blue, and mine is red.  Have you tried the newer version from the Ubuntu Artwork Team Page?

---

### Post by robcalewar on 2008-10-16
[https://wiki.ubuntu.com/Artwork/Incoming/DustTheme?action=AttachFile&do=view&target=Dust-0.2.tar.gz](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme?action=AttachFile&do=view&target=Dust-0.2.tar.gz)

That's the link I download the theme. I'm pretty sure .2 is the latest. This picture here is what I was trying to achieve;
[[IMG]http://img157.imageshack.us/img157/8248/290553455761e19a41d7blp3.th.jpg[/IMG]](http://img157.imageshack.us/img157/8248/290553455761e19a41d7blp3.jpg)

---

### Post by perlluver on 2008-10-16
On this page download the Burnt, Sand and bordered extras, and then try again: [https://wiki.ubuntu.com/Artwork/Incoming/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme), not sure which I am using.  

Edit: I am using Dust Burnt.

---

### Post by robcalewar on 2008-10-16
Wow that's weird, I had to install the Murrine engine listed on that site to get it working, well thanks a lot for your help!

---

### Post by gjoellee on 2008-10-16
This is a common issue to about all the "non-default" themes you ma find for Ubuntu!

---

### Post by perlluver on 2008-10-16
> **robcalewar said:**
> Wow that's weird, I had to install the Murrine engine listed on that site to get it working, well thanks a lot for your help!

You are most welcome, please mark as Solved.

---

### Post by forger on 2008-10-16
are you using hardy or intrepid?

Here's a screenshot in intrepid:
[ATTACH]88559[/ATTACH]

---

### Post by redman5087 on 2009-08-27
I have also a problem with dust sand.
I installed the theme but some windows look nice but some don't.
An example of an ugly firefox and a good looking nautilus

---

### Post by redman5087 on 2009-08-28
the problem seems to be related to
[https://bugs.launchpad.net/ubuntu/+source/gnome-themes-extras/+bug/215472]("http://https://bugs.launchpad.net/ubuntu/+source/gnome-themes-extras/+bug/215472")
I changed the settings with tooltip but this doesn't help


Upon reboot, the GTK elements of the theme are broken (including scroll bars, gnome panel menu items, dialogs, buttons, etc) -- they revert to a simplistic, gray, and squarish style.

---

