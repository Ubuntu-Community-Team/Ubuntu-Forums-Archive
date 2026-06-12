---
title: "Custom PC will not boot?"
date: 2011-09-10
forum: Hardware
---

### Post by brightlights on 2011-09-10
Hello,

I am really hoping someone can help me with this. Suddenly, my computer will not boot. A couple of days ago I added a second hard disk with ubuntu on it, and set up dual boot. This morning it tried to boot into Ubuntu and it made a loud clicking noise. I disconnected the 2nd hard disk, then Windows 7 was able to boot off of the main hard disk seemingly fine. 

My computer automatically hibernates, so later this afternoon it was off, and I'm unable to get it to boot. It lights up and makes sounds, but then turns off, and does this over and over again until it dies. I really don't know what to do next.

My entire PC build is only a couple of months old.

---

### Post by Blasphemist on 2011-09-10
An option is for you to download this iso and burn it to CD or USB. [http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

When you first run it you can un-check everything except create boot info summary. Then copy the web page address that it gives you and post it back here for us to review. 

It does sound like the Ubuntu drive may be belly up. It's not good when they make that noise. I can't tell from what you describe what the problem is but this summary gives a lot of good info.

---

### Post by brightlights on 2011-09-10
I burned the ISO to CD, and I am trying to boot off of the CD drive. It continues to turn on, then shut off, and repeat until I unplug it. Nothing on the monitor comes up at all.

I opened it up and everything looks okay to me. Is that book repair ISO bootable?

---

### Post by Blasphemist on 2011-09-10
It is bootable. Does any cd or usb boot? It also normally wouldn't cycle to reboot too. I wonder if you are having a power problem.

---

### Post by brightlights on 2011-09-10
This is odd. I couldn't get the Boot Repair ISO disk to boot (maybe the CD I burned is bad?), but I switched around some SATA cables (the SATA cable to the Windows hard drive was at the very bottom slot so I moved it above the DVD Drive one). I replaced one of the SATA cables with a completely new one. Somehow I got it to boot. It might have just been coincidence.

GRUB came up, and I chose Windows 7. It shut off after about 2 minutes in Windows. I re-boot again, and now I'm in Windows again and it hasn't shut off yet.

Are there any diagnostics that I can do to see if this is power-related or if it's a hardware failure?

Thanks.

---

### Post by Blasphemist on 2011-09-10
You could download and burn this. [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

In the hard disk section of this page you'll see a number of tools that can help determine the health of hard disks.

---

