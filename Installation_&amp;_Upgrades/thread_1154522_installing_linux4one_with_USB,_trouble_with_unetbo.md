---
title: "installing linux4one with USB, trouble with unetbootin?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by karasuman on 2009-05-09
I'm following the guide here: [http://www.linux4one.it/forum/index.php?topic=144.0]("http://www.linux4one.it/forum/index.php?topic=144.0") without much luck.  For one thing, I don't know how to format my thumb drive; there isn't an option when I right-click.  I think it's already formatted to use FAT32, though, so I skipped this step and tried to continue.  I installed unetbootin and ran it, but it can't find the iso on my computer.  When I run unetbootin, it finds only two directories: root and computer, and one subdirectory, desktop.  No files.  No iso.

What am I doing wrong?

---

### Post by logos34 on 2009-05-09
sounds like you did everything correctly...now, if you could just find the iso.

Under Computer, do you see a "File System"?  Look in there for /home.  Hopefully the iso will show up

---

### Post by thesavager on 2009-05-09
Hi karasuman,

Just click "Computer" then you will see "/", click on that also.
Now click on "Home" --> "<your username>"

So if you downloaded the iso with firefox, firefox downloads are at your Desktop at default.

Goodluck, Savage

---

### Post by karasuman on 2009-05-10
Thanks for the help; I don't know what I was doing wrong.  Maybe I forgot to turn my brain on.

Actually, I'm pretty sure that that IS what happened, because I just realized that my crappy thumb drive is only half a gig, and that's not enough for this.  I do have a ginormous external hard drive... is there any way to modify this process to boot from that?

---

### Post by logos34 on 2009-05-10
in that case I believe you can still boot unetbootin on the usb, point it to the iso on your internal hdd, and install to the big external usb. You could also run Unetbootin from the internal hdd, so-called 'frugal' install:
> [URL="http://unetbootin.sourceforge.net/#install"]
Features[/URL]

UNetbootin can create a bootable Live USB drive, **or it can make a "frugal install" on your local hard disk if you don't have a USB drive. **It can load distributions by automatically downloading their ISO (CD image) files, **or by using existing ISO files**, floppy/hard disk images, or kernel/initrd files, for installing other distributions.

So in the unetbootin window try navigating to the iso ("Disk image"), then in the dropdown menus at the bottom select the target drive --> "Type: Hard disk" and the "Drive" letter of the partition on the big external usb disk.  

[IMG]http://sourceforge.net/dbimage.php?id=173795[/IMG]

---

