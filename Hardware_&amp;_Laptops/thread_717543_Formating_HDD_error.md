---
title: "Formating HDD error"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by Gouz on 2008-03-07
Greetings everyone

I am trying to format an external HDD and make it NTFS

what I have done up until now it:

```

sudo fdisk -l (to find my hdd)
fdisk /dev/sdb (then I follow the commands and make it NTFS by selecting 7)
mkfs.nfts /dev/sdb -F (cause other which it doesn't want to proceed and format it)

  #but then I get an error msg at the end

Initializing device with zeroes: 100% - Done.
Creating NTFS volume structures.
Error writing to /dev/sdb : Input/output error
Error writing non-resident attribute value.
add_attr_sd failed: Input/output error
Couldn't create root directory: Input/output error


```

Do you have any idea?
Thanks

---

### Post by lswest on 2008-03-07
did you have your drive mounted while formatting it?  if so, unmount it first

---

### Post by Gouz on 2008-03-07
It is unmounted.
And now it don't recognize the mkfs.ntfs command
(I used the mkfs -t ntfs)

---

### Post by Gouz on 2008-03-07
Ok found it :D

all you have to do it


```

sudo fdisk -l (to find you hdd)
fdisk /dev/sdx  (sdb in my case)

Command (m for help):  n for you partition, t for inserting the Hex code (type L to list codes): linux are 83 ntfs is 7 followed by Enter (button)
Command (m for help):w (to apply changes)
#and then you will have to format.
sudo mkfs -t ntfs /dev/sdx (sdb in my case)
#mind you it will take some time :P  and then you will the following:

Cluster size has been automatically set to 4096 bytes.
Initializing device with zeroes: 100% - Done.
Creating NTFS volume structures.
mkntfs completed successfully. Have a nice day.



```

I hope it help the rest of you :P

---

