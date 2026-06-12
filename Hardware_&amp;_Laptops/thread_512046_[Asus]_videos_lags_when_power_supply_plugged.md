---
title: "[Asus] videos lags when power supply plugged"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by lexma on 2007-07-28
I'm experiencing a very strange issue with feisty. When i'm running my Asus A6VA laptop on the battery, everything is ok, but when i plug the power supply the videos (no matter X11, Xv ....) start to slow and lag, and my whole computer seems to run slower ... it's even more strange when we know that the cpu is working at 800mhz on batteries and at 1700mhz on power supply . Is anyone able to help me ?

---

### Post by wsmoser2004 on 2007-07-29
lexma-

Wow, that certainly is counter-intuitive.  However I've noticed that on my laptop, Ubuntu seems to "save" certain tasks for when the laptop is plugged in.  For example, there's a process called 'updatedb' that scans my disks and creates a database of the files on it for when I use the 'locate' command.  However it only runs when the laptop is plugged in, presumably to save battery power.

Maybe the next time it happens, open up a terminal and type 'top.'  That shows a partial process list of what's running.  To sort by CPU usage, do Shift-O (the letter O) and then hit the letter for "% CPU usage" in the screen that comes up.  (Hit enter to exit that screen then.)  Hopefully that will give you some insight into what's consuming all of your CPU.

If you're using KDE, Ctrl-Esc also brings up a graphical process list, I don't know if that works for Gnome though...

---

### Post by lexma on 2007-08-03
Thank you for your answer, but i haven't noticed any modifications in the list of running process  when i plug or not the supply.. it doesn't seems to be the right way.

I was wondering if it wasn't a mistake in the power management of my ati X700, ubuntu may decrease the power of the graphic chip when plugged, but i haven't found anything to investigate that way. It's strange because even if the CPU usage is highter on batteries (because of the lowest frequency) the entire computer seems faster, that's why i'm thinking of a mistake in the ati power management feature.

---

### Post by lexma on 2007-08-05
The power management of the ATI X700 doesn't seems to be guilty finaly, when i make a glxgears test, the fps is the same when the power supply is plugged or not (about 4200 fps). This issue is becoming more and more freeky... perhaps the synchronisation of the screen ? (how can i enable the v-sync). The CPU is not in cause because it's load is always above 100%.

PS: how can i manage the modification that occurs between the plugged and battery mode ? this would helpful to understand what happen to that damn laptop !!!

---

### Post by jdk_ on 2007-08-29
I've got the same problem: everything goes very slow when my laptop is plugged to the mains, everything is ok when it is on the battery. The difference is overwhelming in boot time, for instance.

I've got a Vaio FS315M with an nvidia card, so as much as I think we have the same issue, I don't think it is related to the video cards.

Any help would be much appreciated!

---

### Post by jdk_ on 2007-08-29
(EDITED!)

Hi again,
I kept looking around and found this:

[http://ubuntuforums.org/showthread.php?t=509984&highlight=slow+battery](http://ubuntuforums.org/showthread.php?t=509984&highlight=slow+battery)

I think the option pci=assign-busses may help. I haven't been able to try it yet but you may want to check it out.

To try it enter the grub menu when starting the laptop and having the Ubuntu option highlighted, press the 'e' key, then highlight the kernel line and add pci=assign-buses at the end, then you can boot the kernel pressing 'b'.

If it works well, then you may want to make it permanent by editing your grub configuration accordingly at /boot/grub/menu.lst and running: sudo update-grub
(see [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) for details)

---

### Post by Weird Al on 2007-10-18
pci=assign-busses didn't work for me. I'm having the same problem, slightly different model - Vaio VGN-FS415M

Intruiguingly, it didn't happen before I reinstalled (I think!), which itself happened because my disk crashed and burned. It doesn't seem to have anything to do with ACPI - I turned ACPI off to see. It seems to be directly related to hardware. When the power is in, the video slows down. No processes change and no events appear in dmesg.

(Edits)

Well I just checked my battery and it's 11.5V. The power supply is 19.5V. It's been suggested to me that perhaps the power supply is too high! Well I would reject this outright if it weren't for the fact that I've just had the motherboard replaced in here and I seem to have been given a different one from what I used to have, so perhaps 11.5V is correct for this... I have no way of testing it on an 11.5V power supply without invalidating the warranty on the 19.5V one. So, everyone, check your batteries! If there's such a large discrepancy between the two it may be we're onto a winner with that theory.

I'm going to find a Windows disk so I have something to send back to Sony, should the need arise. Luckily I just got myself a new hard disk so I can taint this old one to my heart's content.

---

