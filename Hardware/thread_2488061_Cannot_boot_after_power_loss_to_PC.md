---
title: "Cannot boot after power loss to PC"
date: 2023-06-21
forum: Hardware
---

### Post by yellowcedar on 2023-06-21
[FONT=arial]I was running Kubuntu 22.04.2 LTS.  [/FONT][SIZE=2][FONT=arial]The switch on my power strip accidentally got switched and my PC lost power while it was running.  Now when I try to boot back up I am having issues.  

When I try to boot, grub loads and kubuntu begins booting, it then prompts me for my password to decrypt my hard disk as usual.  After I enter the password it then proceeds to the kubuntu logo screen (as usual), but then it flashes a couple of lines of text quickly on the screen.  It is impossible to read what it says.  After this it sends me to a black screen and does absolutely nothing no matter how long I wait.  I cannot press any keys, nor type and commands here.  The only way to reboot at this point is to shut off the power switch to my motherboard and turn on again.

I have tried to boot in recovery mode.  When doing so I see an error when mounting the root filesystem.  It says "cannot process volume group vgkubuntu, volume group not found" It does then send me to the recovery screen where I choose to enter the root prompt.  In root I have tried 
```
sudo fsck -f /
``` but it gives me no errors or useful information.  

I then tried booting kubuntu from a usb and going to "try kubuntu".  Then in the terminal I ran gparted on the EXT4 partition of my hard disk.  It processes this without issue and returns no errors.

If I try to run ```
sudo fsck -f /dev/nvme0n1p3
``` in terminal it checks without error and returns "/dev/nvme0n1p3: 607/109536 files (1.0% non-contiguous), 89796/437504 blocks"

If I try to use the GUI to navigate to my hard disk while running kubuntu from the usb drive it prompts for password, and when I enter it, then I get "An error occured while accessing '3.6TiB Encrypted Drive', the system responded: 
"An unspecified error has occured: No such interface "org.freedesktop.UDisks2.Filesystem" on object at path /org/freedesktop/UDisks2/block_devices/dm_2d0"

I have no idea what else to try at this point.  It appears my disk has gotten corrupted somehow from this power outage?  Any help is greatly appreciated.  I have ALOT of work ahead of me if I cannot get this back up and running.







[/FONT][/SIZE]

---

### Post by yellowcedar on 2023-06-21
I was able to boot up in the earlier kernel version by going to advanced in grub after holding shift upon startup.  Booting into 5.19.0-45-generic was giving me issues, however booting into 5.19.0-43-generic works.  Is this going to be problematic moving forward?

---

### Post by yellowcedar on 2023-06-21
I just ran```
sudo apt install -f && sudo apt upgrade
```

Now I am able to boot into the newer kernel.  It must have been an issue with doing the update prior to the power outage event and not rebooting the system in the typical way.  So I guess before the updated kernel never installed properly when it was a forced reboot.

It just strikes me as strange that I was seeing errors while trying to access the drive from the kubuntu usb media.  Oh well it works now

---

### Post by Bashing-om on 2023-06-21
yellowcedar - hello

What results from the kernel checking the validity of the non-booting kernel / and maybe fixing:
From the booted -43 kernel run:
```

sudo update-initramfs -u -k 5.19.0-45-generic

```

Might also be of value 1st to run a file system check (fsck) from a liveUSB.

[INDENT]I  believe in magic
[/INDENT]

---

### Post by oldfred on 2023-06-21
If you are using full drive encryption, you must have good backups.
And corruption of the encryption, may prevent any sort of data recovery from drive. Backups are then only recourse.

What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
Change to exclude line:
[https://ubuntuforums.org/showthread.php?t=2484708](https://ubuntuforums.org/showthread.php?t=2484708)
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

---

