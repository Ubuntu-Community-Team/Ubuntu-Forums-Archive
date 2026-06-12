---
title: "How to retain desktop during upgrade"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by benali72 on 2009-09-28
I'm upgrading from 8.04 to 9.04.

I'll do this by installing 9.04 into a new partition.

My question is: if I then simply copy over my /home directory from the 8.04 install to the new 9.04 install, will that retain all Toolbar Panel and Desktop applications?

Thank you.

BTW my apologies if this has been asked before but I was having trouble digging it out of existing threads.

---

### Post by lyall on 2009-09-28
See the following link from psychocats
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
then go to Beyond the Basics
click on Upgrade Ubuntu*
or go to the following link
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

Please check out psychocats web site a lot of answers and help is there
It is a GREAT web site

good luck and have fun learning

---

### Post by slakkie on 2009-09-29
Yes. But the better option would be to create a seperate partition for your homedir, so then you only need to mount your homedir, via fstab on both installs. Which is way easier iyam.


You put something like this in both 8.04 and 9.04's /etc/fstab:
```

# /dev/sda6
#UUID=16a38a99-6e21-462c-939d-2716412d8701 /home           ext3    relatime,errors=remount-ro 0       2
/dev/sda6 /home           ext3    relatime,errors=remount-ro 0       2

```

---

### Post by benali72 on 2009-09-29
Thank you both for the info.  With your help I've got a handle on it now.

---

