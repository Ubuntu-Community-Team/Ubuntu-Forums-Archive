---
title: "Can't Find Way To Install Xbuntu to a Pen Drive"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by boothruwindow on 2009-03-21
This should (really) be the stupidest question ever asked, but I just spent an hour trying to google up an answer to this question. Sometimes searches are mired in mysterious ways, maybe I'm the only one who didn't see an obvious answer, and then maybe my Taiwanese Acer and it's hardware are giving me problems which Intel users don't have, but I cannot find a way of installing Xbuntu onto a pen drive. Unlike the Ubuntu (GNOME) version, I can't find a menu option to get it installed this way. Yes, I did try the Install program, which took me into the partitioner with no menu options, and I wasn't about to install it on my hard drive just yet. I understand there's really no magic to these .iso files and the burning process, but being from DOS world, maybe there's some formatting issues (special boot format?), and anyway my two pen drives (brand new, by the way) both have the fallout of failed DreamLinux installation attempts (the goobers who created that OS actually wrote the program into their GUI, which failed), and Ubuntu will not remove these messed up files (whyyyyyy???????). So, I cannot (not through GNOME, anyway) clear the way for a simple .iso copy and paste, even if it is that simple - but anyway, what goes on behind the GUI when you do an install - would I need to do more than get it moved to the pen? If not, how do you get rid of stubborn files (is there a linux format command), and if so, what do you do then?

Please help, if you know how.

Thanks.

---

### Post by sgosnell on 2009-03-21
Just run the install program, which should show you all the drives on your computer, including the USB drive.  You need to have it connected when you boot the live CD.  Just make sure you're getting the right drive, which should probably be sdb, unless you have multiple hard drives or another USB drive or a memory card attached.  Sda is the first drive, with sda1 being the first partition on it.  The second drive should be sdb, and sdb1 would be the first partition on that.  When the partitioner comes up during the install, select sdb, and probably choose to use the entire drive.  The install should be straightforward from there.  You probably want to make sure the format box is checked.

If you just want to format the drives, run gparted, which is a GUI paritition editor/formatter, and you can remove all the partitions already on the drive, then make a new partition and format it.  If there is just one partition on there now, you can just format it in gparted.

---

### Post by Matt Yun on 2009-03-21
Try [unetbootin]("http://unetbootin.sourceforge.net"), a gui utility to create bootable live USB drives for a variety of distros.  

If you want to know more about Linux installs to pendrives, you should peruse the articles at [pendrivelinux.com]("http://www.pendrivelinux.com").

---

### Post by tom4jean on 2009-03-21
Alternatively, [www.pendrivelinux.com](www.pendrivelinux.com) worked very well for me.

---

### Post by boothruwindow on 2009-03-21
> **tom4jean said:**
> Alternatively, [www.pendrivelinux.com](www.pendrivelinux.com) worked very well for me.

More votes for that website??? I saw it, and then I saw the ORDER buttons, - I don't know why I would see that where there isn't somebody selling what's already free!

---

### Post by boothruwindow on 2009-03-21
> **sgosnell said:**
> Just run the install program, which should show you all the drives on your computer, including the USB drive.  You need to have it connected when you boot the live CD.  Just make sure you're getting the right drive, which should probably be sdb, unless you have multiple hard drives or another USB drive or a memory card attached.  Sda is the first drive, with sda1 being the first partition on it.  The second drive should be sdb, and sdb1 would be the first partition on that.  When the partitioner comes up during the install, select sdb, and probably choose to use the entire drive.  The install should be straightforward from there.  You probably want to make sure the format box is checked.

If you just want to format the drives, run gparted, which is a GUI paritition editor/formatter, and you can remove all the partitions already on the drive, then make a new partition and format it.  If there is just one partition on there now, you can just format it in gparted.

I'm wear'n egg for not seeing that on the end of one (out of two) options which appeared to be SCSI-type hard disks, way out on the end (never seen this gobbledygook in front of my drive options elsewhere) was my SanDisk Cruzer. 

Well, it did the transfer to that 8G Sandisk, but it killed my GRUB, too - I get that error 25, or 23 when I try to boot my hard disk now. I booted the CD again, and in the partitioner I saw that I still have my origional partition which contained an installation of Ubuntu Ibex (and much of my time invested. I've noticed that many complain about this in the forums, and I've just looked up a solution by Kipper, but I need more detail for my situation. I don't know where, after booting again with the CD, that you would type in Rescue. I have a fatal GRUB error when I try to boot the hard disk, and I get no opportunity to type in anything before that happens. To boot the CD, I hit the F12 key, then select my CD drive, and then I get the main CD menu. No prompts to enter anything here, and the options are 
[CENTER]Try Ubuntu...
Install Ubuntu
Check CD for defects
Test Memory
Boot from first hard disk
[/CENTER]I checked the F4 and F6 options for each of these, and saw nothing on recovery. So, how do I get to that Recovery menu, when GRUB seems to be blocking it?

---

### Post by sgosnell on 2009-03-22
Sorry, I forgot to mention that at the final step, you need to click on the Advanced button and select to install the bootloader on the USB drive, probably (hd1).  Doing that lets you boot without having the USB drive connected.  You should be able to boot to the HD by pressing Esc as soon as the BIOS screen starts to go away.

To fix the grub problem, if you can't boot from the USB, boot from the live CD.  Open a terminal and type
>     sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit
That should fix things, and you can boot from the HD directly.  To boot from the USB drive, you'll need to make it the first boot drive in your BIOS.

---

### Post by C.S.Cameron on 2009-03-22
On a desktop I usually find it easiest and most sure to disable my hard drives before doing an install.

---

### Post by bubwitmaingay on 2009-03-22
Ubuntu supports usb-create, but if you love to play around like a techie, you can go to the terminal (although it is still GUI).

Download UNETBOOTIN from their site (usually the downloade file is saved in the Desktop).

Open Terminal and go to the directory where UNETBOOTIN was downloaded.

```
cd ~/Desktop/
ls -l
chmod a+x unetbootin-linux-313.bin
./unetbootin-linux-313
```

> The "cd" command transfer you to the directory
The "ls -l" command lists all the files in the directory (including the file extension, so you can be sure of what to type/encode)
The "chmod a+x" command makes the file executable
The "./unetbootin-linux-313" command lets you open the GUI of unetbootin

A window will appear with the unetbootin. Hope that helps. 8)

---

