---
title: "Files moved to USB key dissapeared"
date: 2015-10-05
forum: Hardware
---

### Post by alain.roger on 2015-10-05
Hi,

i moved files and folders from my HDD to my USB key.
For an unknown reason the files and folders are not anymore on the USB key.

i did not delete then...they are just gone.

my USB key is formated in NTFS and i was wondering if there is a way to recover those lost files and folders ?

thx

---

### Post by dino99 on 2015-10-05
are you sure they are gone ? or simply hidden: check the free space of that stick or have a look with a partitioner

---

### Post by alain.roger on 2015-10-05
in fact during moving step from HDD to usb stick, it seems an error occured at the end of the moving process.

I tried on USB stick foremost and photorec without any success :( so as they were moved from HDD directory maybe i can recover them from there.

So, is there a way to recovery files from original directory from my HDD ?

---

### Post by Bucky Ball on 2015-10-05
You've tried one of the recommended ways. Did you also try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk")?

---

### Post by alain.roger on 2015-10-05
As far as i know testdisk is a photorec tool, no ?

---

### Post by yancek on 2015-10-05
If you go to the Photorec site, you will see this statement:  PhotoRec is a companion program to TestDisk, an application for recovering lost partitions on a wide variety of file systems and making non-bootable disks bootable again. You can download them from this link.  If you go to the link, it will show download TestDisk and Photorec comes with it.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Were you moving them from an ntfs partition to an ntfs partition on the usb?
Did you do this from windows?  From Linux?
If you got an error at the end of the moving process, what was it?
How did you move the files, copy/paste, use a terminal?

---

### Post by alain.roger on 2015-10-06
I moved files from NTFS partition to a NTFS USB key and everything using Linux Kubuntu 15.04
basically the errror was that process stopped but nothing special as message as no message has been displayed :(
i moved files using Dolphin.

---

### Post by yancek on 2015-10-06
> I moved files from NTFS partition to a NTFS USB key and everything using Linux Kubuntu 15.04

It should work but if I were moving files from an ntfs to an ntfs, I'd use windows.
Did you check when you initially moved the files/folders to see that they were actually there?  You seem to imply that in your initial post.

So the message you got was the process stopped and not that there was an error?

---

### Post by Bucky Ball on 2015-10-06
Did you right click the USB and 'Safely Remove'?

---

### Post by tgalati4 on 2015-10-06
Sometimes, when moving files in Dolphin or Nautilus, the progress bar shows finished, but the actual writing of the files is not finished.  The slow speed of USB transfer causes buffering and when a large number of files are moved, the file manager shows that the process is completed (and it is in RAM) but the writing of the buffers to a USB flash drive takes time.  Pulling the thumb drive before it has finished will cause errors.  One needs to Right-Click, Eject on the thumb drive icon, before removing.  This is similar to "Safely Remove".

Try using *testdisk* first and then *photorec* on the hard disk to find the missing files.  Make sure you have a large USB stick or external drive to receive the recovered files.

---

