---
title: "I have to &quot;STARTX&quot; manually everytime??"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2006-02-10
Hi..

I did a server install of 5.10 on a comp..
I then installed "xfce" desktop enviroment..

Whne I restart or power down, i have to type "startx" every time to get into the GUI..
Is there a way to make it automaticaly load the GUI? 
Could someone fill me in on how to accomplish this..
thanx again..

---

### Post by Brunellus on 2006-02-10
sudo apt-get install gdm

---

### Post by floyd27 on 2006-02-10
What will that accomplish?
Wont that just install Gnome? That is not what I want

---

### Post by bluevoodoo1 on 2006-02-10
how about this?

[http://ubuntuforums.org/showthread.php?t=120692&highlight=gdm](http://ubuntuforums.org/showthread.php?t=120692&highlight=gdm)

---

### Post by Brunellus on 2006-02-10
gdm will not install gnome.  it will install the gnome display manager--what you're looking for is a display manager.

If gdm is too much, you can use xdm

---

### Post by az on 2006-02-10
wdm is also nice and light.  It has more features (okay, one more) than xdm.

---

### Post by floyd27 on 2006-02-10
From reading that link above..
Do I have to install the ubuntu desktop (gnome)
I dont have the disk space for that..

can I just install GDm and that will give me a display manager..

I have a old comp..
P3 600mhz 128 mb ram..

I was trying to install a "lite" distro of linux. People told me to do a server install of ubuntu with "xfce"
Im having soo much trouble with it.
Nothing starts automaticaly.. Internet/display manager/
So im looking to either fix these problems or find another distro to install?
any ideas..
thanx

---

### Post by bluevoodoo1 on 2006-02-10
[QUOTE=floyd27]
I have a old comp..
P3 600mhz 128 mb ram..

I was trying to install a "lite" distro of linux. 
thanx[/QUOTE]

Why not just stick with what you have and type "startx". Seems like it can't get any lighter than that, no?


and with that link, the author says:

"For this, we will need an existing Gnome installation. if you don't already have gnome installed you can just: apt-get install ubuntu-desktop"

So it seems like, yes, you have to get ubuntu-desktop that way.

---

