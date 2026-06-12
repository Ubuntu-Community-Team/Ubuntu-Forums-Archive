---
title: "Ubuntu 5.04 + VMWare 5.0 = No Partionable Media"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by wiseleyb on 2005-04-22
I'm running VMWare 5.0 on WinXP Pro with a 20GB initial drive for the Unbuntu install.  I burned the Ubuntu ISO (5.04) to a CD and started the VMWare image.  Install runs fine until it get's to the Partion stage at which point I get a "No Partionable Media".   I'm using auto boot on the CD (so when VMWare image starts it auto boots from the CD).

Complete Linux novice.  Any suggestions?  I searched through the posts but it seems everyone else is using VMWare 4.5

---

### Post by philipacamaniac on 2005-04-22
I'm using 5. Did you:

Choose "Other Linux 2.6.x kernel" for your guest OS?

Allocate disk space (the step that takes a while)?


Also, did you know you can set the ISO as your CD drive, so you don't even need the CDROM?

---

### Post by mrtaber on 2005-04-22
I ran into this.  In the VM Ware virtual machine creation, don't choose 'Typical', choose 'Expert'...don't be alarmed.  When you get to the section where you create your virtual hard drive, choose 'IDE' rather than 'SCSI' (even though SCSI is the recommended choice).  I was able to install after that.

Hope this works for you,
Mark Taber :)

---

### Post by philipacamaniac on 2005-04-22
Mine is working great with the SCSI option. mrtaber, did you have to allocate disk space for it to work? I have a feeling that may be the problem.

---

### Post by mrtaber on 2005-04-22
You know, now that you mention it, I *did* have to allocate disk space!

:)

Thanks,
Mark

---

### Post by wiseleyb on 2005-04-22
Thanks for the help!  I did pre-create a 20GB ... but it was SCSI.  Went back and switched to IDE and, so far, so good.

---

