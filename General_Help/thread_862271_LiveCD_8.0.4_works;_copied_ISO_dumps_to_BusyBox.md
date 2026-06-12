---
title: "LiveCD 8.0.4 works; copied ISO dumps to BusyBox"
date: 2008-07-17
forum: General Help
---

### Post by birdbeast on 2008-07-17
Greetings

I am attempting to make some very minor customizations to the Ubuntu 8.04 LiveCD. I am familiar with the process and have done it before, but the particular platform I'm working on now is giving me some trouble (Dell PowerEdge R200 servers).

Note that the LiveCD that Ubuntu provides works fine.

After I made the customizations, I created an ISO, burned it, and booted from it. It booted properly, but after selecting my kernel in ISOLINUX, and waiting a minute or so, I got dropped to the busybox shell. Looking at the casper.log, it seemed to have trouble mounting the CD-ROM drive containing the ISO. I could mount it without any trouble using a single command (e.g. mount /dev/scd0 /cdrom).

So I thought that something I did was clearly causing problems. I didn't know WHAT problems; I hadn't made any modifications to the initrd and was using the exact same initrd that came on the LiveCD. But just to be sure, to narrow down the issue, I tried again, this time simply copying the Ubuntu LiveCD verbatim onto my hard drive, creating the ISO, burning it, and booting -- in effect copying the LiveCD. 

I got the same problem.

I believe the issue is related to one or both of the following:

1) The Dell PowerEdge R200s have the DRAC 4/P remote management cards in them -- you can use them to get a virtual console of the machine via the network, and view/interact with the machine all the way from boot. They provide a virtual CD-ROM and a virtual floppy; one can use the browser client to put an ISO in the virtual CD-ROM drive and boot from/use it as a normal CD-ROM drive. The OS identifies it as a normal ATA CD-ROM drive. That, along with the SATA CD-ROM drive, equates to two CD-ROMs in the machine, and the initrd may be getting confused about which one to mount -- although, like I said, the stock Ubuntu LiveCD works just fine in both the virtual drive (via an ISO) and the physical drive. But the exact copy I made with mkisofs does not work in either drive.

I've tried disabling the virtual CD-ROM drive -- still get dumped to busybox.

2) My mkisofs command may be incorrect. I copied it from the LiveCDCUstomization Howto, and many others have used it successfully. Here it is:

(in the root directory of the ISO copied to the HDD):

mkisofs -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-6.06.2-desktop-i386-custom.iso .

Note that $IMAGE_NAME is not set when I boot from the Ubuntu LiveCD, so I've tried the command verbatim (setting a blank image name, in effect); I've tried setting an image name in the quotes of the command, I've tried matching that image name with the image name in /README.diskdefines on the CD; all to no avail.

If anyone can help me with this problem it'd be MUCH appreciated. I'm at a standstill and this is really important for me to finish.

Thanks
Birdbeast

---

### Post by birdbeast on 2008-07-17
One more interesting item:

When I boot with the normal Ubuntu LiveCD (the one that works just fine), casper.log begins as follows:

stdin: error 0
/init: /init: 1: cannot open /dev/sdb: No such file
/init: /init: 1: cannot open /dev/sdb: No such file
/init: /init: 1: cannot open /dev/scd0: No medium found
/init: /init: 1: cannot open /dev/scd0: No medium found
/init: /init: 1: cannot open /dev/sr1: No such file
/init: /init: 1: cannot open /dev/sr1: No such file
stdin: error 0
/init: /init: 1: cannot open /dev/sdb: No such file
/init: /init: 1: cannot open /dev/sdb: No such file
/init: /init: 1: cannot open /dev/scd0: No medium found
/init: /init: 1: cannot open /dev/scd0: No medium found
/init: /init: 1: cannot open /dev/sr1: No such file
/init: /init: 1: cannot open /dev/sr1: No such file
stdin: error 0
/init: /init: 1: cannot open /dev/sdb: No medium found
/init: /init: 1: cannot open /dev/sdb: No medium found
/init: /init: 1: cannot open /dev/scd0: No medium found
/init: /init: 1: cannot open /dev/scd0: No medium found
Shadow passwords are now on.
Using '/usr/share/libgksu/debian/gconf-defaults.libgksu-sudo' to provide 'libgksu-gconf-defaults'.
Generating locales...
  en_US.UTF-8... up-to-date
Generation complete.
... [ the rest of the log ] ...

However, when I boot from the copied/regenerated ISO, the messages at the top of the above log repeat 6-8 times, and the log stops with a message like "Unable to locate root filesystem" or something, and that's when I am dropped to the busybox shell.  The "Shadow passwords are now on line" and the lines beneath it are never written.

So it appears that, with the Ubuntu stock LiveCD, the same errors are generated as the regenerateed ISO; but in the regenreated ISO's case, the errors repeat more often (6-8 times) and are eventually fatal.

I've never seen anything this strange before.  Any help is appreciated.  I started diving into initrd scripts, but it just seems illogical to do so, since we're talking about the EXACT SAME INITRD.

Ugh.

Thanks for any help
-bb

---

