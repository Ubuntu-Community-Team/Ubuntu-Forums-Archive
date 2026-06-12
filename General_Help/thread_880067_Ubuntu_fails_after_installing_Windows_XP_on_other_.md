---
title: "Ubuntu fails after installing Windows XP on other hard disk"
date: 2008-08-04
forum: General Help
---

### Post by anderssl on 2008-08-04
Hey! I'm in a bit of crisis - can anyone help?

I have two hard disks on my computer. A few months ago I formatted one of them and installed Ubuntu 6.06 on that one - on the other one I kept Win XP. Upgraded to Hardy as it came out. Then I formatted the other hard disk and reinstalled Win XP (to clear a virus problem). During installation Windows demanded that i deactivated the disk which held ubuntu, saying that I could easily reactivate it afterwards. However, since then I have been unable to boot in ubuntu. If I set booting to that disk in the bios setup, the comp freezes immediately on boot and asks for system disk.

Stupidly, I hadn't backed up my data on the ubuntu drive, thinking they were safe from Windows trouble there... And now I can't access them. Please tell me, are my data dead and gone forever?

I tried booting from an ubuntu cd, but that didn't give me access to the hard drive. Also, during the fatal WinXP installation I was forced to use a small (2GB) unpartitioned space on my computer to create a partition that Windows would use for something - turns out that space was on the disk that holds ubuntu - is that why I'm in trouble?

Sorry for the level of technical detail here, I'm pretty green... Help anyone?!?!

Anders

---

### Post by ibuclaw on 2008-08-04
2GB of unpartitioned space sounds like enough for a swap, perhaps.

As for ubuntu, boot up into the LiveCD and post the output of the following command in the console:
```
sudo fdisk -l
```

Also, I'm not sure if it will work in a liveCD, but you could try out an app called "restoregrub"
[http://ppa.launchpad.net/kiwilinux-members/ubuntu/pool/main/r/restoregrub/](http://ppa.launchpad.net/kiwilinux-members/ubuntu/pool/main/r/restoregrub/)

It has proven exceptionally useful to me when dual/trio booting Linux installs, but wanting to only use the first Linux GRUB config.

Regards
Iain

---

### Post by anderssl on 2008-08-05
Hey,

thanks for the fast reply!

Here is the result of sudo fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       30400   141789690    f  W95 Ext'd (LBA)
/dev/sda5           12749       30400   141789658+   7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7165    57552831   83  Linux
/dev/hdb2   *        7166        7475     2490075    7  HPFS/NTFS

```

About the second tip you gave me, I have to figure out how to install it first... As I said, I am very green. 

Anders

---

### Post by hyper_ch on 2008-08-05
ok, the 2 gb hdb2 used to be SWAP, right?

that can easily be fixed. However first you need to reinstall grub.

Have a look here:  [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

The first post uses the alternate disk as far as I can tell.

---

### Post by anderssl on 2008-08-05
Restoregrub now installed, it asks me to edit the configuration file, it looks complicated so I think I will try the advice below first... Thanks though!

---

### Post by anderssl on 2008-08-05
tinivole: Restoregrub asks me to edit the configuration file, it looks complicated, think I will try the second advice first... thanks though!

hyper_ch: Have no idea if that partition was SWAP, but it must have been created originally by the ubuntu installation I guess so I guess it is whatever you guys say it is. :) So a stupid question: I only have the installation disk for ubuntu 6.06, but the current installation is 8.04. Can I use the installation cd that I have to restore grub, or should I download one for the current installation?

---

### Post by hyper_ch on 2008-08-05
grub didn't change - I think... so you can use the one you have.

---

### Post by anderssl on 2008-08-05
Ladies and gentlemen, now speaking to you live from my original ubuntu installation, just to say a great THANK YOU! for all your help! I used the 6.06 disk and it worked fine - and my data are back home and safe. Thanks a lot!

Anders

(and now, of course, the big question is: Did my Windows installation survive? ;)

---

### Post by hyper_ch on 2008-08-05
> **anderssl said:**
> (and now, of course, the big question is: Did my Windows installation survive? ;)

Is that important?

;)

btw, you might want to get your swap back ;)

---

### Post by anderssl on 2008-08-05
Well, Windows didn't make it - and yeah it is actually important, I have some stuff that only runs on Windows that I need for my work. But then again, I can just reinstall it. However, with the installation I had, the setup was kind of unelegant - I had to go to the BIOS and swap hard disk priority each time I wanted to boot in the other system. Do you know how to set this up so it can be done just from a menu at startup, like I have it on my other comp? I guess it's the fact that the installations are on separate disks that cause the problem, but can it be fixed somehow?

AND: How do I get my swap back?

---

### Post by logos34 on 2008-08-05
Your windows stanza at the bottom of menu.lst [should look like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Swap: use gparted to delete it, then create a new one.  Replace the UUID in /etc/fstab with the new one.

sudo blkid

---

### Post by anderssl on 2008-08-07
Phew, this took a while, and a bunch of fiddling, to figure out for a noob... But finally, yes it's working like a dream! THANK YOU VERY MUCH! :)

---

### Post by logos34 on 2008-08-07
no prob.

Enjoy

---

### Post by anderssl on 2008-08-24
Hey guys, I'm back with more problems...

After I did as you told me to, everything was working fine for a while. But now Ubuntu crashes on login. It happened yesterday the first time, after putting in username and password the screen goes yellow (as normal) but then freezes. Yesterday I tried to restart, then was told of errors on the hard drive, an automatic fix failed so I had to do a manual one ('fsck'). It gave me lots of errors, I pressed 'y' to fix each one, and then rebooted - and everything ok.

But today it's happening again. Now I left the frozen screen for a while, and finally I got - yes, believet it or not: The blue screen of death... I thought that was a windows thing?!?!? The message reads:

"Could not start the X-client (your graphical environment) because of an internal error. Please contact your system administrator or check your syslog to find out what went wrong. Meanwhile this screen will be deactivated. Please restart gdm when the problem has been fixed." There's an "<Ok>" at the bottom, but nothing happens if I press enter... 

Oh, and one more thing: At boot I always get an error message that says:
"Error 11: Unrecognized device string
Press any key to continue..."

Any ideas or suggestions? I'm still a newb, so please speak like you would to a child. :)

*Update: I rebooted manually from the blue screen, and got back to the same errors as yesterday:
"/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
           (i.e., without -a or -p options)
fsck died with exit status 4"
etc, and then instructions to do fsck, various "command not found" messages and a prompt. I type fsck and get loads of error messages, and press 'y' to fix each of them as yesterday.

---

### Post by anderssl on 2008-08-24
Another update: after the fsck everything works again, but after login I get another error message:

"An error occurred during startup of the program which runs settings for GNOME.

Certain things, such as theme, sounds or background settings may not work properly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.



GNOME will still try to start the settings program next time you log in."

Also, the computer freezes a lot and I get weird noises from the hard disk. This also happened yesterday.

Well well, thank god I at least have windows... But I want my ubuntu to work! Any help?

---

