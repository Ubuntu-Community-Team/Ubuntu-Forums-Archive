---
title: "big problem. Can't access encrypted partition"
date: 2011-09-14
forum: Hardware
---

### Post by gpost3 on 2011-09-14
hi guys,
i made an acronis image backup of my entire drive as I was swapping it. Now that I am restoring the drive, my data partition (NTFS) seems to be encrypted (I thought i didn't encrypt it). I remember the passphrase I used to generate the key but I don't have that huge long key itself. Need some help to access and decrypt the contents of this partition. Please help.

---

### Post by gpost3 on 2011-09-15
bump

---

### Post by bodhi.zazen on 2011-09-15
Do you know how you encrypted it in the first place ?

---

### Post by gpost3 on 2011-09-15
I used disk utility when partitioning and I think I must have checked off the checkbox to encrypt the partition. The partition is NTFS. I believe disk utility uses cryptsetup to encrypt it? So I am hoping the big long encryption key is generated using a hash function which takes the input passphrase. If this is correct, then I may be able to generate that same key again using the passphrase. But this doesn't seem to be working (i.e. I can't unlock the partition using disk utility by entering passphrase).

---

### Post by bodhi.zazen on 2011-09-15
Is this your old home partition ? Then it would be ecryptfs.

Try this : [http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

If not, LUKS .

---

