---
title: "HP Netraid RAID controller - booting?"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by zerhacke on 2006-05-18
I can't figure this out.

I've got a HP Netserver 4 with a NetRAID controller, this thing is old (Pentium Pro CPU, if that tells you anything).

I've been trying to figure out how to load the RAID drivers on boot before mounting the drives so that I can boot the RAID array.  So far I've come up with nothing.  My extent of experience lies with using rc.d, which obviously comes after disk mounting so that won't work.

Any pointers for a guy with some old hardware?

---

### Post by zerhacke on 2006-05-22
BUMP... anyone know anything about this?

---

### Post by dhichandler on 2006-11-04
I have 10 HP LP2000r with NetRaid 1 & 2si cards that we would like to load also, but we cannot get the RAID to be reconized. Did you everyt figure out how to do this.

---

### Post by sparehead1 on 2006-11-10
i've got a similar problem, trying to install with HP netraid.

Its similar to the cards seen here:
[http://www.lackof.org/taggart/hacking/netraid/](http://www.lackof.org/taggart/hacking/netraid/)

i've tryed telling the install to use use the megaraid, megaraid_mm and megaraid_mbox modules during the install but no joy. Thinking I may have to compile a kernel with the options listed on that page but then im not sure how to get an install going with the new kernel, guessing I'll have to make my own install cd :-?

---

### Post by coach-x on 2006-11-22
Good info sparehead1, i also have hp megaraid (lh 3000)  I have never gotten ubuntu to see the card.  I did get it working with SuSE, currently using 9.3.

---

### Post by sparehead1 on 2006-12-19
okies not really a fix but just thought you may like to know that my megaraid card works fine with debian aslong as I install with the 2.6 kernel

---

### Post by RX7Godfather on 2007-02-26
I've also got a similar problem with my HP NetRAID 1Si card, can get 6.10 to recognize it as a MegaRAID card, ubuntu appears to install correctly but upon reboot it just sits there. Have tried every Flavor of UBUNTU and 6.10 is the only one that see's it, appears to install the OS just fine but then doesn't recognize it's own partition it created upon reboot...

Have also tried 6.06, and 6.10 SERVER editions but those won't even see that I have a SCSI card installed.

What really sux is that a lot of these posts out here are very old and none of the experts from UBUNTU seem to be responding to any of them.....

I really like what I see with UBUNTU and was finally really excited about going to LINUX but can't seem to get any support at all on these issues. I have seen many people say that they can get them to work with other flavors of LINUX, (Debia, Suse, Fedora etc) but I wanted to use UBUNTU....

So please, please, experts from UBUNTU, can you please give us some help?????

---

### Post by RX7Godfather on 2007-02-27
OK, I may have found an answer, at least it is working for my NetRAID 1Si SCSI controller.

You need to enter the bios of your scsi card, usually Ctrl+M while booting, locate somewhere in your scsi config utility the emulation section, you may have to dig for it, I know I did....

Change your SCSI emulation from I20 to MASS STORAGE, erase your array (you will lose everything on your drives) and rebuild and initialize it. This way Ubuntu will not see multiple installations and will erase the entire disks.

After doing that, try to install it again, so far it is working with my NetRAID 1Si controller.

Hope this helps...

---

### Post by unngh on 2007-08-29
The switch from I20 to MASS STORAGE worked on my system.

---

