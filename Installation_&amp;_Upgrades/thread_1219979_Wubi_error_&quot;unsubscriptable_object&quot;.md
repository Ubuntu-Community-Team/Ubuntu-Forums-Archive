---
title: "Wubi error &quot;unsubscriptable object&quot;"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Theory5 on 2009-07-22
Hey, I recently partitioned my laptop so I could dual-boot Ubuntu and vista on it(Vista is already on it). It has been having some difficulty installing, so I downloaded Unetbootin and ran it on my second HDD partition. The only problem is that when I boot my computer the BIOS only sees the harddrive and boots from the first partition, not the second one. So in windows I ran the wubi application and tried to install the boot helper. After 2 hours or so it finally stopped right at the end to give me the error "unsubscriptable object". Is there a way around this? Could I install another bootloader so I can see and boot from the second partition? please help.
And can ubuntu use the NTFS file system? Cause thats what I have formatted the second partition as so I could put the Ubuntu installation there.

---

### Post by Mark Phelps on 2009-07-22
> **Theory5 said:**
> ... 
And can ubuntu use the NTFS file system? Cause thats what I have formatted the second partition as so I could put the Ubuntu installation there.

NO.  Ubuntu needs to be installed using Ext3 or Ext4.  Wubi installs don't care because they really create a file on an existing partition that serves as an installation.

---

