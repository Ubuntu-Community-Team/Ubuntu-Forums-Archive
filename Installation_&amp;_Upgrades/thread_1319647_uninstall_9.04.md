---
title: "uninstall 9.04"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by cowboy7305 on 2009-11-08
I have ubuntu 9.04 on my computer and also 9.1,both on same disk ,how do i uninstall 9.04 and leave 9.1 to use all of my disk 
many thanks

---

### Post by raymondh on 2009-11-08
> **cowboy7305 said:**
> I have ubuntu 9.04 on my computer and also 9.1,both on same disk ,how do i uninstall 9.04 and leave 9.1 to use all of my disk 
many thanks

You could use the liveCD and access gparted to delete the unwanted version and then extend the 9.10 partition/s to take up the empty space.  From there, you'll need to edit GRUB2 to take out the 9.04 headers.  Unfortunately, I have not played around with GRUB2 that much to provide any guidance on manual editing.

Another option is to re-do your install of 9.10 and select "use entire disk" in the partitioning stage of ubiquity.  That will also automatically re-configure GRUB2 for you.

Either way, pls. have a working back-up of your files.

Regards,

---

