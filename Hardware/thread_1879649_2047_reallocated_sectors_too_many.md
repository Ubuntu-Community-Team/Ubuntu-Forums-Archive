---
title: "2047 reallocated sectors too many?"
date: 2011-11-12
forum: Hardware
---

### Post by jonnyboysmithy on 2011-11-12
I have a 400GB drive that has 2047 reallocated sectors. Disk utility thinks its failure is imminent. How many reallocated sectors is okay? Is the drive 'safe' to use?

---

### Post by Rubi1200 on 2011-11-12
I highly recommend that you start backing up all important data now!!!

If Disk Utility is reporting that many reallocated sectors it is not a good sign.

---

### Post by father_ted on 2011-11-12
no!! backup everything and RMA the drive.

and test the new one carefully before you start to use it. been a lot of DOA drives lately.

run this a few times on the new drive to make sure its perfect before you commission it ( pointign at the right device )

sudo e2fsck -c -v -f -k /dev/sdd1

and use gsmartcontrol to check the drive too. it can run the internal diagnostics of the drive.

---

### Post by jonnyboysmithy on 2011-11-12
> **Rubi1200 said:**
> I highly recommend that you start backing up all important data now!!!

If Disk Utility is reporting that many reallocated sectors it is not a good sign.

Okay! :):)

---

### Post by jonnyboysmithy on 2011-11-12
> **father_ted said:**
> no!! backup everything and RMA the drive.

and test the new one carefully before you start to use it. been a lot of DOA drives lately.

run this a few times on the new drive to make sure its perfect before you commission it ( pointign at the right device )

sudo e2fsck -c -v -f -k /dev/sdd1

and use gsmartcontrol to check the drive too. it can run the internal diagnostics of the drive.

I'll test my laptop drive, I think its healthy but better safe than sorry. The 400gb drive was replaced and was sitting in the drawer of spare bits.. So any reallocated sectors and its a gonner?  EDIT: what does RMA stand for?

---

