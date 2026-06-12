---
title: "Cannot read CD"
date: 2009-12-19
forum: Hardware
---

### Post by titus2020 on 2009-12-19
Hello 

I am using Ubuntu 9.10. When i insert a disc, it is not auto mounting and also when i go into computer and try to access disc iam not able to see the contents of the disc. I also tried changing administrative privilleges. 


Thank you

---

### Post by Revolutionary101 on 2009-12-19
Do any other CDs work?

---

### Post by titus2020 on 2009-12-19
NO,

This is the first time i am using CD drive. I dont have other discs to try.

---

### Post by titus2020 on 2009-12-19
This is my fstab file. Community suggests making changes to fstab file. i am not sure if this helps. 



# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by Revolutionary101 on 2009-12-19
Hmm... well this could either be a problem with the disc, or it could be a problem with the Optical Drive's driver. What is the brand and model of the CD drive?

---

### Post by titus2020 on 2009-12-19
I am not sure of the brand. I have Hp pavilion dv2000 series Laptop.

---

### Post by titus2020 on 2009-12-19
Problem Solved. The disc is not working.

Thank you for the quick responses.

---

### Post by Revolutionary101 on 2009-12-19
Glad I could help

---

