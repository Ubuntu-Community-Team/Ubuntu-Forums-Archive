---
title: "Dell Inspiron 6000 wireless woes"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by joepotter on 2006-02-03
I need to make a Dell Inspiron 6000 dual boot with win-XP. The internal wireless card *must* work so the box can run a projector for a small school in either win or Ubuntu.

The wireless card is a "1470 Dual Band WLAN Mini-PCI" by Broadcom and I have followed the how-to to the letter. I can not get iwconfig to even see that darn thing. Others report that they can, so there is a mystery here.

Perhaps the driver downloaded from the Dell site is the trouble? Dell fouling up Linux on purpose would not be surprising, but I think I would have read of it by now.

The driver on win is BCMWL5.sys and that is what I downloaded from Dell.

I have used ndiswrapper in the past without issue --- I see no way to make this work as I am getting no errors, but I can see no card in iwconfig.

Any ideas?

---

### Post by snowjunkie on 2006-02-03
I have an inspiron 6000 also and wireless works great out of the box.  I dual boot with XP.

The card you mention is not familiar though.  I have some kind of intel 2200 card.  Any ideas why we don't have the same cards? Was your card some kind of Dell upgrade?

---

### Post by joepotter on 2006-02-03
[QUOTE=snowjunkie]I have an inspiron 6000 also and wireless works great out of the box.  I dual boot with XP.

The card you mention is not familiar though.  I have some kind of intel 2200 card.  Any ideas why we don't have the same cards? Was your card some kind of Dell upgrade?[/QUOTE]


As you may know, Dell picks various hardware components at different times depending on the fluctuating price from the manufacturers.

You have a card made by Intel and I have one by a *Linux-hostile* company named Broadcom.

I must use ndiswrapper, but "ndiswrapper -l" tells me that bcmwl5 is there as well as driver and hardware --- yet the system sees nothing.

Be glad you have an intel card.

---

### Post by hw-tph on 2006-02-03
[QUOTE=joepotter]I need to make a Dell Inspiron 6000 dual boot with win-XP. The internal wireless card *must* work so the box can run a projector for a small school in either win or Ubuntu.

The wireless card is a "1470 Dual Band WLAN Mini-PCI" by Broadcom and I have followed the how-to to the letter. I can not get iwconfig to even see that darn thing. Others report that they can, so there is a mystery here.

Perhaps the driver downloaded from the Dell site is the trouble? Dell fouling up Linux on purpose would not be surprising, but I think I would have read of it by now.

The driver on win is BCMWL5.sys and that is what I downloaded from Dell.

I have used ndiswrapper in the past without issue --- I see no way to make this work as I am getting no errors, but I can see no card in iwconfig.

Any ideas?[/QUOTE]

Is the module even loaded? Try **sudo modprobe ndiswrapper** and if it's already loaded have a look at your **dmesg** output to see if any errors are reported.

FYI, the [bcmxx driver](http://bcm43xx.berlios.de/) is actually usable by now but it might be a little tricky to get it going with Breezy. It will most likely be included in Dapper.


Håkan

---

### Post by LightsOut on 2006-02-03
[QUOTE=snowjunkie]I have an inspiron 6000 also and wireless works great out of the box.  I dual boot with XP.

The card you mention is not familiar though.  I have some kind of intel 2200 card.  Any ideas why we don't have the same cards? Was your card some kind of Dell upgrade?[/QUOTE]

Hey I also have a dell laptop with the intel card and a linksys wireless router. Do you have to restart your router everytime you switch from Linux to XP, or does it work for both OSs w/o restarting the router?

---

### Post by klett on 2006-02-04
Hi,

I've got a Broadcom card too, although it's not the same model. I remember reading something about the files required to get the card working: I think you also need the bcmwl5.inf file placed in the same folder. In fact, I have copied  the folder which comes with the recovery cd with all it files  inside, although I tell ndiswrapper to load the bcmwl5.inf (instead of bcmwl5.sys).
Have you checked if it recognizes the hardware?
ndiswrapper -l should show "driver present, hardware present"


Good  luck!

---

### Post by joepotter on 2006-02-07
[QUOTE=hw-tph]Is the module even loaded? Try **sudo modprobe ndiswrapper** and if it's already loaded have a look at your **dmesg** output to see if any errors are reported.

FYI, the [bcmxx driver](http://bcm43xx.berlios.de/) is actually usable by now but it might be a little tricky to get it going with Breezy. It will most likely be included in Dapper.


Håkan[/QUOTE]


I can put Dapper on the laptop if that would work better. How would this help me?

---

### Post by joepotter on 2006-02-07
[QUOTE=klett]Hi,

I've got a Broadcom card too, although it's not the same model. I remember reading something about the files required to get the card working: I think you also need the bcmwl5.inf file placed in the same folder. In fact, I have copied  the folder which comes with the recovery cd with all it files  inside, although I tell ndiswrapper to load the bcmwl5.inf (instead of bcmwl5.sys).
Have you checked if it recognizes the hardware?
ndiswrapper -l should show "driver present, hardware present"


Good  luck![/QUOTE]

I have this exactly -- driver present, hardware present -- but iwconfig shows nothing.

---

### Post by beowulf on 2006-02-08
I am cross-posting this thread here as it seems to be about the same issue

[http://ubuntuforums.org/showthread.php?t=126716](http://ubuntuforums.org/showthread.php?t=126716)

---

### Post by Starman on 2006-02-08
I have the same wireless card on a latitude D400. Previous times I installed breezy ndiswrapper worked fine but now it doesn't. sudo modprobe ndiswrapper results in this:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

