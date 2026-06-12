---
title: "fixed /dev/mapper/ for LVM on install, update killed it"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by Steven Edwards on 2009-03-24
Hi,

So, I have been working on this for a while.  I have a standard Dell Dimension 8400 and it has been nothing but trouble.

I got a new Seagate Barracuda 1.5 TB drive and want to install Ubuntu 8.10 on it, making a clean break from Windows.

First problem: SAMSUNG SD-616E DVD player won't boot the Live CD.
Solution: Burn the Live DVD and enjoy.

Second problem: After installation (with LVM following [this guide](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/)), drive fails to boot citing /dev/mapper/main-root not found.
Solution: Select ubuntu option from grub menu, e to edit, append irqpoll to the second line

Third/current problem(s):

[list=1][*]On initial boot, approve all software updates.
[*]On reboot, ubuntu-2.6.27-generic option fails, citing same error as second problem.
[*]Soft reboot from Busybox causes SATA-0 (Barracuda) to not be recognized; hard reboot fixes that.
[*]Appending irqpoll to 2.6.27-generic fails, repeating same /dev/mapper errors -- adding ata1: COMRESET failed! (errno=-16)
[*]On next boots, grub boots into 2.6.27 before I can attempt to boot from the original.
[*]Attempts to boot from Live CD now return ata1: COMRESET failed! (errno=-16) errors, putting me in busybox.[/list]

I'm thinking of just booting from the QParted Live CD, wiping the drive, trying again and ignoring the software updates, but I was hoping someone here had a suggestion or three I could try.

Anyone? :)

Thanks,

Steven

---

### Post by Steven Edwards on 2009-03-24
I don't know how it happened, but Grub finally gave me time to choose which kernel I wanted to boot with.  I added irqpoll to the one that comes with 8.10 and it booted flawlessly.

---

