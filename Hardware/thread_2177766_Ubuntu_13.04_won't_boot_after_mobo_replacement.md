---
title: "Ubuntu 13.04 won't boot after mobo replacement"
date: 2013-09-30
forum: Hardware
---

### Post by HuaiDan on 2013-09-30
It's autumn, and I've got upgrade fever again. I recently upgraded to Raring, and was pleasantly surprised, but I noticed the hardware was under a bit of a strain using the nearly 6 year old GA965 core duo mobo and generic nvidia card. 
First I upgraded the card to a GTX 660 variety, no major problems presented themselves. 
Couple weeks later,  got a GA-Z87P mobo with an i7 processor, and just put it in today.
I had some problems with Grub at first, but tweaking the boot order in BIOS fixed that. Now grub starts.
I can'tget much than that, it goes to a black screen.
When I select recovery from Grub, it hangs at 7 seconds, with the message "Nvidia taints kernel"
If I use the live CD, 13.4, then it goes past the Plymouth screen and prompts me to load low graphics mode, and freezes.
Can someone help me troubleshoot this? I can't wait to see what Raring is like on high end hardware.

---

### Post by grahammechanical on 2013-09-30
Let us review what you have done. You have replaced a motherboard that was at least six years old with an much newer motherboard and you are using the same hard disk with an OS that has kernel modules for the hardware of the six year old motherboard. Yes? The hardware on the motherboard does not match the Linux kernel hardware modules in the OS. You need to re-install Ubuntu to get an OS that has software components that match the motherboard's hardware components.

Regards.

---

### Post by Yellow Pasque on 2013-09-30
> **grahammechanical said:**
> You need to re-install Ubuntu to get an OS that has software components that match the motherboard's hardware components.

The problem is that the LiveUSB/CD does not work correctly, so it is easy to suggest reinstall, but that is probably not the full answer.

My suggestion: Since you have a very recent mobo chipset (z87), try a 'buntu 13.10 LiveUSB/CD

---

### Post by HuaiDan on 2013-09-30
That's right. I can't even boot to the Live CD, so how am I going to re-install?
I'll try the Saucy daily build,, but first I think I'll try something I saw something about booting the Live CD on UEFI hardware. I managed to do it before, and I got a regular Grub menu from the Live CD. Apparently, you can specify boot options from there.
Now, if I can find what those boot options are, or if they'll have any effect.

---

### Post by HuaiDan on 2013-10-01
If indeed the problem arises from the kernel modules not matching the hardware, then why does an openSUSE 12.2 installation, which uses an older kernel (3.4) and which I also installed some time ago, start right up?
I managed to get the Ubuntu 13.4 Live CD to boot up, and tried re-installing, now I get a purple screen and freeze. I even tried reinstalling nvidia-current from root shell.

---

### Post by HuaiDan on 2013-10-01
Installed Saucy, now it takes me directly to a grub rescue prompt, no such device,  some long number.
How did that happen?

---

### Post by HuaiDan on 2013-10-01
delete this

---

### Post by HuaiDan on 2013-10-01
Set prefix  blah blah
set root blah blah
get to  "insmod  normal", get "file not found".
That's not supposed to happen.
from "ls" all the kernels get listed, so I'm in the right place, but it never seems like grub commands work the way they're supposed to.
Heeeelllp MMeeeeeeeee...I'm in the grub dungeon!!!

---

### Post by HuaiDan on 2013-10-01
The yannubuntu boot-repair got me booted. From the messages I got from there, it was an EFI issue (something I know next to nothing about), and grub had to be removed from all partitions an reinstalled.

---

### Post by HuaiDan on 2013-10-01
Actually, it's not solved.
After a fresh install of 13.10, then a boot repair, I finally got it  to boot.
Then, after an install of nvidia-current, I'm back to the original problem.
6 seconds into boot, it freezes at "nvidia: module license 'NVIDIA" taints kernel.
Then,
"Disabling lock debugging due to kernel taint"

---

### Post by HuaiDan on 2013-10-01
Searching around, I see some ideas, but how can I try them? I need t get to a shell prompt, but I don't see a way to do this. Recovery crashes before I can get to the menu that allows me to drop to a shell prompt.

---

### Post by Elfy on 2013-10-01
Closed.

Op started new thread to deal with this - [http://ubuntuforums.org/showthread.php?t=2177934](http://ubuntuforums.org/showthread.php?t=2177934)

---

