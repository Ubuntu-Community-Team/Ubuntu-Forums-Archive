---
title: "Sudden memory stick failure"
date: 2009-02-19
forum: Hardware
---

### Post by Jayhawker on 2009-02-19
When copying some files, a memory stick kept stuck suddenly and from then on (I had to unplug it without being able to unmount it) it is not recognized by linux. 

Please, is there any way to make this memory stick work again?

Thanks.

---

### Post by linux_tech on 2009-02-19
see if umount in terminal works or not
with flash drive plugged in, in the terminal type:
```
sudo fdisk -l
```
check for listing of usb flash 
then in terminal type:
```

sudo umount /dev/sda1
```
/sda1 is an example

To get more info on drive yoiu can also use fstab
```
cat /etc/fstab
```

---

### Post by Jayhawker on 2009-02-19
> **linux_tech said:**
> see if umount in terminal works or not
with flash drive plugged in, in the terminal type:
```
sudo fdisk -l
```
check for listing of usb flash 
then in terminal type:
```

sudo umount /dev/sda1
```
/sda1 is an example

To get more info on drive yoiu can also use fstab
```
cat /etc/fstab
```

Thank You for your interest, but that only seems to give some information. Not quite sure how to solve the problem from it. Can you explain me it some more? 

Thank You very much

---

