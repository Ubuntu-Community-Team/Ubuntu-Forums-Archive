---
title: "Printer daemons not working (Ubuntu 5.10)"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by runlevel0 on 2005-12-01
I'm having quite a mess with the printer drivers hpoj, hplip and cupsys. My hardware is an HP PSC 1315, or 1310 series, as the last 5 is a zone code for Europe...

I have been unable to print anything w/o having to restart all the daemons and even then it's not granted that gnome's printing system will be willing to collaborate.

Note that I'm perfectly able to tweak stuff onto FUBAR or make things work in a "do-it-yourself" fashion, but my idea migrating to Ubuntu was to keep things clean and neat at least for a few weeks ;)

I know that I need to modprobe the needed modules and setup the initscripts so that hplip, hpoj and cupsys are started at boot time and in the correct order. So my here question is:

How can I do this in a proper Ubuntu fashion?

Or shall I use the classical debian approach and simply simlink 
the initscripts to the corresponding /etc/rc2.d/ script?

TIA.

P.D.: I forgot to say that I'm a newbie Gnome user as I have been using almost exclusively KDE from version 0.9.

---

### Post by metoo on 2005-12-05
Setting up hpoj (oj4215) on another machine was a joy for me. Actually on breezy the hpoj driver is booted by default. There should not be a problem (haha).
You only need one of the two hp drivers you mentioned, right?

Is your hardware supported via hpoj? Check on [www.linuxprinting.org](www.linuxprinting.org) . If yes I would try to re-install the package.

With my laser printer, I have the problem, that the permissions on /dev/lp0 and /dev/usb/lp0 are not set properly when the printer is not on during boot. They are set to root/lp and need to be lp/lp. So when I fire it up later, I have to re-set the permission and re-start the printer (cups) nothing else.
But I don't even know, whether the hpoj uses these devices.

---

### Post by runlevel0 on 2005-12-05
Hmmm, this is funny, my hardware is supported by *both* drivers.
Thanks for the answer, now I only need to see which driver I like betted (IMHO HPLIP).
Windoze peopel can say what they want, but let them try to beat this: We have 2 drivers for a device, and both of them official, ROFLMAO...

My printer is one of those multi-use scanner-printer-fotocopier. Great buy indeed, I love it.
HPLIP is also used by the scanners, isn't it?

Well, as this is Ubuntu and not Gentoo I will simply see which one fits best and keep it. I love binary distros, ^_^

---

