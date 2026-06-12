---
title: "Changing OS's"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Free Thinker on 2009-04-23
Do problems arise when you change OS's too much?

I've gone from Vista => Windows 7 beta => Ubuntu 8.04 => Ubuntu 8.10 => Linux Mint => Ubuntu 8.10 => Soon to be Ubuntu 9.04
All on the same laptop.

Also, is any data kept from previous installations or is it completely removed?

---

### Post by Menschenfresser on 2009-04-23
the only thing would be that the hard disk is used more during the installation, but don't worry about that. And about remaining data, if you format the disk/partition when you install, then it's gone, else the data is kept.

---

### Post by drs305 on 2009-04-23
> **Free Thinker said:**
> Do problems arise when you change OS's too much?

I've gone from Vista => Windows 7 beta => Ubuntu 8.04 => Ubuntu 8.10 => Linux Mint => Ubuntu 8.10 => Soon to be Ubuntu 9.04
All on the same laptop.

Also, is any data kept from previous installations or is it completely removed?

No, to the first question,

If you do the upgrade via online updates your current data and settings are retained. If you do a clean install from a CD your configuration settings, which are stored in your /home/username folder are overwritten. You can preserve your user settings with a clean install if you have a separate /home partition. To do this, you would identify the /home partition during the partitioning portion of the install and make sure NOT to format it. 

There are several HOWTOs for creating a separate /home partition, including this one:
[_http://www.psychocats.net/ubuntu/separatehome_]("http://www.psychocats.net/ubuntu/separatehome")

---

