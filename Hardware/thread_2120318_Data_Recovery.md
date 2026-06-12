---
title: "Data Recovery"
date: 2013-02-26
forum: Hardware
---

### Post by chrisqck on 2013-02-26
Hi Everyone, 

I have an external HDD size of 500GB. Today when I plugged it to my desktop running Windows, it's not detected. I boot to Ubuntu and plug it in and it's not detected. (auto-mount)

so I go to terminal and SUDO FDISK -L and the HDD is not listed. However, if I go to Disk program, it indicate that it's mounted as SDH. 

Would appreciate if anyone can advise me any way to force mount this HDD ? It's still under warranty but usually they'll just replace a new HDD and the data would be lost forever. I would like to recover what's on the HDD if possible. 

p/s: I've used ntfs-3g previously to fix issue on external USB HDD but that only work if FDISK -L list the hdd in the result. In this case it doesn't. 

Any assistance / guide in recovering the files is much appreciated. And thanks in advance. 

Chris

---

### Post by carl4926 on 2013-02-26
Are you sure it's not even seen under windows?

It's possible it's just dirty

chkdsk -f [drive_letter]:
from the windows shell might be the best move
(but I am not a windows boffin)

Does Gparted see it?

---

### Post by chrisqck on 2013-02-28
installed Gparted and when i plugged in the external drive, i get input/out error during read on /dev/sdh...

---

### Post by carl4926 on 2013-02-28
> **chrisqck said:**
> installed Gparted and when i plugged in the external drive, i get input/out error during read on /dev/sdh...

sounds terminal

---

### Post by Mark Phelps on 2013-03-01
> **chrisqck said:**
> Hi Everyone, 

I have an external HDD size of 500GB. Today when I plugged it to my desktop running Windows, it's not detected.

What version of Window are you using? If you're using Win7, then open the Disk Management tool and scroll down to see if the drive is shown there.  If you find it, it won't have a drive letter assigned.

See if it will let you assign a drive letter.

If it won't, you may then have to use Data Recovery apps to get any data back.

---

