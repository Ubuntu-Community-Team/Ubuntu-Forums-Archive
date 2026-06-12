---
title: "installing other distros"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by porter on 2005-11-11
i am trying to install another distro on an existing blank partition. i've installed ubuntu5.10 and i want to keep it as my base system. when i try to install another distro i get "no partitions found". running cfdisk i get a "read-only" permissions error and that's it. i created the 15gb partition just for installing another distro when i first installed ubuntu and now i can't get to it... what do i need to do to get the partition 'free' so that another distro will recognize it?

thanks.

---

### Post by taurus on 2005-11-11
Which distro are you having in mind?  I have both ubuntu and suse running on my laptop with only one harddrive so there shouldn't be a problem installing two distros on a same machine...

---

### Post by ibanez88 on 2005-11-11
Do you get the same results using several different distros?

In the other distro's partition tool (fdisk?) you should be able to see all of your partitions, select the empty one, and hit C to create your new linux filesystem on that.

I have FreeBSD on another partition/slice but I'm pretty sure Linux works the same way.

---

### Post by porter on 2005-11-11
i was trying to install zenwalk 1.3. i would also like to try pcbsd when 1.0 comes out. 

zenwalk's cfdisk and fdisk say that i do not have permissions to view the drives. i have already formated the partition as ext3 when i installed ubuntu.

---

### Post by porter on 2005-11-19
no go with vector 5.1 either. i get the same "no hd" error.

anyone?

---

### Post by taurus on 2005-11-19
Is that an EIDE or SATA???

---

### Post by porter on 2005-11-19
sata

---

