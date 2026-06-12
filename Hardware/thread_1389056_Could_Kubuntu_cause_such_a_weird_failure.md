---
title: "Could Kubuntu cause such a weird failure?"
date: 2010-01-23
forum: Hardware
---

### Post by LuisGMarine on 2010-01-23
So I've been running Kubuntu 9.10 for some time, and recently this morning when I rebooted Kubuntu would not let me change the resolution past 640x480.  I did some researching and people told me on IRC that it could be the driver broke.  So I removed it and re-installed it and still nothing.  I tried reverting back to an older version, and still the problem persisted. 

However the weirdest thing is that now I can't connect to my monitor through DVI.  I've hooked up my laptop and it works great with my monitor.  I even hooked up my desktop to a different monitor using DVI and it still works.  However kubuntu and my DVI connect to this particular monitor just don't seem to click.

Essentially I was dropped into a terminal on boot, and I just gave up on trying to fix Kubuntu and came back to regular old Ubuntu.  Everything is working silky smooth, but I'm shocked at what just happened.

Anyone have any idea what in the world could of gone wrong?!?  I'm so lost for an explanation.  :confused:

---

### Post by adam814 on 2010-01-23
Yeah, that sounds like broken video card driver to me.  I can imagine two ways that would happen:
1) An update to the driver broke support for your card (weird, but could happen).
2) Your xorg.conf changed for some other reason (also weird if you don't remember editing it).

Either way you'll get stuck in low-graphics mode with the "vesa" driver.  If you can fix your driver and/or xorg.conf you can get it back, but I understand how it can be without a usable system.  There are those times you can reinstall faster than you can fix a stubborn problem.

AFAIK as the KDE desktop environment is the sole difference between Ubuntu and Kubuntu it could happen to either if the same circumstance that caused it occurred again.

---

### Post by LuisGMarine on 2010-01-23
The weird part it was working great, and I ran no updates nor did I make changes to my xorg file.

I'm just shocked that a simple reboot just caused the whole system to go bottoms up.  The other sad part was that I could not make a backup of all my music =(.  It would just sit there and say "copying" but no files where actually being copied.

Well in all I don't blame any of the software it just one of those weird things.  I'll just have to keep making more current backups of my Music since it's the most important part.

As far as re-installing and getting the system up and running with flash and everything has become second nature to me.  I actually enjoy doing it, which is weird.

For some reason I did things the hard way, but simply installing the restricted drivers fixed everything for me =)

---

