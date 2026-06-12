---
title: "DVD +/- RW won't mount when inserted and makes Ubuntu unstable"
date: 2006-05-26
forum: Hardware &amp; Laptops
---

### Post by digby280 on 2006-05-26
Hi.  I have an NEC DVD +/- RW ND-2500A.  I can open the drive when Ubuntu starts and then close it again, but after that it locks and it won't open again using either the button on the front of my computer, eject in Ubuntu, or the unmount and eject script that I found in these forums.  It also doesn't mount the CD/DVD that I insert and I can't mount it manually either, however, I can get it to mount a CD/DVD if I leave it inserted and reboot the computer.  I can open the drive sometimes using but sticking a pen inside and pressing the button on the DVD drive - its a cube type and the button on the front does not directly press the DVD drives button.  If this doesn't make sense details can be found at:

[http://www.msi.com.tw/program/products/slim_pc/slm/pro_slm_detail.php?UID=547]("http://www.msi.com.tw/program/products/slim_pc/slm/pro_slm_detail.php?UID=547")

I was running Breezy and the effect of this was as above and I could not access the 'Disks Manager' once I had opened and closed my DVD drive.  I upgraded to Dapper in an attempt to solve the problem and now I get some errors that appear when I shut down / restart my computer after opening and closing the DVD draw (as well as the previous problems).  The errors appear immediately after 'Will halt all' right at the end of the shutdown process.  The screen switches out of the graphical shutdown to the UNIX look (like Breezy) and [OK] appears next to 'Will halt all' and then a series of errors like this one appear:

[4301380.704000] ata2: command 0xa0 timeout, stat 0x58 host_stat 0x0

If I have inserted a disc these errors seem to continue indefinitely.  However, if I have simply opened and closed the drive without inserting a disc this error is only repeated a few times and then the computer successfully shuts down.

As well as this (before I attempt to shut down) the pointer starts freezing for 5-10 second intervals and Ubuntu becomes generally jumpy.

Just a bit of extra information which may or may not be useful.  I have just attempted to activate dma, because some other threads I have read made me feel this could be a possible solution, but I got the following errors and thought this could be related:

sudo hdparm /dev/scd0
Password:

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

This part is the same as post: [http://www.ubuntuforums.org/showthread.php?t=182650]("http://www.ubuntuforums.org/showthread.php?t=182650")

To summarise, I'm now using Dapper, I have a NEC ND-2500a DVD +/- RW, Intel P4 3GHz, and most of the other information is the same as can be found here: [http://www.msi.com.tw/program/products/slim_pc/slm/pro_slm_detail.php?UID=547]("http://www.msi.com.tw/program/products/slim_pc/slm/pro_slm_detail.php?UID=547")

Sorry it's a bit long.  I wanted to make sure I got everything down.  Let me know if you need more information.

Thanks in advance.
Pete

---

### Post by digby280 on 2006-05-28
Quick update.  I seem to have found a kind of solution to this problem, although it's not ideal.  If I use the "eject" command in the terminal to eject the DVD drive and "eject -t" to close it works fine.  I just have to remember not to press the button on the front of my computer :( .

---

