---
title: "very slow disk speed, seems like PIO mode but hdparm cant read drive...."
date: 2008-09-22
forum: General Help
---

### Post by syadnom on 2008-09-22
info: 
8.04 desktop
1.66Ghz Core Duo, 2GB RAM, Dell e1505(same as 6400)
kernel= 2.6.24-19-generic


I am having a TERRIBLY slow system whenever I do any kind of I/O.  I tried to look and see if DMA was on but when I run 'hdparm /dev/sda' i get the following:

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 4681/255/63, sectors = 75200265, start = 0

I googled each of the HDIO errors but google has no knowledge of any of these.

I checked the known issues in hardy but this is not on the list.

anyone every seen this?  I dont remember having this problem until recently but I was not doing much I/O on the primary disk but to an external USB.  Seems like maybe a recent kernel update caused this.

any help would be very appreciated.

thanks

---

### Post by BrownieMan on 2008-12-02
exact same problem here. It seems to be rampant with Hardy

---

### Post by syadnom on 2008-12-02
Its not just hardy, I have the same issue with Fedora9 and debian etch.  Fedora10 and Ubuntu 8.10 both have resolved the issue.  

Seems to be some bugs from the switch in ide drivers or something..

---

### Post by BrownieMan on 2008-12-03
> **syadnom said:**
> Its not just hardy, I have the same issue with Fedora9 and debian etch.  Fedora10 and Ubuntu 8.10 both have resolved the issue.  

Seems to be some bugs from the switch in ide drivers or something..

So if I upgrade from 8.04 to 8.10 this is all solved?!?!?!

---

### Post by syadnom on 2008-12-03
I didnt upgrade, I did a fresh install, but that did fix it for me on my inspiron e1505

---

