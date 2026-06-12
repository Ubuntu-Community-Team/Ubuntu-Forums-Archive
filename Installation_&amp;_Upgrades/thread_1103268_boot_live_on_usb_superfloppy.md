---
title: "boot live on usb superfloppy"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by luke67m on 2009-03-22
First the result : i am writing this from ubuntu 8.10 live 'installed' and booted from a usb superfloppy pen drive.
This has been a bit difficult bee the procedure included in ubuntu 8.10 try only to create HD like usb drive.

Initially i have tried to use the menu driven procedure but i discovered that my old notebook was not able to boot from my pen drive configured in this way as a hard-disk whit mbr and partitions.
Then i discovered that the bios of all the pc where i tried my pen drive recognized it as a floppy [superfloppy] and not as a hd.
So i start searching a way to install ubuntu live on my pen configuring it as a superfloppy. I found a lot of note that all said to create mbr and partition and activate and use grub, but this is not good for me. Then i remebered that SLAX could be easily installed on a usb key and so i tried it. Bingo. With SLAX , fat16, mkdosfs in superfloppy mode and syslinux with -s parameter i was able to boot from my 2giga usb pen drive [mp3 player] in written protected mode.
The second step was to copy all the content of and SD card where i installed ubuntu 8.10 with the menu driven procedure and to add a line in the slax.cfg copied from text.cfg of ubuntu.
I have written this for 2 reason : 
First : Some pen drive are recognized by bios as superfloopy and not as hd and you must configure them as superfloppy and not as hd
Second : please ubuntu can you adapt your script to manage Superfloppy usb pendrive?
Then next step is to verify if -s parameter of syslinux is needed.
Then if there is an easier way to do the thing.
Bye.

---

### Post by luke67m on 2009-04-12
The -s parameter of syslinux is NOT necessary. I've tryed without it and my notebook boot ok and (of course) boot is faster. So the right way to boot my notebook from my usb key is to format it as Superfloppy with   mkdosfs -I -F 16   and to install syslinux in normal way (no -s). The next step is to try to have th native ubuntu boot menu. Now i use this lines added to the slax slax.cfg : 

```
label live
menu label Ubuntu in italiano
kernel /casper/vmlinuz
append  noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash locale=it_IT preseed/locale=it kbd-chooser/method=it console-setup/layoutcode=it --
TEXT HELP
                                          More about currently selected:

                                          ubuntu 8.10 live da slax609
ENDTEXT


```

By luke67m

---

