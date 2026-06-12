---
title: "Lubuntu 14.04 on Toshiba Satellite L770D: keyboard/touchpad stuck sporadically"
date: 2014-09-01
forum: Hardware
---

### Post by no_keyboard on 2014-09-01
Hi, seeing the exact same issue as reported at: [http://ubuntuforums.org/showthread.php?t=1887165](http://ubuntuforums.org/showthread.php?t=1887165)

> **Toshiba Satellite L770D touchpad/keyboard intermittant**

New laptop, dual booting with Windows 7 & Ubuntu 11.10 64bit.  I   have a problem where its a crap shoot if my keyboard/touchpad work after   a reboot - often taking repeated power cycles before they get   recognized at the login prompt.

Its not a hardware problem, as there is no issue using the keyboard at   POST and GRUB menus.  It seems to drop as soon as the login screen is   initialized as I can toggle the splash screen up to that point with the   keyboard.

Hoping there's a simple fix, as spending 10 to 20 minutes to boot up is   getting absolutely ridiculous... I'm starting to consider actually  using  Windows at this point.



Identical noteboook (Toshiba Satellite L770D), identical problem - but under lubuntu 14.04 instead, desktop doesn't seem to matter much, it's the login screen (lightdm) where the whole thing is getting stuck.
But the OS itself remains responsive, i.e. by attaching an external USB mouse, it does respond properly - it's "just" the internal keyboard/touchpad that seem completely disabled/stuck.
I supposed it's some kind of ACPI related issue, but when I tried to the ACPI tables to post them here, I was getting segfaults from the acpidump/xtract utilities.
Problem occurs sporadically and notebook performs otherwise perfectly well, including under Windows (dual-booting) - where the problem doesn't show up at all
Would love to get down to this - even if that means rebuilding a custom kernel.


Anybody else seeing this, any advice/hints ? 

Thanks & all the best

EDIT: It seems this is a recurring problem, and it has been occurring for at least 3 years, affecting mainly Ubuntu-based installations on Toshiba Satellite notebooks:
[http://forums.techarena.in/operating-systems/1445294.htm](http://forums.techarena.in/operating-systems/1445294.htm)
[http://ubuntu.aspcode.net/view/635400140124705175289196/keyboard-not-responding-at-login-with-1204-dual-boot-on-toshiba-satellite-l775](http://ubuntu.aspcode.net/view/635400140124705175289196/keyboard-not-responding-at-login-with-1204-dual-boot-on-toshiba-satellite-l775)
[http://askubuntu.com/questions/336839/touchpad-not-working-with-toshiba-satellite-ubuntu-13-04](http://askubuntu.com/questions/336839/touchpad-not-working-with-toshiba-satellite-ubuntu-13-04)
[http://askubuntu.com/questions/477517/touchpad-detected-but-not-working-in-ubuntu-14-04-on-toshiba-satellite-p75-a7200](http://askubuntu.com/questions/477517/touchpad-detected-but-not-working-in-ubuntu-14-04-on-toshiba-satellite-p75-a7200)
[http://forums.linuxmint.com/viewtopic.php?t=152185](http://forums.linuxmint.com/viewtopic.php?t=152185)
[https://answers.yahoo.com/question/index?qid=20140606065817AAEub8Q](https://answers.yahoo.com/question/index?qid=20140606065817AAEub8Q)
[http://crunchbang.org/forums/viewtopic.php?id=14601](http://crunchbang.org/forums/viewtopic.php?id=14601)
[http://forum.ubuntuusers.de/topic/toshiba-satellite-touchpad-funktioniert-einfa/](http://forum.ubuntuusers.de/topic/toshiba-satellite-touchpad-funktioniert-einfa/)[URL="http://forum.ubuntuusers.de/topic/tastatur-und-touchpad-funktionieren-nur-period/"]
http://forum.ubuntuusers.de/topic/tastatur-und-touchpad-funktionieren-nur-period/[/URL]

---

### Post by no_keyboard on 2014-09-02
ok, it seems this is a very common issue related to kernels >= 2.6 and the i8042 chipset that uses PS/2 for interfacing the keyboard and touchpad. So it's not specific to Toshiba Satellite notebooks.
The solution that worked here was adding this to grub.cfg:
```

i8042.nomux=1 i8042.reset

```

I hope that this will be recognized as a real troublemaker and recognized during installation, and dealt with accordingly:

[https://bugs.launchpad.net/linuxmint/+bug/1258632](https://bugs.launchpad.net/linuxmint/+bug/1258632)
[http://askubuntu.com/questions/181882/cant-use-keyboard-at-all-on-12-04](http://askubuntu.com/questions/181882/cant-use-keyboard-at-all-on-12-04)

[http://forums.linuxmint.com/viewtopic.php?t=152185](http://forums.linuxmint.com/viewtopic.php?t=152185)
[http://forums.linuxmint.com/viewtopic.php?t=155149&p=805309](http://forums.linuxmint.com/viewtopic.php?t=155149&p=805309)
[http://askubuntu.com/questions/465136/laptop-keyboard-and-touchpad-disabled-on-startup](http://askubuntu.com/questions/465136/laptop-keyboard-and-touchpad-disabled-on-startup)
[http://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu](http://unix.stackexchange.com/questions/28736/what-does-the-i8042-nomux-1-kernel-option-do-during-booting-of-ubuntu)
[http://forum.linux-club.de/viewtopic.php?f=92&t=117505#p742848](http://forum.linux-club.de/viewtopic.php?f=92&t=117505#p742848)

---

### Post by jaffarfiree on 2015-02-19
Hello,
I am having the same issue. I am just wondering where I would this code that you provided? Do I do this through the loader menu or through the file explorer?

Thanks!

---

