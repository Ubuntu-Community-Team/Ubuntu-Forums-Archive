---
title: "HP Smart Array E200 RAID controller: compatible with Ubuntu 8.04?"
date: 2008-06-06
forum: Hardware
---

### Post by titao70 on 2008-06-06
Hi,
we have an HP Proliant DL320 G5 Server on which we would like to install a HP Smart Array E200 controller ([http://h18004.www1.hp.com/products/servers/proliantstorage/arraycontrollers/smartarraye200/](http://h18004.www1.hp.com/products/servers/proliantstorage/arraycontrollers/smartarraye200/)).
Does anybody know if this RAID controller is recognized by Ubuntu Server 8.04?

Thanks!

---

### Post by b.haver@encaps.nl on 2008-08-12
We have Ubuntu 8.04 installed on a HP DL320 Server with HP E200 controller and 4 x SATA 500 GB drives. Works fine, no extra drivers needed. We are now looking for a tool to monitor the raid array.

---

### Post by ahansen on 2008-09-08
I've got a Prolaint ML350 G5 with the e200 array controller and have an open ticket right now re very slow performance.  I'm seeing peaks of 3400 % write time from the Windows VM side.  I just posted back to support asking if there is a way to monitor the local disk performance from within Ubuntu to isolate the problem to either the hardware, OS or VMware.  Good luck - approach with caution.

---

### Post by ahansen on 2008-09-08
Avoid the e200.  See the link below.  I'm looking at the Adaptec 3805 as a potential replacement.

[http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1220903522617+28353475&threadId=1178606](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1220903522617+28353475&threadId=1178606)

Not good...

---

### Post by damaan on 2008-11-03
Could anyone tell me if the E200 is a "real" RAID controller (as opposed to a fake RAID)?

I tried creating a RAID 1 volume using the E200 BIOS disk management tool. All seemed to go well, the array build completed successfully. Then I ran the Ubuntu installation but it showed **two** disks when I was expecting one. From what I read in other places, this is an indication that the raid controller is fake and needs special drivers to work properly. Can someone confirm this?

---

