---
title: "Tried updating from 7.10 to 8.04 boot to BusyBox initramfs"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by hd79 on 2008-12-13
Hi All.
I am hoping somebody can help me out here. I tried updating from ubuntu 7.10 to 8.04. I used the package manager to install all updates for 7.10 and restarted a couple of times. I checked package manager, and no updates were in the package manger window other than the choice to upgrade to 8.04 LTS. I have a DSL connection, and it took about 3 hours to download the update, and about another hour to install everything. I did not watch the entire time, but I checked on it from time to time, and I got a screen that asked to Restart. I clicked on Restart, and now when Ubuntu starts, instead of getting the orange progress bar on the ubuntu startup screen, the orange bar "bounces' back and forth, and then I finally get to this screen:

Starting Up....
Loading, please wait...
    check root=bootarg cat /proc/cmdline
    or missing modules, devices! cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/586255b2-73b6-4830-89aa-630e0727fe07 does not exist, Dropping to a Shell!

BusyBox v 1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Shell (ash)

Enter 'help' for a list of built in commands.

(initramfs)_

And the cursor just blinks at this initramfs prompt.

From the message , I gather there is some sort of problem recognizing the hard drive, but when I go the Grub Menu and enter the Rescue choice, I just get a Help screen and not a real Rescue mode or prompt.

So, am I hosed here, or is there some way to get my system to work again?

---

### Post by Partyboi2 on 2008-12-14
Have a go at [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6211457&postcount=2"), if you have not already.

---

### Post by hd79 on 2008-12-14
Thanks for the message. I added the rootdelay line in, but it still came up to the initramfs prompt.

When I go into the GRUB menu, I have about three different choices, but it looks like they all say the same thing. I didn't write it down, but the choices all say something about 8.04 kernel, and then below that line is something about 8.04 kernel rescue. anyway, I tried the middle choice that says "rescue", and I did get to a rescue screen.

I picked the choice that says fix broken packages, and then picked the top choice that says "resume normal boot"

I can now get back into my system, but when I restart, I still come up to the BusyBox shell with the initramfs prompt.

As long as I can get into my system at least, maybe there is some hope to recover some of my files, but I would like to fix this boot issue

is there any way to fix or repair the boot issue?

---

### Post by hd79 on 2008-12-14
Ok, I have a little more information now. When I enter the Grub menu, there are three choices.

the first one is this:
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=586255b2-73b6-483c-89aa-630e0727fe07 ro quiet splash

the second one is this:
kernel          /boot/vmlinuz-2.6.22-16-generic root=UUID=586255b2-73b6-483c-89aa-630e0727fe07 ro quiet splash

When I choose the 2.6.22-16 kernel choice, the system starts up ok.

When I choose the first on, the 2.6.24-22 kernel, I get the BusyBox  initramfs prompt, and this is also what happens if I just let the system start up, without entering into GRUB.

So, How do I fix this?

---

