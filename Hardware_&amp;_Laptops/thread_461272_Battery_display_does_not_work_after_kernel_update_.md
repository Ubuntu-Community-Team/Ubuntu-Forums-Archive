---
title: "Battery display does not work after kernel update to 2.6.20-16"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by Empedokles on 2007-06-01
Hello,

I'm using an Acer Notebook TravelMate 4002 WLMi with Kubuntu 7.04. With the original kernel version 2.6.20-15 that comes with feisty the KDE application "Power Manager" shows me the battery status and the cpu clock frequency. Everything works fine.

Since I've updated the kernel to 2.6.20-16, only the display for the clock frequency works correctly. Unfortunately the new kernel isn't able to find any batteries, and the detection of the power supply for plugging in and out also doesn't work since the update.

I've posted this problem in my native language in the german ubuntuusers.de forum. There is another person with the same notebook with the same problem and without any idea too.

Can anyone help us?

---

### Post by joncheyne on 2007-06-02
Only to say that quite a few others have this too, on gnome too.

On gnome, if you add applets to the panel, there is another applet there that works fine, although without adjusting power saving properties - at least you know your battery status. 

acpi -V

will also tell you your status in a terminal.

I think we just have to wait for this one to work it's way though the bug fix stage - have you posted or contributed to a bug?

Cheers

Jon

---

### Post by Freiburg05 on 2007-06-02
Hi there, 

    I'm one of those others with the problem, and with a very similar laptop (the specifications are in my signature). I have to say that the other applet you can add to the panel doesn't work either, at least not for me. These other thread deals with the same problem: 
[http://ubuntuforums.org/showthread.php?t=457417]("http://ubuntuforums.org/showthread.php?t=457417")

The problem is already been reported to launchpad, but I think we'll have to wait for a new kernel update.

   Bye!

---

### Post by mr bob on 2007-06-03
I had a similar problem but maybe slightly different. 

I was getting a plug icon only and there was no indication of the battery at all (gnome). I tried acpi -V in the terminal and was told acpi isn't supported. I realised that my laptop is quite old and I have to add "acpi=force" in
/boot/grub/menu.lst for grub to boot up with acpi support.

Once I edited menu.lst everything was fine again.

---

### Post by Freiburg05 on 2007-06-03
Hi

acpi -V returns for me this:

:~$ acpi -V
     Thermal 1: ok, 44.0 degrees C

I've tried to apply your solution but still nothing (I really didn't expect to work, but I had nothing to lose). Thanks for the tip anyway.

---

### Post by neis on 2007-06-04
Someone already filed a bug on this issue. Please add your comments to the launchpad thread at:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117773)

Let's hope someone will pick this up.

---

### Post by stchman on 2007-06-04
> **Empedokles said:**
> Hello,

I'm using an Acer Notebook TravelMate 4002 WLMi with Kubuntu 7.04. With the original kernel version 2.6.20-15 that comes with feisty the KDE application "Power Manager" shows me the battery status and the cpu clock frequency. Everything works fine.

Since I've updated the kernel to 2.6.20-16, only the display for the clock frequency works correctly. Unfortunately the new kernel isn't able to find any batteries, and the detection of the power supply for plugging in and out also doesn't work since the update.

I've posted this problem in my native language in the german ubuntuusers.de forum. There is another person with the same notebook with the same problem and without any idea too.

Can anyone help us?

During the boot up sequence just select the -15 kernel in the grub menu.  The -16 kernel worked fine on my machines.

---

