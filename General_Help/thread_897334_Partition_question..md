---
title: "Partition question."
date: 2008-08-22
forum: General Help
---

### Post by shamusl on 2008-08-22
I have 3 partitions on my drive, 1 for ubuntu (EXT3), one for swap, and one for windows vista (NTFS). After months of using ubuntu, I've decided I want to destroy the windows partition and just make the ubuntu partition the whole drive (other than swap). Anybody got a command for this?

---

### Post by erfahren on 2008-08-22
you can boot up with the LiveCD and use GParted - just open the terminal and launch it with "gksu gparted"

delete the Windows partition and resize the Ubuntu one

if the swap is between the two you'll have to delete it as well and re-create it of course - if you do that you'll also want to check your /etc/fstab file afterwards to make sure the correct UUID is listed for it - example:
```

# Entry for /dev/sda7 :
UUID=76bea7c0-d3b8-4ff0-bb66-4fdd497b0cf9 swap swap defaults 0 0

```
you can get the new, correct UUID by running (block ID):
```

sudo blkid

```

one other thing you could do while your working on it is just reformat that Windows partition to ext3 and move your /home to there - it's a little involved but its good to have your home on seperate partition

instructions to move home here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by kernelhaxor on 2008-08-22
I recently did the same.  This worked like a charm for me:

Burn a gParted live CD and boot using it ..
then delete ur windows partition and extend ur ubuntu / partition to use that space as well

---

### Post by shamusl on 2008-08-23
> **erfahren said:**
> you can boot up with the LiveCD and use GParted - just open the terminal and launch it with "gksu gparted"

delete the Windows partition and resize the Ubuntu one

if the swap is between the two you'll have to delete it as well and re-create it of course - if you do that you'll also want to check your /etc/fstab file afterwards to make sure the correct UUID is listed for it - example:
```

# Entry for /dev/sda7 :
UUID=76bea7c0-d3b8-4ff0-bb66-4fdd497b0cf9 swap swap defaults 0 0

```
you can get the new, correct UUID by running (block ID):
```

sudo blkid

```

one other thing you could do while your working on it is just reformat that Windows partition to ext3 and move your /home to there - it's a little involved but its good to have your home on seperate partition

instructions to move home here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Actually, I already have a /home partition, and I just want to expand my home partition and my / partition a bit.

---

