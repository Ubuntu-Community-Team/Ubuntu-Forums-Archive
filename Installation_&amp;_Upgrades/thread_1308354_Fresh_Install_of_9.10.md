---
title: "Fresh Install of 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by CSHANKY on 2009-10-31
I have 9.10 installed and it's FUBAR due to my tinkering. So, I'd like to:

1. Format my HD
2. Install a FRESH / CLEAN Ubuntu 9.10

I have the 9.10 CD burnt and my my files are all backed-up. 

Can someone tell me how go about it? 

Please don't advise me for an upgrade - been there / done that.

All I want to do is: Format - install 9.10

Thanks !

---

### Post by bulldog on 2009-10-31
Create the partitions you need.

10GB for /
2GB  for /swap
xxxGB for /home

When the installer comes to the partition part,choose manual!!
Select the 10GB partition and set it to use as ext3 or ext4 if you want,mount point would be /
Select the 2GB and see if it's mounted as it should be (mostly you don't need to do anything here)
Select the xxxGB partition,set it to use as ext3 or ext4,mountpoint /home.
Proceed with the install.

---

### Post by CSHANKY on 2009-11-01
I am a newbie...could you please elaborate a little on the steps? I don't know how to set-up partitions.

Step-by-step guide would be very helpful.

Thanks

---

### Post by cAlpha on 2009-11-01
Not sure whether you're currently working within Ubuntu or some Windows variant, but [this]("http://www.bing.com/search?q=how+to+create+partitions&go=&form=QBRE&qs=n") would probably be a good start.

---

