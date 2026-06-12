---
title: "Ununtu Too Dumbed Down?"
date: 2011-04-12
forum: Hardware
---

### Post by mooreted on 2011-04-12
Well, Installed Ubuntu 10.04 on a Shuttle system. The SIS onboard video was too slow so I installed a Geforce MX4000. After rebooting the video resets, I see some errors scroll by then the monitor goes black and then goes to sleep.

On a single drive Ubuntu doesn't install Grub so there are no boot option to get to a command line or other geeky stuff so I can fix the problem. I can't stop the boot process anywhere and get to a different runlevel. There's no xorg.conf so I can't choose the Vesa driver which would let me boot and fix the problem.

In making Ubuntu "easy" to use they seem to have dumbed it down so much a regular technical person cant work on it at all. 

Grrrr!!!

---

### Post by mick222 on 2011-04-12
Grub is installed just press shift at startup. You can create an xorg.conf file if you need it.

---

### Post by coffeecat on 2011-04-12
> **mooreted said:**
> On a single drive Ubuntu doesn't install Grub

Of course it does. How else would it be able to boot at all? If you mean an installation of Ubuntu alone with no other OS, then you simply press SHIFT at the post screen, keep it pressed and the grub menu appears. Then you can select recovery mode for a root shell and put in geeky stuff to your heart's content.

> **mooreted said:**
>  There's no xorg.conf so I can't choose the Vesa driver which would let me boot and fix the problem.

There's been no xorg.conf in any major distro for at least two years. That's an xserver thing. It can autoconfigure itself in most cases.

For vesa, simply edit the main Ubuntu entry at the grub menu and add "xforcevesa" to the kernel options. You can make this permanent either by creating your own xorg.conf or, better, by reconfiguring grub to include this option.

---

### Post by K_45 on 2011-04-12
Look here midway down for more info on Xorg:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by mooreted on 2011-04-12
Ok, thanks. I found instructions here:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I used to just boot into single-user mode, do "nano /etc/X11/xorg.conf" and change "Driver='vesa'" and reboot. 

Seems like all this automatic stuff is great until something doesn't work. I guess I'm getting old. I like configuration files I can edit and control what my computer does.

Just frustrated I guess. Every time I learn how to play the game they change all the rules.

---

