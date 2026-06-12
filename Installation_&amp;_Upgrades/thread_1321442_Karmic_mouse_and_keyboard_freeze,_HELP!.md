---
title: "Karmic mouse and keyboard freeze, HELP!"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by gardiol on 2009-11-10
Hi guys!
i just did an upgrade from 9.04 to 9.10 on my father desktop and after some time (ranging from 2 to 10 minutes) mouse and keywboard will stop working! I can still login over SSH and i get aboslutely nothing in the LOGS (not even in X log) so i am posting to you.

This is VERY serious because he needs the computer and so i need to fix this ASAP, and possibly a fresh reinstall of Jaunty is not an option.

I am ready to post here any informations you might need to help on this topic.

The video is an NVIDIA GeForce4-MX and i both tryed nvidia binary and NV X driver with the same exact results.

---

### Post by QueenZ on 2009-11-10
Have the exact same problem, i'm also looking for help. And this happens to all new distros.. I think it's the new kernel's fault...

---

### Post by gardiol on 2009-11-10
I have temporary fixed this issue by reverting to kernel 2.6.28-r13, the last one updated by my old jaunty.

So now seems to be working, and currectly this is a KERNEL issue.

---

### Post by QueenZ on 2009-11-10
I figured that it's a kernel issue because none of the new distros seem to work anymore. Could someone tell me how i can downgrade the kernel?

---

### Post by gardiol on 2009-11-10
Sorry but downgrading is NOT a solution. Not to 2.6.28 at least.

The printer stopped working AND my father got a mouse/keyboard lockup again, just some time later.

I guess is a udev/kernel problem since the latest udev does noyt work with older kernels. So, again, please somebody tell us how to revert to another kernel...

thanks!

---

### Post by Antmannz on 2009-11-10
Same deal here; no keyboard or mouse from the splash screen onwards. Both PS2 and USB. USB plugging and re-plugging has no effect.

Have spent the best part of a day on this - considering moving back to Windows, at least it works. I mean, keyboard and mouse - how basic can you get.

---

### Post by gardiol on 2009-11-11
I have finally solved the problem with my father pc: i bought a USB keyboard and a USB mouse. Plugged, working.

But this is not a solution...

People, Windows requires you to upgrade ram, CPU and video card, Linux requires you to upgrade.. keyboard and mouse... Is this a joke? hey, its not April 1st...

---

### Post by Antmannz on 2009-11-11
I've also resolved this, not with new hardware though.

I was able to connect remotely via SSH and used: ```
sudo apt-get --reinstall install udev
reboot
```

Once the reboot completed the keyboard and mouse were live once more, but I did notice an initramfs error during the boot.

---

### Post by gardiol on 2009-11-12
Your problem is a bit different. My mouse&keyboard was always alive after a reboot, would only stop working after a while, and a reboot would fix it every time.

Anyway reinstalling udev did not help me with the old PS2.

---

### Post by bPawn on 2009-11-21
I had the same problem and many others in bug reports at launchpad. What I did is a bit _**tricky/dangerous**_ but worked.

get the latest stable kernel form kernel.org and follow this guide:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) , **mind not to include the modules_image**. Then remove everything proprietary, like ati/nvidia (even if you have no nvidia check if there is anything installed), install the generated debs and then your proprietary drivers. Reboot and profit. uname -a should say your new kernel.

---

