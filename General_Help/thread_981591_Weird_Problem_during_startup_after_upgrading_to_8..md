---
title: "Weird Problem during startup after upgrading to 8.10"
date: 2008-11-13
forum: General Help
---

### Post by mattlb0619 on 2008-11-13
after upgrading from 8.04 to 8.10 bia the web; When i boot after the ubuntu loading screen is up the bar goes about 1/4 the way across and stops. It looks frozen but if i hold donw a key it will move again, it i let it go it stops. holding the key down itll go across then back across and finish loading as usuall. if i dont hold a key down itll just sit there...

any ideas?

thanks matt

---

### Post by popuptarget on 2008-11-13
Matt, So just pressing any key that you feel like cause the system to load normally?

---

### Post by mattlb0619 on 2008-11-13
i havent tried ctrl or alt or windows key but the ones ive tried yea. but u have to hold it down not just push it. hold it down the the bar goes like normaly let it go and itll stop again. like i said its weird... :/

---

### Post by mattlb0619 on 2008-11-13
anyone else?

---

### Post by Lesouteneur on 2008-11-20
Josueped solved my problem for me you just have to add the boot option "acpi=noirq" (without quotes):

> **Josueped said:**
> here is the fix. from terminal

gksudo gedit /boot/grub/menu.lst

Find the line

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=...ro quiet splash

add

acpi=noirq to the end so

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=.... ro quiet splash acpi=noirq 

and you are good to go.

---

### Post by my username is on 2008-11-20
Thank you for the reply.

 I have the same problem and after that  bar moves to 1/3rd of its way instead of 1/4.
Holding down a key docent help with this USB keyboard

---

### Post by SoCalChris on 2008-11-20
I'm guessing that you have an HP laptop, with a 64bit AMD processor? This is a known bug with the latest kernel. So far, I haven't heard any developer response to it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)
[http://bugzilla.kernel.org/show_bug.cgi?id=11973](http://bugzilla.kernel.org/show_bug.cgi?id=11973)

> **Lesouteneur said:**
> Josueped solved my problem for me you just have to add the boot option "acpi=noirq" (without quotes):

This does work, but will sometimes cause weird behavior, such as volume buttons not working correctly. Check the launchpad thread that I noted above for some other workarounds that don't have side effects.

---

