---
title: "What does the sbp2 module do?"
date: 2008-11-07
forum: General Help
---

### Post by alhead on 2008-11-07
Does the sbp2 module affect anything other than FireWire, i.LINK, and Lynx?  I don't have any firewire ports on my computer, and I don't use my i.LINK port.  Would it be ok to comment out the sbp2 line in /etc/modules?

---

### Post by wootah on 2008-12-21
I'm curious about this too.

For firewire, it appears you need to also blacklist ieee1394 and ohci1394.

EDIT: Those modules effectively disable firewire--sbp2 controls the hotplugging of firewire devices by providing a low level SCSI tunnel. See [http://www.linux1394.org/sbp2.php](http://www.linux1394.org/sbp2.php) . Hopefully this will help someone :)

---

### Post by kerry_s on 2008-12-21
> **alhead said:**
> Does the sbp2 module affect anything other than FireWire, i.LINK, and Lynx?  I don't have any firewire ports on my computer, and I don't use my i.LINK port.  Would it be ok to comment out the sbp2 line in /etc/modules?

yes, you can comment it out.

---

