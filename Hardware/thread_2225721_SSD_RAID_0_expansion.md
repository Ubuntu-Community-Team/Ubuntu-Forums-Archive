---
title: "SSD RAID 0 expansion"
date: 2014-05-22
forum: Hardware
---

### Post by stevie6 on 2014-05-22
I built my new machine & gave it a SSD main drive. So of course I need more space.  Ubuntu, to the best of my knowledge (please correct me if I'm wrong), doesn't like to install/parse to other drives. My idea is to install my important stuff to near full on the SSD and then install a 1-2 TB HDD set to RAID 0 with the SSD to make it all seamless. Has anyone tried this? 


Also anyone who could point to good (read: SIMPLE) RAID setup would be cool too.

---

### Post by oldfred on 2014-05-22
I am not a fan of RAID, and mixing SSD & hard drive sounds like issues.

Not sure what you mean by install to other drives. My SSD is sdd, my data partitions are on sdc, my backup partition is on sda (along with a now unused XP) and my ISO files are on sdb which I can boot from grub in stalled in any drive, but each grub boots a different install, most in sdc.
But you need to understand partitions, what partitions you want and then use something else and install manually. I normally partition in advance with gparted.

       [URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup
      [/URL]
 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

 Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]

[/URL]

---

