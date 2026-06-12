---
title: "Does Ubuntu Server/Desktop support IBM server xSeries 3850 x6"
date: 2015-10-12
forum: Hardware
---

### Post by Goor_S on 2015-10-12
Hi,

I'm in a process of purchasing a new server for the lab I'm working in.
I want it to be installed with Ubuntu afterwords.
I want to know whether the above server would be supported by Ubuntu's current and later versions
(specific server model (6241)).

Thanks,
Goor

---

### Post by SeijiSensei on 2015-10-12
That's a hefty piece of hardware!

It looks pretty vanilla, but it might depend on what you use for the disk interface.  Most SAS RAID cards are well-supported, and it looks like that server uses one of them.

I exclusively use [CentOS]("http://www.centos.org/") on servers because server manufacturers make sure their hardware works with RedHat Enterprise Linux from which CentOS is cloned.  If Ubuntu doesn't work out for you, I'd try CentOS.

I prefer Ubuntu on the desktop though.

---

