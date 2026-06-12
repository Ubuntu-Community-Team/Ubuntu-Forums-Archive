---
title: "Ubuntu 9.04 cannot mount Ubuntu Desktop Remix 9.04's iso"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Giacecco on 2009-06-26
All,
I have a 9.04 running fine in a VMWare Fusion virtual machine. 

In the past I used this and the 9.04 image to create 9.04 bootable USB keys without any issues. 

Today I downloaded the 9.04 Notebook Remix iso to do the same... but I cannot even mount the iso! I get a 'Invalid mount option when attempting to mount the volume' error!

I imagined that the iso was corrupted and downloaded it again from a different source... but I got the same error.

Interestingly enough, MacOS can mount the iso, whose only oddity is a 'untitled' label.

Any ideas?

Giacecco

---

### Post by kilowattradio on 2009-06-26
> **Giacecco said:**
> All,
I have a 9.04 running fine in a VMWare Fusion virtual machine. 

In the past I used this and the 9.04 image to create 9.04 bootable USB keys without any issues. 

Today I downloaded the 9.04 Notebook Remix iso to do the same... but I cannot even mount the iso! I get a 'Invalid mount option when attempting to mount the volume' error!

I imagined that the iso was corrupted and downloaded it again from a different source... but I got the same error.

Interestingly enough, MacOS can mount the iso, whose only oddity is a 'untitled' label.

Any ideas?

Giacecco

Did you check the intergrity of the file you downloaded? 
You should get the md5 or sha1 or sha256 sum from the download site and check it.  
If you have a md5sum:
**md5sum FILENAME.iso**
You can also check the sum in Mac OS X in the terminal. 
If everything is fine with the sum then you may be using the wrong command line parameters or if this is a Windows program the program may have a bug. Try winRAR from [http://www.rarlabs.com/](http://www.rarlabs.com/) to mount the ISO in windows. 

:KS

---

### Post by Giacecco on 2009-06-27
Thank you for your response kilowattradio . The MD5 is fine!

I am trying mounting the iso from Ubuntu 9.04 itself. I tried both ArchiveMounter and usb-creator. The former simply does not do anything. The latter says that it is unable to mount the image. 

If I look into dmesg I find: 

ISOFS: Unable to identify CD-ROM format.


G.

---

### Post by kilowattradio on 2009-06-27
> **Giacecco said:**
> Thank you for your response kilowattradio . The MD5 is fine!

I am trying mounting the iso from Ubuntu 9.04 itself. I tried both ArchiveMounter and usb-creator. The former simply does not do anything. The latter says that it is unable to mount the image. 

If I look into dmesg I find: 

ISOFS: Unable to identify CD-ROM format.


G.

[http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html")

You should check the above link for instructions on how to mount an ISO in Linux. If you are doing it properly the only thing I can think of is that the kernel does not have support for ISO9660?? Sorry I can't help you more.

---

### Post by Giacecco on 2009-06-27
All fixed. I have RTFM and realised that the image I downloaded was not supposed to be a CDROM, but a USB key! I should have never tried to mount it as such, and rather than usb-creator I should have used usb-imagewriter!

Thank you for all your help,

Giacecco

---

