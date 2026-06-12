---
title: "GRUB error 21"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by hafunui on 2006-01-24
I just installed Ubuntu 5.10 on my computer. I have WinXP on my Master drive, and Linux on my Slave Drive ( both drives are on the same cable btw ) And on the first reboot I got a blank screen saying this:

> GRUB Loading stage1.5.


GRUB loading, please wait...
Error 21

Thats it. It then locks up. Right now, I'm using the live cd and I can't really do much. 

What should I do!?

I did a google search but all I found out was that it seems to be a common problem and some people fixed it by changing some sorta config file (?) 
I dunno what it all means. I only got the CDs today.

Please help. And keep in mind im quite new to this.

---

### Post by az on 2006-01-24
[QUOTE=hafunui]I just installed Ubuntu 5.10 on my computer. I have WinXP on my Master drive, and Linux on my Slave Drive ( both drives are on the same cable btw ) And on the first reboot I got a blank screen saying this:






Thats it. It then locks up. Right now, I'm using the live cd and I can't really do much. 
[/QUOTE]

Grub error 21 means that there is a bug in the motherboard's bios.  Grub runs and uses the bios' information about where things are.  Once the linux kernel is loaded, it works around a number of bios bugs.  Grub does not get the benefit of that.

Error 21 means that it is looking for the boot directory in  a certain place but cannot find it.
[QUOTE=hafunui]

What should I do!?

I did a google search but all I found out was that it seems to be a common problem and some people fixed it by changing some sorta config file (?) 
I dunno what it all means. I only got the CDs today.

Please help. And keep in mind im quite new to this.[/QUOTE]

From the live cd, you can try to change (switch around) the devices in /boot/grub/device.map. Put /"hda" where "hdb" is and "hdb" where "hda" is, for example.

You can also try to edit the grub arguments when you boot.  Hit escape if you never get to see the grub menu and "e" to edit an entry.

---

### Post by tseliot on 2006-01-24
You might as well update to the latest bios for your motherboard and see if it makes ant difference (it did the trick for me).

---

### Post by cvcaelen on 2006-01-24
I get that GRUB error 21 too, sometimes, and sometimes not.
Just restarting does the trick for me,
so
I don't bother about it anymore
but reading it's a Bios-bug kinda worries me, allthough I have to admit that it's an old PC : PIII, 550Mhz, 512RAM.
I searched for "bios-flashing"but that scares me alot.
Everything is well backed-up, so when it crashes i'll just have to go and buy a new one I guess

Christiaan

---

### Post by az on 2006-01-24
[QUOTE=cvcaelen]I searched for "bios-flashing"but that scares me alot.
[/QUOTE]
Be afraid.  Be very afraid.  Every single time I have had to do it, it has been a leap of faith.  (Closes eyes and hits "enter" *Gulp*)

---

### Post by hafunui on 2006-01-24
It seems the primary drive 1 was auto while the second was NONE. So changing that to auto aswell fixed it right up. Thank You!

---

