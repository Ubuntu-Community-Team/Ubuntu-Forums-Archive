---
title: "Remove Vista and Install XP in UBUNTU dual boot"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by avspavan on 2009-01-19
Hi all:

I have UBUNTU and VISTA as dual boot. Now I want to remove Vista and install XP. How do I do that? I have a XP boot CD. When I tried to install XP from bootable CD, I am worried that it might erase UBUNTU. How do I install just over VISTA? And my Vista has crashed already. So I can't access it.

Please help!
Thanks
Pavan

---

### Post by EXCiD3 on 2009-01-19
The only way you will be able to install XP on the Vista partition is by installing it and then using the ubuntu livecd to reinstall grub. Windows always overwrites the bootloader and you will just need to restore it. Install XP like normal on the Vista partition and then boot into the livecd, open a terminal and run these commands:
```
sudo grub
find /boot/grub/stage1
(***Use the output from this command in the next command)***
root (hd0,1)            (hd0,1) is an example
setup (hd0)
quit
```

This reinstalls grub so now you can reboot and you will have Grub come up. I am not for sure if the XP entry is different than the Grub entry for Vista so you may need to modify your /boot/grub/menu.lst if the Windows entry does not boot properly.

---

### Post by Montblanc_Kupo on 2009-01-19
What I would do... and other's might do things differently *shrug*.

I would boot from the ubuntu live cd and use the partition editor to nuke the vista partition and leave it as unpartitioned space. I just trust gparted way more than windows partitioning (it's easier too). Then when you make the install of XP just make SURE you only use the unpartitioned space and don't let it use the whole disk.

You're going to have issues with the grub boot loader disappearing temporarily because windows will write it's boot to the MBR.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

That guide will give you a good reference to getting it back up. It talks about vista... but gives the basic idea.

One item that took Me forever to track down was how to make the grub setup work correctly... here's how I finally got it:

Make sure you have a backup of your /boot/grub/menu.lst (since this has your boot loader in it... and since you already have windows... you shouldn't have to change anything in it).

Boot from LiveCD
Open terminal
sudo grub
find /grub/stage1
root (hd0,X) [COLOR="Silver"]<-- the stage1 command will give you a number to put in for X[/COLOR]
setup (hd0)
quit

Now just restart normally and you should see the linux bootloader again with all your choices.

---

### Post by Montblanc_Kupo on 2009-01-19
> **EXCiD3 said:**
> 
find /boot/grub/stage1

I've found that usually the LivdCD won't find the stage1 with that path and you end up having to use the path I listed... although it could be dependent on how you installed. Basically if it returns an error that it can't find it, try the other path... no harm no foul.

---

### Post by EXCiD3 on 2009-01-19
> **Montblanc_Kupo said:**
> I've found that usually the LivdCD won't find the stage1 with that path and you end up having to use the path I listed... although it could be dependent on how you installed. Basically if it returns an error that it can't find it, try the other path... no harm no foul.

Interesting, ive never had that trouble. Will take note of that though :)

---

