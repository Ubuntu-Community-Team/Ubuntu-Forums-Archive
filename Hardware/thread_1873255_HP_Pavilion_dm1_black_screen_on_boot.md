---
title: "HP Pavilion dm1 black screen on boot"
date: 2011-11-01
forum: Hardware
---

### Post by L0ngsh0t on 2011-11-01
Hi everybody, I've  done a clean install of Ubuntu 11.10 on my HP Pavilion dm1 from a USB disk. The installation seemed to work fine. When I power on, 
 
1. I get the flashing prompt on a black screen for a second or two, 
2. the usual instructions to hit escape for the boot menu appears,
3. Flashing prompt again for a second
4. The top half of the screen might flash with a colour for a split second (red, green or purple usually)
5. The screen backlight appears to turn off, and no activity is indicated, but the computer is definitely still running (power light on, fan running).
 
Very occasionally I might get as far as the GRUB boot menu. Selecting "Ubuntu, with Linux 3.0.0-12-generic" causes the screen to turn off as it usually does. Recovery mode seems to load fine (I get a "Recovery Menu" on a purple background), however selecting "resume" from here shows a prompt for a second, and then turns the screen off.
 
So basically it seems that whenever Ubuntu tries to boot, the screen turns off and the computer seems to sit idle.
 
My only idea was that there was a video compatability issue with the AMD e-300 APU, but I read [this post]("http://ubuntuforums.org/showthread.php?p=11257691&highlight=dm1#post11257691") on the laptop compatability list, which indicates that this system works fine, at least on 11.04.

---

### Post by tors on 2011-11-01
Yeah, I'm running 11.04 Xubuntu on my HP Pavillion DM1-3110eo.
Now I think I'll wait a bit with upgrading to 11.10...

Please let me know if you come up with something you want to compare or something and I'll see if I can be of assistance.

---

### Post by L0ngsh0t on 2011-11-02
I just installed 11.04, and I'm having the exact same problem as before.

---

### Post by Redblade20XX on 2011-11-02
I've got a dm1 installed with 11.10 and everything worked out of the box. Did you try and boot from grub with the kernel parameter "NOMODESET"? Also what version of the dm1z you have?

- Red

---

### Post by JeTDoG on 2011-11-02
Running into a similar problem on a new (purchased within the last 30 days) Pavilion g7-1260us. When I first tried to install, I was getting a black screen the second the live CD entered the Ubuntu GUI. Pressing F3 turned the backlight back on, and the install proceeded flawlessly.

At this point, the only time I have the problem is the backlight immediately turns off between the OS selection from the GRUB2 menu and the appearance of the actual login prompt. F3, backlight turns on, and everything works fine. I haven't yet tried the NOMODESET switch, but it's worth a try.

---

### Post by L0ngsh0t on 2011-11-02
> **Redblade20XX said:**
> I've got a dm1 installed with 11.10 and everything worked out of the box. Did you try and boot from grub with the kernel parameter "NOMODESET"? Also what version of the dm1z you have?
 
- Red
 
I don't know where to check which version of the computer I have. It is a netbook, if that narrows it down. 
As for GRUB, it's a small miracle if I get as far as the GRUB boot menu. Provided I can get that far, how do I fiddle with the kernel parameters?
 
Hitting F3 seems to do nothing, unfortunately. I really would love for there to be a magical button that fixed my problems...
 
I'm new to Ubuntu, and I'm sticking with "this is an unusual case, it really is a good system", despite the cynicism of my family.
 
Thanks all for the support.

---

### Post by Redblade20XX on 2011-11-02
> **L0ngsh0t said:**
> I don't know where to check which version of the computer I have. It is a netbook, if that narrows it down. 
As for GRUB, it's a small miracle if I get as far as the GRUB boot menu. Provided I can get that far, how do I fiddle with the kernel parameters?
 
Hitting F3 seems to do nothing, unfortunately. I really would love for there to be a magical button that fixed my problems...
 
I'm new to Ubuntu, and I'm sticking with "this is an unusual case, it really is a good system", despite the cynicism of my family.
 
Thanks all for the support.

Since you've stated that the problem occurs before the os gets control of the system, it may be a hardware problem. Can you try and install windows to see if anything changes? If it is a hardware problem then either it will show the same result.

- Red

---

### Post by brunoferreira on 2011-11-02
Hi, Im using a Pavilion DM 1 3250 with Ubuntu 11.10 64b works fine except the touchpad.
Did you try boot with with usb sticky and switch to boot config to runlevel 3 ?

---

