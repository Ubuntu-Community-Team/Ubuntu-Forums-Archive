---
title: "System unbootable"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by warwon on 2009-04-29
So I converted my ext3 to ext4, after having other issues ( the steps seemed easily enough and were all followed).

The system sits at Grub loading now.

Just great, I did a root (hd0,1) and setup (hd0,1) and nothing.

Any ideas?

---

### Post by graysky on 2009-04-29
You very likely need to use an updated grub to boot the ext4 root partition.  You can probably use the one included on the live CD.  BTW, if you just converted an ext3 partition to ext4, don't expect to see any speed gains.  See [this post](http://bbs.archlinux.org/viewtopic.php?id=71132).

---

### Post by warwon on 2009-05-02
So I found that I was able to repair grub after a few tries.

Once I got to the kernel menu I wasn't able to select the newest one.

So I manually edited the boot up to start the new kernel which support ext4.

At that point I rebuilt a number of system drivers, wireless, video etc.

I was able to finally get the drive as rw, not just r.

I did a few other things, I was able to recover 100%, got wireless, and lan working; also on ext4.

---

### Post by andreika73 on 2009-05-04
> **warwon said:**
> So I found that I was able to repair grub after a few tries.

Once I got to the kernel menu I wasn't able to select the newest one.

So I manually edited the boot up to start the new kernel which support ext4.

At that point I rebuilt a number of system drivers, wireless, video etc.

I was able to finally get the drive as rw, not just r.

I did a few other things, I was able to recover 100%, got wireless, and lan working; also on ext4.
[COLOR=black][FONT=Verdana]Hi there warwon and everybody else who might see this. I'm going crazy over this thing here. I am trying to install Ubuntu Studio ( I have tried 9.04, 8.10 and 8.04.1 which supposed to work on low memory machines) on HP 753N, Intel(R)Pentium 4, 2.53 GHz, x86, 32-bit OS (XP Professional-works fine) and 1GB memory. The installation finishes up just fine and when I reboot the system the first time, it goes up loading Ubuntu Studio letters almost to the end and then just freezes up.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]It always stops at the same spot. In other words, I haven't been able to start the system, not even once. I have Hard Drives on the PC and install Ubuntu Studio on one HD using the whole disk of 80 GB hoping that having 2 OSs on 2 separate disks would give some pluses. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]It seems like you somehow resolved the problem. Can you plz help me do the same, so I can get my mind out of this nightmare? Guys, plz take me out of this misery! [/FONT][/COLOR][COLOR=black][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thank you in advance, Andrei[/FONT][/COLOR]

---

### Post by andreika73 on 2009-05-04
[COLOR=black][FONT=Verdana]Hi there everybody who might see this. I'm going crazy over this thing here. I am trying to install Ubuntu Studio ( I have tried 9.04, 8.10 and 8.04.1 which supposed to work on low memory machines) on HP 753N, Intel(R)Pentium 4, 2.53 GHz, x86, 32-bit OS (XP Professional-works fine) and 1GB memory. The installation finishes up just fine and when I reboot the system the first time, it goes up loading Ubuntu Studio letters almost to the end and then just freezes up.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]It always stops at the same spot. In other words, I haven't been able to start the system, not even once. I have Hard Drives on the PC and install Ubuntu Studio on one HD using the whole disk of 80 GB hoping that having 2 OSs on 2 separate disks would give some pluses. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]It seems like you somehow resolved the problem. Can you plz help me do the same, so I can get my mind out of this nightmare? Guys, plz take me out of this misery! [/FONT][/COLOR][COLOR=black][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thank you in advance, Andrei :)[/FONT][/COLOR]

---

