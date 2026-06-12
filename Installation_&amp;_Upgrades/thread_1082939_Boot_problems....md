---
title: "Boot problems..."
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by gshappell on 2009-02-28
First I'll explain what I did in case I did something wrong.  

I have 2 physical disks, vista is on disk1 and disk2 is just an extra disk for files.  

So I created a partition with gparted from the livecd on disk2 since I have more room on that disk.  I went through the install without any errors.  However, now that I boot...i dont get a boot menu and it goes straight to vista.  Is that because it was installed to disk2?  Is this setup possible?  Can I install grub from livecd to point to the other disk?

Thanks

---

### Post by ekidd91 on 2009-02-28
Should be a simple fix.

Restart your computer > press F2 repeatedly until you come to a system menu > Go to the Boot tab/section > Go down to Boot devices > Change it so that the disk that Ubuntu is on is the first place your computer checks to boot from.

That should be it, perhaps I haven't explained it 100% correctly though... someone else might offer a more detailed solution.

---

### Post by gshappell on 2009-02-28
Thanks for the response!! That worked.  Sorry for the delay, been working on my friends dell all day long...ugh.  Anyway thx for the quick response.

---

