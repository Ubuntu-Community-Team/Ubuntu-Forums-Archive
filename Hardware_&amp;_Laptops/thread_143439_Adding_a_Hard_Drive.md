---
title: "Adding a Hard Drive"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by souteneur3190 on 2006-03-12
I just bought a 200GB Maxtor HD off of ebay.  It should get it by Wednesday.  I remeber a friend that had problems running Ubuntu with 2 HD's.  Is there some way I need to configure it first?  I have a 20GB that has the ubuntu on it.  I just want one big partion for my HD so I can fit all my movies in it.

---

### Post by taurus on 2006-03-12
Not sure what your friend did but I have two HDs on my machine and didn't have any problem whatsoever with Ubuntu.  I assume you want to keep Ubuntu on the first HD and install your second one as a slave to store all your personal stuff then.  Just format it as ext3 and mount it...
```

sudo mke2fs -j /dev/hdb1

```
Then, create a mount point and edit your /etc/fstab to have it mount automatically upon boot.
```

sudo mkdir /data
sudo gedit /etc/fstab

/dev/hdb1  /data  ext3  defaults,umask=0000  0  0

```

---

### Post by fizwigit on 2006-03-14
hey I tryed the about post to add a partition instead of an actual hard drive but I get the 'bad option' error message I doesn't seem to recognize 'umask=0000'

---

