---
title: "[SOLVED] 8.10 - System does not start after installation"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by turipriv on 2008-12-30
Hi everybody, I just installed Ibex on my Acer Aspire 3050 laptop.
Everything went fine with the installation process, but after rebooting, GRUB came up with the following message:

[B][I]Boot from (hd0,0) ext3 c9f54224-bf6d-4dbe-87ac-59252b8eef49
Starting up...
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; le /dev)
ALERT! /dev/disk-by-uuid=c9f54224-bf6d-4dbe-87ac-59252b8eef49 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/I][/B]

I tried to modify the **menu.lst** file using the root device drive instead of its UUID but without any result.
I also tried reinstalling GRUB and still nothing changes.
Please note that none of this happened when I was using Feisty Fawn on the same computer ant that this is also the first time that I get such an error message with an Ibex installation.

I hope anybody can help me on this.

---

### Post by abn91c on 2008-12-30
> **turipriv said:**
> Hi everybody, I just installed Ibex on my Acer Aspire 3050 laptop.
Everything went fine with the installation process, but after rebooting, GRUB came up with the following message:

[B][I]Boot from (hd0,0) ext3 c9f54224-bf6d-4dbe-87ac-59252b8eef49
Starting up...
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; le /dev)
ALERT! /dev/disk-by-uuid=c9f54224-bf6d-4dbe-87ac-59252b8eef49 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/I][/B]

I tried to modify the **menu.lst** file using the root device drive instead of its UUID but without any result.
I also tried reinstalling GRUB and still nothing changes.
Please note that none of this happened when I was using Feisty Fawn on the same computer ant that this is also the first time that I get such an error message with an Ibex installation.

I hope anybody can help me on this.
at the prompt type [COLOR="Red"]**exit**[/COLOR] then hit enter

---

### Post by -=-+ w1r1zu +-=- on 2008-12-30
I experienced that too. What I did is re-installed Ubuntu. First I typed reboot and then Uninstall Ubuntu using Wubi. And then Install again.

Of course, I deleted the ubuntu backup folder.

---

### Post by turipriv on 2008-12-31
@ _**abn91c**_, thank you very much, your solution worked perfectly!!!

@ **_-=-+ w1r1zu +-=-_**, thank you to you too, unfortunately I cannot try your method, since Ubuntu is the only systemm installed on my computer I cannot use wuby.

Anyway, problem solved.
Thanks everybody for the support.

---

