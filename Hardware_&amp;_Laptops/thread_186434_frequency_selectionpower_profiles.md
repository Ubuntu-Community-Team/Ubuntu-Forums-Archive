---
title: "frequency selection/power profiles?"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by spotman on 2006-06-01
Hello,

In suse or kubuntu (i am positive about suse, assume kubuntu is true also) there is a power applet that lets you select your desired cpu frequency and/or power profile.

In dapper I appreciate the cpu frequency monitor (panel applet), but that only displays the current mhz/ghz, it does not allow you to set it.  Dapper also features the battery/ac icon in the system tray, and if you configure it, there is options for what to do when you close your lid, etc, but an option to say "i am on battery, i want to save as much power as possible" or "I am on a/c, i need to crank this bad boy up" are not available.

In suse 10.1 I get 5 hours of battery if I am trying to save power and not using it much, under normal use, about 4.  With dapper, I hardly ever break 3 hours 20 minutes.  I don't mind suse and all, but yast is a joke, and I am familiar with ubuntu and have been using it for quite some time.  

I have been testing all this for the past bit, and this is all on the same notebook (lenovo/ibm t60)

Thanks for any input/advice/comments!

---

### Post by spotman on 2006-06-02
After digging around I think that this las less to do with ubuntu, and more to do with gnome:

[http://www.gnome.org/projects/gnome-power-manager/gpp.html](http://www.gnome.org/projects/gnome-power-manager/gpp.html)

does anyone know of a 3rd party or otherwise app that will let me control other settings such as my cpu frequency policy, my screen brightness, etc.. but especially the cpufrequency, and I see some apt packages, but which ones are compatible with gnome power manager?

---

### Post by userid on 2008-03-28
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

this always worked in dapper.. now i got it working in gutsy

just dpkg-reconfiigure as he says in his blog post, then you can left click and just select the governor or speed on the gnome panel applet :P

---

