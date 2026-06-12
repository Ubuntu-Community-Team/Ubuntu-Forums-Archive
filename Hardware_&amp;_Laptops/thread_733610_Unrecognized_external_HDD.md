---
title: "Unrecognized external HDD"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by Bobert on 2008-03-24
Hi, I was trying to connect an external hdd.  I did a brief search for similar problems, but being as I am a semi-new user to linux, I didnt know what actually applied to me as far as helping to resolve the situation.  I have 2 external HDDs, both connected by USB.  The smaller 250ishGig one works fine, but the other does not.  

I was reading about mounting the drive and I figure that may be the problem, but I feel like I am reading latin when looking over the code.  So far I tried this: 

sudo fdisk -l

Which supplies this:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03470347

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38156   306488038+  83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris


in the terminal and I did not see the drive connected.  I am also very weary about just going blindly into doing this because I do not want to format the HDD.  I have a lot of info on it which I cannot afford to lose.  Any directions how to do this, or a link to where the same problem is described would be greatly appreciated.  Thanks

-Bob

---

