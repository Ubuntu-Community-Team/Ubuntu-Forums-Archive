---
title: "Intel RST(Rapid Storage Technology) RAID on Lenovo Flex 5"
date: 2017-12-08
forum: Hardware
---

### Post by ohernandez3 on 2017-12-08
I just bought a new laptop and the first thing I did was nuke the drives to run straight Linux. It is a Lenovo Flex 5 with a 256GB nvme drive and a 1TB sata drive. Most everything works except for two things the hdmi sound and Intel RST. If Intel Premium RST is enabled in BIOS I can not see the hard drives in Ubuntu 16.04.3LTS, but I can see the hard drives in AHCI mode. I tried running "mdadm --assemble --scan" it can not detect any raid configuration, and "lsblk" and "blkid" does not list the hard drives. Surprisingly though if I use Ubuntu 17.10 I can see the sata drive, but it does not list my nvme drive. What am I missing to be able to run the Intel RST, anyone?

---

### Post by oldfred on 2017-12-08
Not sure what Intel RST is offering.
It was used on early Windows 8 systems as Microsoft required vendors to speed up boot. But Windows boots slow, so they added a tiny 16 to 32GB SSD on motherboard and used Intel RST to run the start up cache. It only used the amount of RAM, so some with larger 32GB SSD also put Ubuntu's / (root) on the SSD. 

But you have a large SSD. And do not have a real RAID configuration with multiple identical drives. So it may just be the start up cache, which if dual booting you should not be using anyway.

[https://www.intel.com/content/www/us/en/support/articles/000005610/technologies.html](https://www.intel.com/content/www/us/en/support/articles/000005610/technologies.html)
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

You may have RAID meta-data on drive. And you may need to update firmware from vendor on SSD.
      
 Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)

---

