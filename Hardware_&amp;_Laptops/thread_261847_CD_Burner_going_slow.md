---
title: "CD Burner going slow"
date: 2006-09-20
forum: Hardware &amp; Laptops
---

### Post by offramp13 on 2006-09-20
I have a 48x CD-RW drive, and when i try to rip music it goes at only 5x or 6x, anyone know why?

---

### Post by JAwuku on 2006-09-20
It could be that Direct Memory Access (DMA) which increases read and write throughput is disabled by default in Ubuntu.

You can switch it on quite easily  by seeing the instructions in this blog:

[http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/](http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/)

You might not get close to 48X but you should see a good speed increase. Also speed of ripping is limited by CPU speed and RAM size.

Hope this helps! :)

To Quote:

If your CR Rom drive, or the CD-RW drive, or your DVD reader/writer are slower than their stated speeds for reading or writing (burning), then you may not have DMA (Direct Memory Access) enabled on the drive in question. DMA allows for faster data access for drives that support it by effectively not using CPU time for data transfer to put it really simply.

You can check if the cd drive has the option enabled by doing a:

**[COLOR="DarkRed"]sudo hdparm /dev/hdc[/COLOR]**

Where “hdc” stands for the drive in question - change this if it is different on your machine (you can find out by looking in the [COLOR="DarkGreen"]**/etc/fstab**[/COLOR] file)

If it says “dma = 0&#8243; in the output of the command, then that means that dma is currently disabled for the drive.

You can enable it temporarily for the current session till you shutdown the computer by using the command:

**[COLOR="DarkRed"]sudo hdparm -d1 /dev/hdc[/COLOR]**

This will be reset when you reboot. You can make the change more permanent by editing the file [COLOR="DarkGreen"]**/etc/hdparm.conf**[/COLOR], and adding the following to the end of the file:

[B][COLOR="DarkRed"]/dev/hdc {
dma = on
}[/COLOR][/B]

This will turn on dma each time you boot up the computer.

Also, if you cd/dvd writer provides for some form of buffer under-run protection, you can enable nautilus to use this when it writes to the disc by using the “burnfree” option. You can set this option by doing :

[B][COLOR="DarkRed"]gconftool-2 –set –type boolean /apps/nautilus-cd-burner/burnproof true
[/COLOR][/B]
Note: Your system BIOS also gets to decide how your drives behave, so check to see if the proper options are enabled in the BIOS upon boot-up.

There! Now you should be able to read/write from optical drives at the best possible speed.

---

### Post by offramp13 on 2006-09-20
Thanks for the help!

---

