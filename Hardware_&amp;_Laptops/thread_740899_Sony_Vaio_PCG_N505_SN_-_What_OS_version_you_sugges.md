---
title: "Sony Vaio PCG N505 SN - What OS version you suggest?"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by djole_nisam_ja on 2008-03-31
The link for specification is [here]("http://www.berndnoetscher.de/notebook.html")

---

### Post by mikemunsil on 2008-03-31
Mandrake worked on mine. Don't know if Mandriva will.

---

### Post by giancast on 2008-05-14
I just installed XUbuntu 8.04, it is working fine. My computer is PCGN505VE, i do not know if it is the same as SN. Mine is very small/thin external CDROM, USB floppy, only 64Mb of memory and 6GB hd. It runs fast, considering, SKYPE works (never did in Win98), I only need to get my wireless card working and I will be set.

---

### Post by djole_nisam_ja on 2008-05-14
> **giancast said:**
> I just installed XUbuntu 8.04, it is working fine. My computer is PCGN505VE, i do not know if it is the same as SN. Mine is very small/thin external CDROM, USB floppy, only 64Mb of memory and 6GB hd. It runs fast, considering, SKYPE works (never did in Win98), I only need to get my wireless card working and I will be set.

Man, I just cannot believe you are running the latest Xubuntu on this machine I tried Xubuntu 7.10 and it was way too slow.

But Xubuntu 6.06 LTS is doing the great job.

Thanks anyway, already have decided...Xubuntu 6.06.

---

### Post by giancast on 2008-05-15
I started with 6.06 and it was fine. Ubuntu ran slow (Gnome was the culprit) that is why I went the Xubuntu route. I do not need speed all I need is internet and VOIP for when traveling. You cannot beat this machine. Small and light. I do not want to travel with a brick. Xubuntu says that this machine supports up to 1GB of memory (?) I will keep researching to see if it is true, and if so I may upgrade my memory, this may improve the speed issue.

---

### Post by kerry_s on 2008-05-15
how's your linux skills?

dsl should work->
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

if you have a fair amount of knowledge then a debian custom install is fantastic. use the net installer to install a base, then build up from there.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at package selection uncheck everything
log in as root
install X-> apt-get install xserver-xorg-video-neomagic xorg

install a light wm, fluxbox is the most common-> apt-get install fluxbox menu

that's enough to get you to the gui
type> exit 
to log out of root
log in as your user
type> startx

thats the basics to start, you'll need a file manager, text editor, web browser, etc...
you'll want to setup auto log in to.

---

### Post by djole_nisam_ja on 2008-05-16
> **giancast said:**
> I started with 6.06 and it was fine. Ubuntu ran slow (Gnome was the culprit) that is why I went the Xubuntu route. I do not need speed all I need is internet and VOIP for when traveling. You cannot beat this machine. Small and light. I do not want to travel with a brick. Xubuntu says that this machine supports up to 1GB of memory (?) I will keep researching to see if it is true, and if so I may upgrade my memory, this may improve the speed issue.

I think that's too much memory for this Komputer.:-) And that it isn't possible.

> **kerry_s said:**
> how's your linux skills?

dsl should work->
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

if you have a fair amount of knowledge then a debian custom install is fantastic. use the net installer to install a base, then build up from there.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at package selection uncheck everything
log in as root
install X-> apt-get install xserver-xorg-video-neomagic xorg

install a light wm, fluxbox is the most common-> apt-get install fluxbox menu

that's enough to get you to the gui
type> exit 
to log out of root
log in as your user
type> startx

thats the basics to start, you'll need a file manager, text editor, web browser, etc...
you'll want to setup auto log in to.

Thank man. You were helpful, will try probably (time is limitation factor).

P.S. My linux skill's are average...soo.

---

### Post by kerry_s on 2008-05-16
average is close enough. use this then->
```
apt-get install xserver-xorg-video-neomagic xorg fluxbox menu mc dillo iceweasel rungetty

run> update-menus
```

fluxbox= wm
mc= filemanager & editor
dillo= light web browser, very limited, great for browsing fast, uses very low resources
iceweasel= the golden standard

rungetty is for your auto log in
as root:
mcedit /etc/inittab

1:2345:respawn:/sbin/getty 38400 tty1
to
1:2345:respawn:/sbin/rungetty tty1 --autologin user

"user" needs to be your log in name

as user:
mcedit ~/.bash_profile

put
startx

at the bottom

---

### Post by giancast on 2008-05-21
> **djole_nisam_ja said:**
> I think that's too much memory for this Komputer.:-) And that it isn't possible.



Thank man. You were helpful, will try probably (time is limitation factor).

P.S. My linux skill's are average...soo.
You are correct. Everything that I have been able to find out says that the max memory is 128MB. I am ok with it. Fast enough for my needs.

---

