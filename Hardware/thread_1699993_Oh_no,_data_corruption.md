---
title: "Oh no, data corruption"
date: 2011-03-04
forum: Hardware
---

### Post by fa2k on 2011-03-04
I'm having some trouble with data corruption when reading from or writing to my hard drive. I'm using an encrypted volume on a 500 GB Seagate hybrid drive. I did some investigation and the following is true:

I can store a 500 MB file to my drive and read it back without problem if I read it back right after I transfered it (maybe it's cached, but I don't know). I transfered the file ~90 times over an Ethernet connection, and when doing md5sum after each transfer, there was no corruption (always the same result).

If I store the same file 90 times first, then read them back one by one, there is some corruption in most files: 
```
[muon:tmp]$ md5sum /tmp/testfile2.*
f5785c10d214742e002f834ece1a33fd  /tmp/testfile2.0.dat
f5785c10d214742e002f834ece1a33fd  /tmp/testfile2.10.dat
d5e1983f473be7f01ced1982b86b842e  /tmp/testfile2.11.dat
d41d8cd98f00b204e9800998ecf8427e  /tmp/testfile2.12.dat
...
d41d8cd98f00b204e9800998ecf8427e  /tmp/testfile2.89.dat
6b3dce433d17f65afae29fe8dfb9dd31  /tmp/testfile2.8.dat
384eff6cba0998c40a4f5c05cb9fd60d  /tmp/testfile2.90.dat
4d0e13d6f7cadf861d234f843f5026a8  /tmp/testfile2.91.dat
f5785c10d214742e002f834ece1a33fd  /tmp/testfile2.92.dat
f5785c10d214742e002f834ece1a33fd  /tmp/testfile2.93.dat
370f0f0a02b052f3732ce58da04c19f4  /tmp/testfile2.94.dat
21e605e32793de58b440b51964bb644e  /tmp/testfile2.9.dat

```

Any suggestions to how I can investigate, and what it may be?

---

### Post by fa2k on 2011-03-04
The result is actually quite interesting, if I order by the number of times I get each hash
```

  [...total of 40 unique hashes...]
  28763ef3ff87c885450c7ccc2da2dadb     1
  2d5f8eb3aa931aa270462cf3d680590a     1
  191cdc6ed599725b471da1e29ecdb346     1
  6b3dce433d17f65afae29fe8dfb9dd31     1
  cc67a426fc19f28132af8e8710c047ec     1
  d41d8cd98f00b204e9800998ecf8427e     28
  f5785c10d214742e002f834ece1a33fd     29

```

Why would there be two alternate hashes that are almost equally probable? The correct one is f5785c10d214742e002f834ece1a33fd . The files are video files, and even the ones with bad hashes seem to play fine.

---

### Post by fa2k on 2011-03-04
The error seems to happen when writing files, because the files don't change on repeated reads. I have a 20GB windows partition that I guess i can wipe, to check if it's filesystem related or a hardware problem.

---

### Post by colmesany on 2011-03-04
Try to do the same on another hard disk. Sounds like the disk about to give up.

---

### Post by fa2k on 2011-03-04
Thanks, I wrote some files to an external drive, and it seems to work fine. I will use that for now, but I'll do some more tests as well (I don't really trust the kcryptd/LUKS/what ever encryption system)

I recently updated the firmware on my drive, that may be the problem.

---

### Post by fa2k on 2011-04-03
It's completely bizarre, and I don't think this story will help anyone, but just to close this issue, here is what happened:

I saved some files to the 20GB partition, and there was some corruption. Thus the error had to be in the drive or the SATA interface, and not in the filesystem/encryption layer.

Having nothing to lose, I installed windows 7 and checked. I have no data corruption when writing to the drive! I don't understand it, it's completely ridiculous. I can't test 100 % properly though, because it's a hybrid drive, and I can't control the state of the flash cache. 

For now, I'm just going to assume that the drive is OK, and do regular checks.

---

