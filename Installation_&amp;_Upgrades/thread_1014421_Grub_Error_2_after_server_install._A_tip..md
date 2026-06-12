---
title: "Grub Error 2 after server install. A tip."
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by thisllub on 2008-12-17
Yesterday I did a 8.10 server install over an existing install on a Dell machine.
Despite having 3 drives the BIOS only allows one to be selected as the boot drive. Unfortunately the one I chose during the install was not correct.

After selecting hd0 as the location for grub the Stage 1.5 Error 2 appeared.

Booting into rescue mode is a problem as the option to install the grub loader asks you to re-partition the disks.

However if you choose rescue mode from the menu the option to install the grub loader will not appear unless a valid boot partition is mounted on /boot

If you have a separate boot partition as I do you will need to mount it manually by opening a shell. Upon exiting the shell the grub option appears and you can try installing grub again to another location.

I hope this helps someone.

---

### Post by ultralame on 2008-12-18
Thanks for your post, I am dealing with this right now, and I have never really looked at GRUB before.

Question:  How do I get into the rescue mode?  My screen looks like this:

[INDENT]Boot from CD/DVD :
GRUB Loading stage1.5.


GRUB Loading, please wait...
Error 2[/INDENT]

Do I have an option to get a rescue mode?  Is there a key to get to it?

---

### Post by thisllub on 2008-12-18
You will need to boot from the install cd.
One of the options is;
Rescue a broken system.

Select that.

Choose execute shell from the main menu and mount your boot partition on /boot
After you exit (by typing "exit") the shell the grub option should appear on the shell sub menu. You may need to repeat this until you find out which drive you are actually booting from with a Dell machine. Most civilised BIOSes are simpler.

---

