---
title: "Installing Intel Embedded Graphics Drivers (IEGD) Help..."
date: 2010-04-23
forum: Hardware
---

### Post by Espionage724 on 2010-04-23
[http://www.nanoant.com/linux/compiling-kernel-iegd-10x-module-for-any-linux-distribution](http://www.nanoant.com/linux/compiling-kernel-iegd-10x-module-for-any-linux-distribution)

This guide seems to be pretty awesome, but I'm still not 100% sure about it, and I just feel that I'll get an error somewhere...

Has anyone here Installed IEGD on Linux? I really would like to try these drivers...

---

### Post by cgriffith on 2010-04-24
I have installed IEGD 10.3.1.  There is a moblin ivi final release image you can use that has the drivers already installed.  I personally used archlinux.

Here are the issues.  

[LIST=1]
[*]Currently, you still have to use kernel 2.6.31 and xserver 1.6.
[*]There is no suspend/hibernate
[*]You can only watch videos with vaapi patched mplayer built with libva 0.29 support.  I have yet to get this combo to compile and work.
[/LIST]
With a proper installation, 2d perfermance is fantastic.  Flash player 10.x is supposed to provide vaapi version for linux soon, but as of now, you can not watch HD videos thru this player.  I have heard that the next release will coincide with next Meego release and thus will support kernel 2.6.32 and xserver 1.8.  Not sure if suspend issues will be fixed by then.  So I would say if you have a spare partition, try it out for testing purposes and get some experience with installing the IEGD drivers so that when the next release comes out, you can have a better option overall.

---

### Post by Espionage724 on 2010-04-24
THanks but I still would like to try it out on my hardware on Ubuntu

---

### Post by Espionage724 on 2010-04-25
So, anyone have any ideas?

---

### Post by Espionage724 on 2010-04-25
Anyone?

---

### Post by Espionage724 on 2010-04-28
bump

---

### Post by Espionage724 on 2010-04-29
bump

Also I tried doing this on my own yesterday and failed. Idk what I didn't do right either...

---

### Post by simhavcs on 2010-06-15
Hi,

Can you please provide your processor and chipset....

IEGD won't support for kernel version more than 2.6.24.3, 
check the iegd feature matrix from this link...[http://edc.intel.com/Download.aspx?id=1903](http://edc.intel.com/Download.aspx?id=1903)

---

