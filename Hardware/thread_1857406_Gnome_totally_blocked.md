---
title: "Gnome totally blocked"
date: 2011-10-10
forum: Hardware
---

### Post by Mircuzzo on 2011-10-10
Hi all, I am on Ubuntu 11.04 64bit on a notebook Dell XPS 16. 
I have an ATI Mobility Radeon HD 565v with proprietary drivers installed (fglrx). 
The problem I'm facing with is that sometimes when boot is going to complete or is completed, the graphical interface (gnome in my case) remains totally blocked and nothing works.
I tried to wait a little but the pc seems completely gone. The only way to continue is to reboot manually with the power button.
Even with CTRL+ALT+F1 I can't get into the terminal.
Some months ago I had the same problem on the same pc, but with Ubuntu 10.10 64bit.

What can I try to do?

I have propritary drivers for the graphic card because the open source ones were giving me some problems with the cpu high usage and overheating.

Thanks a lot...

---

### Post by collisionystm on 2011-10-10
> **Mircuzzo said:**
> Hi all, I am on Ubuntu 11.04 64bit on a notebook Dell XPS 16. 
I have an ATI Mobility Radeon HD 565v with proprietary drivers installed (fglrx). 
The problem I'm facing with is that sometimes when boot is going to complete or is completed, the graphical interface (gnome in my case) remains totally blocked and nothing works.
I tried to wait a little but the pc seems completely gone. The only way to continue is to reboot manually with the power button.
Even with CTRL+ALT+F1 I can't get into the terminal.
Some months ago I had the same problem on the same pc, but with Ubuntu 10.10 64bit.

What can I try to do?

I have propritary drivers for the graphic card because the open source ones were giving me some problems with the cpu high usage and overheating.

Thanks a lot...

Yup that happened to me. After every kernel update, you have to run the proprietary driver install again. It modifies the kernel. The open source ATI driver is broken.

Reboot your computer,

After the bios screen, hold the shift key

This should take you to the grub menu.

Press E to edit.

Where it says, quite splash

make it say

quite splash nomodeset

press F10 to boot.

Login, run your proprietary driver install again.

---

