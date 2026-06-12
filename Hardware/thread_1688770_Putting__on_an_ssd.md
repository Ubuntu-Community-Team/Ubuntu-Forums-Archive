---
title: "Putting / on an ssd"
date: 2011-02-15
forum: Hardware
---

### Post by b0b138 on 2011-02-15
Would there be an advantage of having / on an ssd while /home is on a normal disk?

Has anyone used one of these? [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100008120%20600038515&IsNodeId=1&name=PCI%20Express](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100008120%20600038515&IsNodeId=1&name=PCI%20Express)

---

### Post by psusi on 2011-02-15
The advantage of SSDs is, of course, speed of booting and launching programs and such.

---

### Post by b0b138 on 2011-02-17
Right,  but is having /home on a normal disk going to defeat the purpose of having / on the ssd? Or is the amount of information in config files that are in your home directory not enough to to really matter?

---

### Post by psusi on 2011-02-17
> **b0b138 said:**
> Right,  but is having /home on a normal disk going to defeat the purpose of having / on the ssd? Or is the amount of information in config files that are in your home directory not enough to to really matter?

Config files are very small.  It will, of course, mean that opening large documents in your home directory won't be as fast though.

---

### Post by fjgaude on 2011-02-17
> **psusi said:**
> Config files are very small.  It will, of course, mean that opening large documents in your home directory won't be as fast though.

Say, what would be the best way to install an OS on a clean drive with /, /boot, and /home directories or partitions?

---

### Post by paulisdead on 2011-02-17
I tried that myself, with / on an SSD, and using a 1tb hdd for /home, and noticed a nice little speedup when I moved /home to the ssd, and just symlinked the few bigger folders to the hdd.  I've got a 40gb Intel that I'm only using 11GBs with /home on it including my email.  It's just the bigger stuff like images, and scratch space to encode video and audio I needed the hdd for.  All those config files might be small, but they're scattered, so there's a lot of seek time involved loading them up.

I've never tried one of those revodrives before, but I think they just show up as a silicon image raid card.  I'm sure if you google around you can find something on linux use with those.

---

### Post by psusi on 2011-02-17
> **fjgaude said:**
> Say, what would be the best way to install an OS on a clean drive with /, /boot, and /home directories or partitions?

What do you mean?  You probably don't have a reason to have a separate /boot partition, and for that matter, I don't recommend a separate /home unless you want to share one /home between multiple Linux installs.

---

### Post by psusi on 2011-02-17
> **paulisdead said:**
> 
I've never tried one of those revodrives before, but I think they just show up as a silicon image raid card.  I'm sure if you google around you can find something on linux use with those.

Yep, that's why I think they are dumb.  Rather than just put the flash on the card so you can access it directly and preferably format it with a filesystem optimized for flash, they put the flash behind multiple chips that emulate a sata disk, which sits behind a multi port sata controller, which comes with software to do fake raid.  :rolleyes:

Of course, the reason they do this is because the evil Microsoft OS does not have a flash filesystem, and they would have to write drivers.

---

### Post by paulisdead on 2011-02-17
> **psusi said:**
> What do you mean?  You probably don't have a reason to have a separate /boot partition, and for that matter, I don't recommend a separate /home unless you want to share one /home between multiple Linux installs.

Actually you might want to create /boot on a separate partition, so that you can make sure the / partition is properly aligned [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/) this comes from the lead ext4 dev.

There's also a great reason to keep /home on another partition.  If it fills up, it doesn't impact the rest of the system.  Not quite as important or as likely on a desktop as on a server, if you're paying attention, but it can happen.  You can also reinstall without formatting /home.

---

### Post by psusi on 2011-02-17
> **paulisdead said:**
> Actually you might want to create /boot on a separate partition, so that you can make sure the / partition is properly aligned 

Having a separate /boot partition does not help with that at all.  Modern partitioning tools take care of alignment for you anyhow.

> **paulisdead said:**
> There's also a great reason to keep /home on another partition.  If it fills up, it doesn't impact the rest of the system.  Not quite as important or as likely on a desktop as on a server, if you're paying attention, but it can happen.

The corollary to this is that you can run out of space for your files in your home directory even though there is plenty of free space in the root.  Or vice versa.

> **paulisdead said:**
> You can also reinstall without formatting /home.

You can do that just fine without a separate /home.

---

### Post by fjgaude on 2011-02-18
> **psusi said:**
> What do you mean?  You probably don't have a reason to have a separate /boot partition, and for that matter, I don't recommend a separate /home unless you want to share one /home between multiple Linux installs.

That's it, I wish to share multiple installs with on /home. What's the best way to do that, with Alternate CD?

---

### Post by psusi on 2011-02-18
> **fjgaude said:**
> That's it, I wish to share multiple installs with on /home. What's the best way to do that, with Alternate CD?

You can use either cd you want.  Just use manual partitioning and assign /home to the right partition, and make sure not to check the format box.

---

### Post by fjgaude on 2011-02-18
> **psusi said:**
> You can use either cd you want.  Just use manual partitioning and assign /home to the right partition, and make sure not to check the format box.

Thanks, it's seems logical, yes! Why didn't I think of that? <smile>

---

