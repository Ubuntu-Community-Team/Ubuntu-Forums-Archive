---
title: "Freevents x56 and ubuntu 9.10 install - How I did it"
date: 2009-11-06
forum: Hardware
---

### Post by douvet on 2009-11-06
Aright peeps, first post but here goes

Basically spent ages trying to get Ubuntu 9.10 to run on my laptop [Freevents x56], finally got there and this is how I did it

1. Downloaded the live cd version, burn to disk.

2. Before you can boot the live cd you have to reserve some memory space that the bios fails to do every time, so:- [INDENT] * highlight, try live CD without touching the hard drive,
* then press F6 to enable the command line.
* press Esc to close the pop-up list.
* before "quiet" enter **reserve=0xFFB00000,0x100000** (Should look something like ..... ro **reserve=0xFFB00000,0x100000 **quiet.....)
* press enter to start the live CD.
[/INDENT]3. Install the system when the live CD has loaded, just as you would normally, But at the end off the install **DO NOT RESTART!!**. just continue to try the live CD

4. Now open up a terminal and navigate to the root of the hard drive, it should be the only hard drive in the media folder (should look something like /media/373h395-382734645-182734/)

5. once in root navigate to etc, then the modprobe.d folders (etc. cd /media/373h395-382734645-182734/etc/modprobe.d/)

6. next open up blacklist.conf using gedit in admin mode - [B]sudo gedit blacklist.conf

[/B]7. Navigate to the bottom of the file and add these 3 lines
```
blacklist sdhci-pci
blacklist sdhci
blacklist mmc_core
```8. Save the file, then restart the system.... this should get Ubuntu to boot with wi-fi but without the SD card slot that's built into the front.

That's how I got it working, unfortunately I'm still a linux/ubuntu novice so not sure how to add the SD reader back in later on.

Thanks goto basically everyone on ubuntuforums for the info on the memory bios bug and to Hawkz for his post on blacklisting the modules. =D>

---

