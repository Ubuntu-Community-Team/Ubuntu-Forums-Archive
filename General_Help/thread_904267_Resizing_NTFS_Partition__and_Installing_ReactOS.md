---
title: "Resizing NTFS Partition  and Installing ReactOS"
date: 2008-08-29
forum: General Help
---

### Post by hamzamusa on 2008-08-29
Hi

after i tried ReactOS on QTemu , and the other PC , i decided to install it on the Main PC . somehow , i don't have an extra partition to work with !
( Linux Partition : EXT3 , Swap , and NTFS Partition about 160GB ) . 

i tried to use   gparted  to resize , the partition and create a new one for ReactOS use , but it doesn't work !! 

any suggestions ?!

---

### Post by forger on 2008-08-29
Boot using the Ubuntu Live CD, then use the gparted to resize

---

### Post by hamzamusa on 2008-08-29
i tried  but the same problem it started , but the operation could not finish :(

any  other solutions ?!

---

### Post by forger on 2008-08-30
any reason why it does that?
what's the actual error?

---

### Post by louieb on 2008-08-30
Need to see the partition table. Post the output of:
```
sudo fdisk -l
``` (Lowercase L at the end)

---

### Post by hamzamusa on 2008-08-30
sorry , for the late reply , but somehow , the HDD drive is completley out . 

not a single OS worked with it , and LiveCDs can't access to the HDD at all . 

so i had to try to backup the data and reformat it . 

now it's working and i am using xubuntu instade of ubuntu !!

in order to resize : using my old Rescues Dicks and cds , i got Grub error 17 .

though also in order to fix it i made another post in here [http://ubuntuforums.org/showthread.php?t=904498](http://ubuntuforums.org/showthread.php?t=904498) 

which  didn't that helpful cause the LiveCDs can't access to My HDD at all !!

---

