---
title: "At login usb keyword and moese don't work"
date: 2008-10-13
forum: Hardware
---

### Post by Alessiogian on 2008-10-13
Dear all,

I installed ubuntu 8.04 on my new desktop (Acer aspire M3641, intel dual core 2 E2200, 4 GB ram, Ati radeon HD 3450) putting as "boot option" **NOAPIC**

the installation was ok, but now when i turn on the pc and arrives the login page, my usb keyboard and mouse don't work (so i can't log on).

I saw in the bios that:

> USB Controller     [Enabled]
Legacy USB Support [Enabled]
USB Keyboard Legacy Support  [Enabled]
USB Mouse Legacy Support   [Enabled]
USB Storage Device Support  [Enabled]

Sometimes the pc stopping loading ubuntu showing

```
Starting bluetooth
```

but, sincerely, i don't have it.

I'm tring to install a new version but i got error such as:

```
can't allocate usb-2, Error 110
```

and it does with usb-3, 4, 5.... and so on.

Is there anybody can help me?

thanks in advance

best regards

---

### Post by Alessiogian on 2008-10-13
little up

hope someone can help me

---

### Post by VOK1973 on 2008-11-05
Similar here. W/O install options I have had the following results: 

(K)Ubuntu (8.04 & 8.10) hang up dead when trying to talk to Bluetooth (which existance I am not aware of). 

Mandriva unsuccessfully talks to some USB devices then asks for confirmation of the stop and stucks dead there because the USB keyboard is not working; 

OpenSuse just hangs up behind a graphic screen; 

Acer call support acts as a flight of Dogberts.

It seems the problem is wider than the distro level. Acer M3641 is a good desktop where Vista soars freely. Unfortunately it seems the I have left with no choice of OS.

---

### Post by Alessiogian on 2008-11-05
> **VOK1973 said:**
> Similar here. W/O install options I have had the following results: 

(K)Ubuntu (8.04 & 8.10) hang up dead when trying to talk to Bluetooth (which existance I am not aware of). 

Mandriva unsuccessfully talks to some USB devices then asks for confirmation of the stop and stucks dead there because the USB keyboard is not working; 

OpenSuse just hangs up behind a graphic screen; 

Acer call support acts as a flight of Dogberts.

It seems the problem is wider than the distro level. Acer M3641 is a good desktop where Vista soars freely. Unfortunately it seems the I have left with no choice of OS.

Infact now i'm using vista & XP in dual boot, but i would like to use ubuntu as i done in the last 2 years.
I hope that someone can help us

---

### Post by VOK1973 on 2008-11-06
I've managed to get some progress. I have got the live session alive (not exactly kicking) with Ubuntu 8.10 using the following boot options: noapic nousb. The results are modest in that my monitor (22" Acer whatever) is not recognized and only works in 800X600@61Hz mode while an external usb drive with a ton of needed legacy files is not seen at all.

The pale goat screen theme kind of sucks but I shall continue the quest.

---

### Post by Alessiogian on 2008-11-06
> **VOK1973 said:**
> I've managed to get some progress. I have got the live session alive (not exactly kicking) with Ubuntu 8.10 using the following boot options: noapic nousb. The results are modest in that my monitor (22" Acer whatever) is not recognized and only works in 800X600@61Hz mode while an external usb drive with a ton of needed legacy files is not seen at all.

The pale goat screen theme kind of sucks but I shall continue the quest.

I can't use nousb 'cause my keyboard and mouse are usb plugged.

I saw in the web a lot of people have the same problem.

Hopefully we can fix this problem ASAP.

Thanks for your replies, man

Regards

---

### Post by VOK1973 on 2008-11-06
>>I can't use nousb 'cause my keyboard and mouse are usb plugged.

Well, mine are usb plugged as well, and they work after 'nousb'. Apparently, the support of usb input devices is organized below the level of OS (you can browse your bios, right?).

---

### Post by Alessiogian on 2008-11-06
> **VOK1973 said:**
> >>I can't use nousb 'cause my keyboard and mouse are usb plugged.

Well, mine are usb plugged as well, and they work after 'nousb'. Apparently, the support of usb input devices is organized below the level of OS (you can browse your bios, right?).

Yes, I can do it!

But can you install ubuntu or not after the live?

---

### Post by Alessiogian on 2008-11-11
> **VOK1973 said:**
> I've managed to get some progress. I have got the live session alive (not exactly kicking) with Ubuntu 8.10 using the following boot options: noapic nousb. The results are modest in that my monitor (22" Acer whatever) is not recognized and only works in 800X600@61Hz mode while an external usb drive with a ton of needed legacy files is not seen at all.

The pale goat screen theme kind of sucks but I shall continue the quest.

Ok

I used noapic nousb and it works. I have to check if everything works but if I want to add a resolution in the xorg.conf, how can I do it?

Thanks

---

### Post by VOK1973 on 2008-11-13
Yep, our wining now seems slightly less warranted than it did a week before. 

To recap: 
1) forget "nousb" - this self invented option does remove the block of the system on the stage of talking to bluetooth, but it freezes later on anyway. So no use.

2) adding noapic at the end of the command line at the install time (and later on editing the menu.lst of grub in the same way) lets the system work with 800X600 display

3) installing the proprietary closed-source drivers from NVidia turns the X223w monitor into an almost proper screen. I have 1650X1050 on 54Hz (it's 61Hz under Vista) under ubuntu now.

4) The good old external usb drive of mine is not yet recognised, but i did not do much yet on it either.

Do you get any more progress?

---

### Post by jbird32275 on 2009-01-29
All right I got it. Go into your 
BIOS -> Advanced BIOS Features -> Installer OS Select
Change it to "Other"

No noapic or nousb or anything. Live CD works as well as install.

Now someone tell me how to configure this video card!!! :(

**UPDATE**
Here's a link to installing the video driver:
[http://ubuntuforums.org/showthread.php?t=1054232](http://ubuntuforums.org/showthread.php?t=1054232)

---

