---
title: "Ubuntu 9.10 on USB stick: No operating system found"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ma84jo on 2009-11-06
Hi all,

I was planning on starting my Linux era with Ubuntu 9.10. Installed it from CD on an 8GB USB drive. Set BIOS to boot from said USB drive before built-in hard drive.

If I switch on computer (acer Aspire laptop), it will ignore USB drive and boot Win Vista from hard disk.

If I force computer to try and boot from USB via the BIOS boot menu, it says: No Operating System found. Why? How can I convince it that there actually is an operating system installed?

I consciously did not install grub boot manager because when I tried Ubuntu installation + grub yesterday, nothing booted anymore: Grub said NO SUCH DRIVE and I couldn't even boot windows anymore without some hassle.

Will I forever be unable to run Ubuntu on this computer? Anything I can do?

Thanks in advance for your help.

---

### Post by dandnsmith on 2009-11-06
Sounds like the USB drive isn't properly set up, or your laptop isn't capable (unlikely, as you've got Vista on it).
What process did you use to set it up?
You need syslinux (or equivalent) installed on the usb drive to make it bootable (not grub)

---

### Post by Sealbhach on 2009-11-06
Use Unetbootin to install a bootable Live istall of Ubuntu. It's really easy to use:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Just delete whatever you have already put on the USB and do it the easy way.;)

.

---

### Post by jaduvet on 2009-11-06
Seems there is a problem with the dist. At least i havent found a solution to the same problem. And there is some other threads reporting same problem in different ways
 
  there is no usb-creator.exe on the 9.10 x64 disk and it seams the problems applies also if you try to use unetbootin 
 
 But still no explanation if this is a user (you, me and her rest) error or a ubuntu error (embarasing then)
 
 threads:
 
 [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1317008](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1317008)
 [http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8255508](http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8255508)
 [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1310707](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1310707)
 [http://ubuntuforums.org/showthread.php?p=8257120](http://ubuntuforums.org/showthread.php?p=8257120)
 [http://newyork.ubuntuforums.org/showthread.php?t=1313987](http://newyork.ubuntuforums.org/showthread.php?t=1313987)

---

### Post by ma84jo on 2009-11-07
I used the USB drive fresh out of the box, let it be formatted with both kinds of Linux file systems by the Ubuntu installation.

As was suggested in Reply #4 maybe I&#8217;ll wait for a next distribution or else try unetbootin.

Thanks for all your replies thus far!

---

### Post by utnubuuser on 2009-11-07
the only version I've sucessfully been able to make a USB-flash startup from is Intrepid Ibex.  In Intrepid the application was working correctly.  All other attempts result with the same isssue of "No OS found" or a blinking cursor.

---

### Post by ma84jo on 2009-11-08
What finally worked was installing grub on the same USB drive as Ubuntu. If the USB stick is connected, now Grub will ask me whether I want to boot Vista or Ubuntu. (Of the two identical Vista choices one works, one doesn&#8217;t.) 

If the drive is not connected, my notebook will start Vista same way it always did.

Before I could attempt to install Ubuntu on the USB drive again, I had to reformat it using G-Parted, though.

Now my only remaining problem is that Ubuntu won&#8217;t accept the user password I&#8217;m sure is the same I set during installation...

Thanks again for all your tips, appreciate it.

---

### Post by dandnsmith on 2009-11-08
Happy to hear that the grub boot works.

For the password, you could change it using a live CD - look up info on the passwd command, and possibly use something like vipwd (my knowledge may be somewhat dated here, and different tools recommended).

---

### Post by duanedesign on 2010-01-02
Guide to creating a Llive USB:
[http://ubuntuforums.org/showthread.php?t=1193680](http://ubuntuforums.org/showthread.php?t=1193680)

**Known Issues**
The 9.10 CDs and DVDs are [COLOR="Red"]missing the usb-creator.exe program[/COLOR]. To install to a flash drive from a disk image on Windows, use the incredibly easy process described at:
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) 
-
-
-

---

