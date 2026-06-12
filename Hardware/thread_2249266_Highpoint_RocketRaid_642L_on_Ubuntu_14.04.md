---
title: "Highpoint RocketRaid 642L on Ubuntu 14.04?"
date: 2014-10-20
forum: Hardware
---

### Post by bbruecker on 2014-10-20
Hi,

Anyone her with a RocketRaid 64x card running a recent Ubuntu? I don't need to boot from the card. I only would like to use it for a data Raid 0 partition.

The adapter seems to to be very fast  -- I tested it with Hackintosh.  A pair of WD Black Edition disks where performing better tests then my SSD.

Unfortunately its quite painful to install the driver on Ubuntu. I tried this:


[LIST=1]
[*]installing the driver HighPoint ships from their website using a simple install.sh for Ubuntu 12.10 x86_64. Result is: the system is rebooting, but only diplaying my disks, not the Raid 0 partition.
[*]The open source driver HighPoint is offering fails during install.
[*]The description on [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid) is not working with the files, event the liked ones, because they are now slightly different, from the that what the author wanted to change. Maybe this is the reason, anyway the result is the build fails.
[*]HighPoint support offered me another version of the open source driver, its possible to build it, but now Ubuntu doesn't boot any more! In the syslog the driver failed to perform port hard reset. The driver is doing that endless again and again and again... In recovery mode card is beeping! Now it seems to me, I have to face the fact I have to reinstall Ubuntu.
[/LIST]

Any ideas? If you need further informations, I will post it.

Thx, Benjamin

---

### Post by WinEunuchs2Unix on 2014-10-20
And I thought I had trials and tribulations with Intel Rapid Storage Technology (RST) and it's Smart Response Technology (SRT) read caching setup on this laptop.  I did a quick google and found this:

[TABLE="width: 860"]
[TR]
[TD="class: text11, align: center"][LEFT]Supported Linux Kernel version[/LEFT]
[/TD]
[TD="class: text11, align: center"]Up to Kernel v3.8.4[/TD]
[/TR]
[/TABLE]

The link you gave was for older Ubuntu versions and perhaps it worked perfectly then.

One thing I've discovered this last month is that when it comes to RAID 99% of the googles ARE NOT applicable to the current platform.

Sorry I couldn't help out more but I "empathize" with you.

---

