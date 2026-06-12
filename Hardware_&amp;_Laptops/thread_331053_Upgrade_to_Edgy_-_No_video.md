---
title: "Upgrade to Edgy - No video"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by mlissner on 2007-01-04
Hello all, I just upgraded to edgy from dapper, and I've lost video on my laptop. The video driver says this about itself:

VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller

I had it working in dapper by installing the 915resolution package, but that's not doing it now (it's still installed).  

When I boot up, xserver essentially just fails. I get a blank screen, and as soon as I touch a button, it tells me that it has failed, I get blue gibberish, and that's about that. I don't know where the error log must reside, but in tty1 (which more or less works fine), I do get some strange errors every now and again:

[17179831.028000] ata2 failed to respond (30 sec)
[17179831.036000] ata2: command 0xa0 timeout, stat 0xd1 host_stat 0x0
[17179831.040000] ata2:translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00

The other strange thing I noticed is that if I hit sudo apt-get upgrade, it lists 40 packages that have been "kept back", including, perhaps notably, xserver-xorg-input-elographics, xserver-xorg-input-mouse, xserver-xorg-evdev, xsever-input-kbd, xsever-xorg-input-synaptics. For some reason, rather than installing these, it skips them. I don't know how to force them to install, but perhaps that would help? 

Anybody have any ideas on this? I'd love not to lose this computer at this point...all I wanted was some better hardware support, and this is what I got...sigh...

Thanks to all in advance.

---

### Post by mlissner on 2007-01-04
OK. Made some progress. I found a thread that suggested that I do sudo apt-get install --reinstall xserver-xorg. Worked to some degree.

However, though my system is now booting into edgy, and hardware seems to actually work better than before, one problem I am still having is that everything seems to freeze every now and again at random. I haven't been able to figure out exactly what's causing this, but I am still getting those three display errors from before if I watch on tty1. 

Any ideas on what to do about these?

Please? I'm hurting to get my computer running smoothly...

---

