---
title: "Hardisk Clone"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by Ajat on 2009-08-14
hi, here is my problem,
i'm planning to have new laptop, but my old laptop has non-fresh kubuntu installation (I don't want to re-do thousand of 'apt-get' again) .. 
I want to move my kubuntu installation to my new Hardisk, that is to completely clone my hardisk (i also have vista partition here) ..   i heard about [clonezilla.]("http://www.clonezilla.org/")
and will there some hardware issue on my new system?

or is there any other way to do this?

---

### Post by starcraft.man on 2009-08-15
Clonezilla is perfectly suited to this, this is what drive imaging lives for! Just make a drive image of your current set up to a file. Then recreate a similar partition structure on new machine (the partitions need to be at least as large as original). Use gparted of course for partitioning. Then restore to those partitions as desired. You'll have to have access to the image file, pretty sure clonezilla works with samba if you've no simple external storage to use.

Once restored, you can alter the paritions to your hearts desire and then boot up. I'm pretty sure should work fine what with xorg autodetecting everything now. If your changing graphics cards (nvidia to ati or intel) be sure to disable that. If there's any trouble, I'm sure can diagnose after.

Don't have a guide for clonezilla, program is pretty easy to use. Just be sure ya understand absolute paths and where your data is and what partitions ya want to backup where. It's possible but unlikely that you'll mess anything up, just read each page carefully and fill in as needed. If you've any serious questions and want to abort, just escape at any point BEFORE the final ask to write to the drive.

---

