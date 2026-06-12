---
title: "Upgrade to 9.10 - No Sound - No Touchpad + More"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Brahmanskarma on 2009-10-30
Jaunty was awesome, and I figured I would upgrade to Karmic to increase me Ubuntu capabilities. After I upgraded I found I had no sound, no touchpad, incorrect colors for videos. I fixed some items.

I used a modprobe command to get the touchpad working. The Touchpad worked flawlessly in Jaunty. After my upgrade the touchpad didn't work and in the Mouse Preferences I do not have a "Touchpad" tab. I would like to get my edge scrolling working again.

I would also like to get my sound working as well. I fixed the color by launching Totem and selected "default" in the color section. The Hue tab went directly to the middle and know works in all my players again.

So my main fixes at this point are Touchpad to actually show up or get edge scrolling to work. And to get my sound back.

I am using a Compaq Presario CQ60, AMD Athlon x2, Nvidia Graphics. Thank you in advance for your help!

---

### Post by 5BallJuggler on 2009-10-30
I have a similar issue, what modprobe command did you use to fix it?

Thanks 
Phil

---

### Post by 5BallJuggler on 2009-10-30
Fixed by calling a previous linux kernel in menu.lst

change default call from 2 to 0

was calling this
Ubuntu 9.10, kernel 2.6.28-15-generic

now calling this
Ubuntu 9.10, kernel 2.6.31-14-generic


Hope this helps someone else.
Phil

---

### Post by Brahmanskarma on 2009-10-31
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe was the command I used. I think I did sudo su or something weird. Sudo does not have enough permission. Then I rebooted. The touchpad works, but doesn't have the tabs and everything in Mouse preferences. I am going to try to use an earlier linux kernel as well now.

---

### Post by JTCA on 2009-10-31
I have this problem too.  Can't seem to get a good fix.  Anyone got ideas?

---

### Post by Andybr2000 on 2009-10-31
I have the same problems with my Dell laptop
Upgraded from Ubuntu 9.04 to 9.10 Karmic
Kernel Linux 2.6.27-9-generic
GNOME 2.28.1
Dell laptop E1505
Memory: 2.5GiB
Processor 0: Intel T2300 @ 1.66GHz    25%
Processor 1: Intel T2300 @ 1.66GHz   100%
Available disk space: 8.5GiB
Help please

---

### Post by 5BallJuggler on 2009-10-31
> **Andybr2000 said:**
> I have the same problems with my Dell laptop
Upgraded from Ubuntu 9.04 to 9.10 Karmic
Kernel Linux 2.6.27-9-generic
GNOME 2.28.1
Dell laptop E1505
Memory: 2.5GiB
Processor 0: Intel T2300 @ 1.66GHz    25%
Processor 1: Intel T2300 @ 1.66GHz   100%
Available disk space: 8.5GiB
Help please

let us have a look at your menu.lst file, 

it's in /boot/grub,

post the text in to a code box (click on #) at the top of the screen

---

### Post by alexbia on 2009-12-21
Same problem after upgrading from 9.04 to 9.10 on an Advent netbook (MSI Wind clone):

I couldn't do it with sudo and the echo command. Gives error message:
bash: /etc/modprobe.d/psmouse.modprobe: Permission denied

I've just opened gedit with sudo to get root rights: >sudo gedit
wrote the text "options psmouse proto=exps" into the editor (no quotation marks please)
and then saved it to /etc/modprobe.d/psmouse.modprobe
creating the psmouse.modprobe file
then I rebooted and the touchpad was working.

---

### Post by alexbia on 2009-12-21
Now I've just discovered the cause of the problem in my case.
I have 3 operating systems installed in 3 different partitions: Windows XP, Ububtu 9.10 (recentrly upgraded from 9.04), and Ubuntu Netbook Remix 9.04, installed in this order.
The problem was that the menu.lst that grub uses at boot time is taken from the last OS installed (Ubuntu Netbook Remix). This list of the third OS was not automatically updated when I upgraded the Ubunbtu of the second installation. So it still said Ubuntu 9.04 in the menu (this is not the problem), and loaded Linux Kernel 2.6.28.11 (this was the problem).
So the solution was to boot the Ubuntu 9.10 of the second upgraded installation. Then I copied the /boot/grub/menu.lst file to a USB flash drive. The restarted the computer, now booting with the 3rd OS (Ubuntu Netbook Remix). I've opened both the menu.list under /boot/grub of the 3rd OS, and the menu.lst from the USB memory. I fixed and saved the menu list of the Ubuntu Netbook Remix, changing the kernel version to the one used by 9.10. Don't copy the entire menu-lst from USB memory to disk, since the menu.lst of the 3rd OS may have some other options that would be lost by an entire overwrite.
I finally rebooted, and both the mouse and audio were fixed. I've also discovered very nicew compiz effects on my netbook that were not working with the 2.6.28.11  kernell.

---

### Post by witsend on 2011-02-23
Had the same sound and touchpad problems the fix that worked for me was in another forum somewhere 

Attach a mouse go to System>Administration>Synaptic Package Manager
Install grub-pc
This shows all the kernel versions on rebooting
choose the latest kernel available
everything should now work

---

