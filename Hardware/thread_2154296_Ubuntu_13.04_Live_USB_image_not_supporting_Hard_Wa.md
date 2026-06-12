---
title: "Ubuntu 13.04 Live USB image not supporting Hard Ware RAID 10 Hard disk"
date: 2013-06-14
forum: Hardware
---

### Post by g_ramesh on 2013-06-14
After booting off Ubuntu 13.04 Live USB image, it is not detecting Hard Ware RAID 10 Hard disk. The PCI based  FastTrak TX4660 HBA is used for RAID. Why it is not detecting the Hard Disk?

---

### Post by Cheesemill on 2013-06-14
Because Promise don't write Ubuntu drivers for that particular card.

---

### Post by g_ramesh on 2013-06-14
> **Cheesemill said:**
> Because Promise don't write Ubuntu drivers for that particular card.

Thanks for the reply. Not only Ubuntu I tried with Debian 7, Gparted (Latest release), none of them are detecting the harddrive. Is there any work around?

---

### Post by Cheesemill on 2013-06-14
The only Linux drivers available for download on the Promise website are for Red Hat and Suse but these are 7 years old.

I don't think you'll be able to use that RAID card on any modern Linux distro.

---

### Post by g_ramesh on 2013-06-15
> **Cheesemill said:**
> The only Linux drivers available for download on the Promise website are for Red Hat and Suse but these are 7 years old.

I don't think you'll be able to use that RAID card on any modern Linux distro.

Thanks again for your reply and time. will try to contact Promise for latest drivers.

---

