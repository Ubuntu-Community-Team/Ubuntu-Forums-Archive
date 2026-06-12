---
title: "New server install with hardware RAID"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by johnstonc on 2009-10-09
Hello all,

I am a complete Linux newbie, and I am trying to install Ubuntu 9.04 on an old HP Proliant ML350 G3, with 2GB RAM, and six 36.4GB SCSI hard drives installed.  The server has an Adaptec SCSI RAID controller (not sure right off had which model) installed and I have used the HP SmartStart CD to create my arrays/logical drives.  The first array is two drives RAID 1 (mirrored), the other arrays (4 in all) are single RAID 0.  I want to install Ubuntu (most preferably the GUI version because of my lack of knowledge) and FOG onto the RAID 1 set, and use the other drives for storage of the FOG images from different campuses in my school district.

The problem I have is, after I boot the Ubuntu CD and start the installation, I get through the language, time zone, and keyboard settings, then the Partioner comes up.  However, when it loads no partions/drives show up in the list ](*,), so I am stuck at this point.  I know it is something I am not doing right, but that is as much as I know.  It seems everything I find on RAID and Ubuntu concerns FakeRAID or software RAID and not a whole lot on hardware RAID.  I am using this server, because it is left over from years past (i.e. - free/no spending) and I don't want to pay money I don't have for something I really don't need to function.

I really do want to get this server going, with the GUI version of Ubuntu so I can run FOG and save myself lots of time and grief in the end.  If you have any suggestions, comments, or advice I am more than willing to accept.  If any more information is needed, please let me know and I will do my best to provide it.

Thanks,

Chris

---

### Post by johnstonc on 2009-10-09
Hello,

Sorry, I got the RAID controller wrong in my previous post.  It is not Adaptec, but instead an HP Smart Array 641 Controller.

Thanks again,

Chris

---

