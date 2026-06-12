---
title: "sata hotplug scsiadd no longer working"
date: 2012-03-28
forum: Hardware
---

### Post by alenis on 2012-03-28
Scsiadd doens't work anymore with the latest debian and ubuntu releases. I used to use it a lot, because it allowed to add in a very simple way sata disks without restarting the system .I just put the disk in the hot-plug capable drawer, then 
```

scsiadd -a x y z 
```

and the disk was ready to be mounted. 

I have been looking for a replacement for several months without success. Somebody suggested scsitools but I couldn't figure out how to use it.

Then I found 

```
"The functionality to add a device is supported via
/sys/class/scsi_host/hostA/scan. Removing devices goes via
/sys/block/sda/device/delete or
/sys/class/scsi_disk/A:B:C:D/device/delete."
```

[here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522542")

but the poster, unfortunately, didn't give any information on how to use those files which, in addition, look non writable even to the root user.

Is there anybody, please, who can provide me and, I guess, other scsiadd orphans, with clear directions?

Thanks
Alessandro

---

### Post by MikeMiller on 2012-05-15
I second that.  Running 12.04 LTS and really need Linux to autodetect and automount when I put a 2.5" SATA Drive in my X-Dock...

Anyone?

---

### Post by antiplex on 2012-09-12
as far as i remember scsiadd was removed from the ubuntu repos since natty since it used some deprecated calls.
the closest thing being still maintained and available through the official ubuntu repos seems to be [FONT="Courier New"]**scsi-spin**[/FONT] contained in the package [FONT="Courier New"]**scsitools**[/FONT].
havent used it for some time but i remember being able to spin down my sata drives with that.

hope that helps, any other ideas so far?

---

