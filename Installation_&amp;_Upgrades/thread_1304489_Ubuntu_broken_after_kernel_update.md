---
title: "Ubuntu broken after kernel update?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by willem.deboer on 2009-10-29
Hi, after upgrading my dualboot machine (XP and Ubuntu) from Xp to Windows Seven, it lost the ability to dual boot. Nevermind, with EasyBCD I reconfigured the Windows 7 bootmanager to dual boot Windows 7 and Ubuntu. It's now using Windows Seven bootmanager instead of Grub. Sofar so good.
After a couple of days, Ubuntu 9.04 warned it needed to update the kernel. Then the update manager asked me whether i wanted to let the manager update my menu.lst (it never did that before). I said no, keep the old one (on hindsight, I wonder what got into me :-).

Now, Ubuntu will not boot anymore. After the initial Ubuntu startscreen I see a lot of text scrolling, and then: "Target Filesystem does not have /sbin/init", and a prompt for "Initramfs". When I exit that, it says something like "operating system panic".
The latest kernel in the menu.lst is 2.6.28-15 generic.

Any help immensely appreciated!

---

### Post by lemming465 on 2009-11-01
> after upgrading my dualboot machine (XP and Ubuntu) from Xp to Windows Seven, it lost the ability to dual boot.
I'm guessing the sequence of events was roughly (1) buy a PC with an OEM windows install (2) add Ubuntu  (3) windows 7 upgrade or install.  Windows thinks it is the center of the universe and *always* overwrites the MBR (master boot record, first part of the first sector of the first hard drive) when you install/upgrade/repair it.

Oversimplified, the boot process goes kind of like:

BIOS --> MBR --> secondary boot loader on first 63 sectors of disk partition --> OS boot loader --> OS kernel --> OS processes

Both the windows and Linux OS boot loaders have the ability to restart the secondary boot loader for some other OS from some other partition, which is how you get dual-boot to work.  You only get one MBR, but you can have multiple secondary boot loaders on different partitions, and the OS boot loader started by the MBR -> secondary chain can offer you a menu and let you choose where you really want to go this time.

When you installed Ubuntu 9.04, you probably took the default boot options, which are to overwrite the MBR with GRUB code (FSF bootloader) pointing to a GRUB secondary, and to add an option to the Grub boot selection menu to chain back to the windows loader.

> the update manager asked me whether i wanted to let the manager update my menu.lst
And you are correct that the usual answer to this should be "yes, please".

There is a fairly good page on [recovering from windows installs]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), which should improve your situation.  (Note: fresh installs of Ubuntu 9.10 "karmic koala" use grub2 beta, not classic grub, and repair is different.)

If that doesn't fix things enough, you need to boot a live CD, hand-mount your root partition, and use "chroot" and "update-grub" to fix things up.  If you post the results of "sudo fdisk -lu" from a terminal window on a live CD and describe your disk partion strategy we can offer more specific advice.  Assuming your disk is partitioned like:
1: primary windows NTFS
2: extended
5: logical Linux root
6: logical Linux swap
and you want Ubunto to control the MBR then this could look like
```

1. boot live CD
2. open terminal window (Applications --> accessories --> terminal)
3. sudo -i
4. mount /dev/sda5 /mnt
5. for x in sys dev proc; do mount -o bind /$x $x; done
6. chroot /mnt
7. update-grub
8. exit

```
Then reboot.

---

### Post by willem.deboer on 2009-11-01
Actually, the machine was running and dualbooting just fine using the Windows Seven bootmanager. EasyBCD is quite a handy utility to edit the boot options. I deliberately let Windows Seven overwrite the MBR because I wanted the Windows bootmanager to be leading.
It was only after the Ubuntu updates were installed that the trouble began with this otherwise smoothly running configuration.

In fact, the problem is solved now, here's what I did:
With gparted from the live CD I chose to check and fix the filesystem of the Ubuntu partition, then booted Ubuntu in recovery mode, then chose "resume boot normally", and to my amazement it started up normally. I wish I knew why. I suppose somehow the check and fix filesystem did the trick, but I don't understand how.

Only thing is the update manager now warns "There was a problem checking for updates".

Any suggestions?

---

### Post by lemming465 on 2009-11-01
> the update manager now warns "There was a problem checking for updates".
I assume networking is working; if not update-manager will never work.  Try a command line run and see what kind of error messages you get, if any.```

sudo aptitude clean  # remove any stale or broken downloads
sudo aptitude update # refresh package lists
sudo aptitude full-upgrade # try to download and install updated packages

```

---

### Post by willem.deboer on 2009-11-01
Thank you for responding so quickly! Unfortunately, no error messages at all ...

---

### Post by willem.deboer on 2009-11-02
However, when I right-click on the update manager item (which now looks like a sign used for wrong side of one-way street), and tell it to install all updates, it says:

E: Could not lock /var/cache/apt/archives/lock - open (11 resource is temporarily unavailable)
E: Could not lock downloadfolder

Does that help?

---

### Post by willem.deboer on 2009-11-29
It seems I'm the only one experiencing this problem ...... I'm giving up and scrapping Ubuntu for Windows Seven, which is running like a song!

---

