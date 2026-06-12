---
title: "Another Install Problem---initramfs"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by hd79 on 2009-01-20
I had some problems updating my computer----after the update I kept getting a BusyBox sehll prompt and kept getting the initramfs prompt.

So...... I installed a New Hard Drive, and installed Ubuntu 8.10 from the Alternate CD. Now I am getting basically the same error, with this New hard drive. The Ubuntu Splash screen appears, but instead of the progress bar going forward, it bounces back and forth for a little while, and then I eventually get this message:
Boot from (hd0,0) ext3  2e0a20cd-a1f7-b63c-c82eca16d601

Starting Up...

Loading, please wait....

Gave Up waiting for root device. Common Problems:
-Boot args (cat /proc/cmdline)
-check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
missing modules (cat/proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid /2e0a20ce-a1f7-4cef-b63c-c82eca16d601 does not exist. Dr
opping to a Shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs)_

And then I am just basically sitting at the initramfs prompt. More by dumb luck than anything else, I tried typing "Return", and pressing enter, and then the system goes ahead an boots up.

So does anyone know how I can get this error message resolved an fixed ?
or alternately,
get the system to boot up normally, without having to type "Return" at the initramfs prompt every time?

I found one suggestion to install something called yaird and remove initramfs, but I don't know if I want to do anything quite that drastic----drastic for me, at least at any rate!

---

