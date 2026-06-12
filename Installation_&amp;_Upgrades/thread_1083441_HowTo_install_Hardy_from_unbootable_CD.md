---
title: "HowTo install Hardy from unbootable CD"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by bcw on 2009-03-01
This HowTo allows booting/installation from the CD when your computer won't. The details below are for Hardy, and have worked for me with both the Xubuntu & Kubuntu install CDs.  They didn't work for me with Intrepid Ibex, but you could always install Hardy and do a dist-upgrade.

For some people, the Smart Boot Manager diskette will allow this, but it does not work for USB CD drives. This approach works if your system will boot off a floppy. The idea is to get access to the CD from DOS, then call the installer on the CD with LinLoad.


**Make the boot diskette**

I have attached a compressed floppy image of the boot disk for download from the link at the end of this post.  Download the image, save it somewhere you will remember.  Then open a console, and navigate to that place.  Unzip the archive with this command:
```
gunzip hardyUSB.img.zip
```

I'll assume you're using a desktop machine.  On one of those, your floppy device name is '/dev/fd0'.  If you have two floppy drives installed on the machine, you might choose '/dev/fd1'.  If you're using a laptop, you'll have to inquire about the device name of the floppy drive.

Make sure the floppy diskette's little slider is covering the cutout, so it can be written to.

Run this command if you're using a Linux box (changing the device name if appropriate):
```
sudo dd if=hardyUSB.img of=/dev/fd0 count=1 bs=1440k
```

If you're using Windows, you'll use a program called rawrite.  Search in the forums or on the web - there are many good howtos.

With a good floppy & drive, this will re-create the bootable diskette with the USB DOS drivers.


**Boot up to get access to the CD**

Now, plug everything in, and place your [K,X]ubuntu CD in the drive, and boot on the floppy.

I used a USB keyboard, mouse, powered hub, and external CDROM, and all worked once I found the right device drivers.  However, I have had some combinations provide access to the CDROM, but disable the keyboard.  In that case, I use a ps/2 keyboard and mouse, and much hardware old enough not to boot on USB will have connectors for ps/2 devices.

If your CD is not USB, but appears as a drive already, just go on with the rest of the instructions.  See '**Call the installer**' below.

This diskette has a collection of USB device drivers & schemes, and a menu for selecting them. I don't know if the ones that worked for me will work for your hardware - please post your own results for us all to see if you try this. But this diskette has most of the USB device drivers available, and while it may be tedious, you will probably find a combination that works. The menus make it relatively easy to try (a lot easier than editing the configuration files each time to change).

All up, there are 48 possible combinations which will cover most of the devices out there.

The first choice to make is the memory manager, and the default is choice 2.  You will see a 20 second countdown until this choice is made, and you can choose one of the other 3 choices.  I have no idea which will work for what hardware - start with one, and you'll know when you get a DOS drive letter assigned to your USB CDROM.

The next choice is one of 4 usbaspi drivers.  Same deal - pick one, and keep track of what you pick.  You must reject each one to be offered the next one, but the prompts make it obvious what to do.

The last choice is the CDROM driver - one of the three choices.

What you are looking for is a screen that ends with something like this:
```
.....
Drive  Driver   Unit
  C:   USBCD001   0
---------------------------------------

CuteMouse v1.9 [FreeDOS]
Installed at PS/2 port

A:>
```

Keep trying different driver combinations until you get a letter assigned to your drive, although it might be other than 'C'.


**Call the installer**

The **A:>** prompt is the Free DOS prompt, and the lines above show that my USB CDROM drive was found and assigned the DOS drive letter 'C'.  If you have DOS or Windows partitions on the hard drive of the computer you're installing to already, you might receive a different letter - 'D' or 'E' or...

Make a note of the letter.  You'll need it in a moment.

The next step is to determine the name of the folder the Linux boot files are in on the CD.  So, take whatever letter your CDROM was assigned and ask with this command (substitute your own assigned letter):
```
dir c:\
```

You'll see something that looks like this:
```
 Volume in drive C is Xubuntu 8.0

 Directory of C:\

README   DIS           224  07-01-08  4:57a
_DISK                <DIR>  07-01-08  4:57a
CDROMUPG               942  04-22-08  7:07a
DISTS                <DIR>  07-01-08  4:57a
DOC                  <DIR>  07-01-08  4:57a
INSTALL              <DIR>  07-01-08  4:57a
ISOLINUX             <DIR>  07-01-08  4:57a
MD5SUM   TXT       137,200  07-01-08  4:57a
PICS                 <DIR>  07-01-08  4:57a
POOL                 <DIR>  07-01-08  4:57a
PRESEED              <DIR>  07-01-08  4:57a
UBUNTU                   0  07-01-08  4:57a
         4 file(s)        138,366 bytes
         8 dir(s)               0 bytes free
```

Notice the '**INSTALL**' directory.  I've also seen '**CASPER**', and perhaps something else might appear on other install CDs.  You can tell when you've got the right name by running this command (substitute your own assigned letter & the directory name you're checking):
```
dir c:\install
```

You'll see something that looks like this:
```
 Volume in drive C is Xubuntu 8.0

 Directory of C:\INSTALL

.                    <DIR>  07-01-08  4:57a
..                   <DIR>  07-01-08  4:57a
README   SBM         1,865  10-19-07  6:08p
INITRD   GZ      5,305,592  07-01-08  4:57a
MT86PLUS           103,204  09-28-07 11:06a
NETBOOT              <DIR>  06-19-08  8:27p
SBM      BIN     1,474,560  10-19-07  6:08p
VMLINUZ          1,920,472  07-01-08  4:57a
         5 file(s)      8,805,693 bytes
         3 dir(s)               0 bytes free
```

When you see '**VMLINUZ**' you know you've got the correct name for the directory on your CD.

Now take those two items, and run this batch file to start the install - remember, my example here uses my CD letter (c) and my CD's directory name (INSTALL), and remember DOS doesn't care about upper or lower case:
```
hardyUSB c install
```

This should start your CD spinning, and start the [k,x]ubuntu install.  If not, review the instuctions above.




Here is how to create the FreeDOS boot diskette found here:
[http://johnson.tmfc.net/dos/index.html]("http://johnson.tmfc.net/dos/index.html")

Add the 'linld.com' program:
[http://lwn.net/Articles/102210/]("http://lwn.net/Articles/102210/")

Create a script file (a batch file) containing this one line (all on one line):
```
linld image=%1:\%2\vmlinuz initrd=%1:\%2\initrd.gz "cl=root=/dev/ram boot=install ramdisk_size=1048576 devfs=mount,dall"
```

I named my script 'hardyUSB.bat'. All of this goes on this one FreeDOS boot floppy. There's plenty of room.


Kudos to Marc Herbert, for his excellent work devising the basis of this approach. He also mentions the instlux sourceforge project that is built on his work. 
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")

Thanks to the fellow who assembled the FreeDOS boot diskette & drivers. I can't tell easily from his web site, but I think he's Lam Chun Sang Johnson.

---

