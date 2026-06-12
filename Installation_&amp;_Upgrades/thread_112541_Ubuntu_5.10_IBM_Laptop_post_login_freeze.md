---
title: "Ubuntu 5.10 IBM Laptop post login freeze"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by krypticus on 2006-01-04
I just received a used IBM ThinkPad 600X from my friend, and I wiped the 12 GB drive and installed Ubuntu 5.10 on it. Now it installed without problems, and the first time I went to log in, it froze with a brown/black screen right after it confirmed the correct login and password. 

I can ctrl-alt-F1 and get to a terminal, but I do not know how to fix the freeze problem. I opened up the /var/log/syslog as someone mentioned, but I didn't see anything that I could assume was a problem (I'm a newb).

 I tried the "date" fix, but my time and date are for 2006, so that wasn't the case. I have a Pentium 3, i think its a 700 mhz. Any help would be greatly appreciated! 

(Btw, no connection to the internet or network, since I still need to buy a USB wireless stick since the normal card ports don't work).

- Thanks!

---

### Post by mips on 2006-01-04
Do a search for **Thinkpad 600** on these forums and you'll find lots of posts and I'm pretty sure they will cover your problems.

You sure your cardbus slots dont work ? Maybe try adding the kernel line "acpi=off" in grub /boot/grub/menu.lst

Display:
[http://ubuntuforums.org/showthread.php?t=109667](http://ubuntuforums.org/showthread.php?t=109667)

Let us know how it goes...

---

### Post by mips on 2006-01-05
Or maybe just look at this, [http://ubuntuforums.org/showthread.php?t=96240](http://ubuntuforums.org/showthread.php?t=96240)

---

### Post by Murf on 2006-02-19
I am at the same point as you are with my 600X. I get to the login screen, select a Session type and enter my user name and password. I just get a black screen and cursor. I was assuming it was a failure to load X windows due to a screen setting. I tried the posted suggestion on setting the default depth to 16 in /etc/X11/xorg.conf but that did not help. If I try to run a program like /usr/games$ gataxx I get the error.....(gataxx:7040) Gtk-WARNING **: cannot open display     So I still suspect some display setting.

---

