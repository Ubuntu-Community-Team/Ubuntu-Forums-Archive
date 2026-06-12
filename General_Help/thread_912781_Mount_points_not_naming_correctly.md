---
title: "Mount points not naming correctly"
date: 2008-09-07
forum: General Help
---

### Post by technotika on 2008-09-07
Hi Guys - think this is an easy one (hope so).....

Just reinstalled, getting things back to normal.

I used to have a "DATA" drive that mounted on my desktop. After reinstalling
it comes up as 253.1 GM Media.

so...to revert back to desired I have created a DATA folder in media and edited fstab to mount the partition there

see

/dev/sdc1       /media/DATA  auto   auto,user,exec,rw 0       0 

It now mounts at start up BUT does NOT have DATA as the lable its still
"253.1 GM Media" - as far as I am aware with my little knowledge that should have done the trick?????

Thanks guys

---

### Post by technotika on 2008-09-07
?Anyone :(

---

### Post by cdtech on 2008-09-07
What is the output of "sudo fdisk -l"

---

### Post by cdtech on 2008-09-07
Auto mounts are listed within the "/media" folder and manual mounts are done through the "/mnt" folder. The media directory uses the label to mount with so if the label of the drive is disk, it will mount as disk.

You can change the label on the drive so it mounts automatically at boot through the "/media" directory using the new label by using:
```
sudo e2label /dev/sdc1 DATA
```
It looks like you have a USB drive your working with and should mount automatically at boot (no need to add it to the fstab file).

---

### Post by technotika on 2008-09-08
e2label did the trick - thats well handy to know - gonna put that to good use. Thanks!

---

### Post by kpkeerthi on 2008-09-08
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by cdtech on 2008-09-08
> **technotika said:**
> e2label did the trick - thats well handy to know - gonna put that to good use. Thanks!

Your welcome....Good luck.

---

