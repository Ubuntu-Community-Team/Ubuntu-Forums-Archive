---
title: "Help Running Ubuntu 8.10 Off a 4gb Flash Drive"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by russet_wolf on 2009-01-24
I'm very new to Ubuntu (and Linux in general), having just installed Ibex about two weeks ago on an external USB hard drive. I love it! but I want to make it a little more portable. I have a 4gb flash drive that I would like to dedicate to Ubuntu as my portable OS, instead of my big clunky (in comparison) external USB hard drive, which I've been using as my default anyway. I have a lot of questions:
[LIST=1]
[*]Is 4gb enough? I'm not going to be doing anything huge on it, like installing who knows what size of programs, but I would like to be able to carry a few files and do the basics like surfing and YouTube-ing.
[*]How should I partition? I've read around a little and saw something about using an ext2 instead of ext3 to reduce the writes made to an SSD.
[*]What other tricks are there for optimizing the life of the SSD? Any settings at install or mounting temporary files somewhere?
[*]Also, how long can I expect the flash drive to live, running Ubuntu?
[*]I know it's a lot to ask, but I would also like to be able to have a separate partition (NTFS) for my files so that Windows computer an read them (using it as a thumb drive)
[*]Is there a better version of Ubuntu than 8.10 to install on a flash drive? Perhaps something smaller?
[/LIST]
I'm sure I'll have more questions later, but these I think are enough to get me started. Does anyone have any suggestions?

---

### Post by snowpine on 2009-01-24
Hi Wolf, the Ubuntu 8.10 live CD has a feature (in the system menu) for creating a bootable USB device. You can set up a "persistent" live USB, meaning the filesystem is compressed like on the live CD (good for preserving the life of the drive) but you can save files, install new applications, etc. It should fit easily on your 4gb drive, and you can have an NTFS partition too. :) I think the NTFS partition needs to be the first one on the drive in order for Windows to recognize it.

---

### Post by russet_wolf on 2009-01-25
Thank you! What do  have to know to set up a persistent USB? Any partitioning requirements? or does it do everything on it's own?

---

### Post by Browser_ice on 2009-01-27
But using the Ubuntu USB creation process off the Live CD, creates just that, a live CD version on the USB. I did it and was disapointed to see upon booting with my USB key that it was still a Live version. I was expecting to have a full operating version with ID login session and not a Live CD version (where you HAVE to choose bettween install or run a live version).

---

### Post by snowpine on 2009-01-27
If the USB Creator isn't what you're looking for, you can also do a full install to a USB drive. This is just like installing to your "regular" hard drive. The only tricky step is making sure the Grub bootloader gets installed to the correct drive (the USB drive instead of the hard drive). You can do this in Step 7 of the installer by clicking Advanced Options. 4gb is borderline for this type of install; you won't have much space left over for files, so I recommend 8gb or larger for a full USB install. This is the type of install I use personally.

---

### Post by russu52 on 2009-01-27
hi
i would like to add a few comments:

the machine has to accept booting from pendrive (booting from usb hdd is not the same)
if the machine is slow, then i suggest xubuntu. although it appears to be a live cd, you can save your changes onto it - and works faster too.

---

### Post by russu52 on 2009-01-27
just forgot...

4gb are more than enough for xubuntu

---

### Post by snowpine on 2009-01-27
ps If you are not attached to Ubuntu, there are a couple of micro-distros like Puppy and SliTaz that have amazing tools for installing to USB. Because they load the entire OS into ram, there is minimal wear and tear on the flash drive. Probably not what you're looking for, but worth mentioning...

---

