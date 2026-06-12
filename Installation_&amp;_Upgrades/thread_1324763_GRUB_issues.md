---
title: "GRUB issues"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by m4g1c on 2009-11-12
i originally had windows on sda1 and ubuntu on sda5. ubuntu was installed after windows so it installed grub itself and had no issues with dual boot

i had a corrupted grub and tried a million things to restore it with no luck. ultimately, i reinstalled ubuntu again on sda7 and let it reinstall grub. now grub shows windows, my old ubuntu, and the new ubuntu and boots all of them fine.

now i want to get rid of the new ubuntu (since i only installed it to get grub back) but when i delete the sda7, im getting problems with grub again.

im not too sure, but is grub being run from sda7 since when i delete it im getting the error (same one that happened when i had original windows and ubuntu)? and is there some way i can "copy" the "working" grub so i can delete sda7 and have grub working normally again? im pretty sure theres 2 grubs installed cause when i do

sudo grub
find /boot/grub/stage1

i get two results, one which is likely the "new" working grub and one old broken one. how would i go about deleting sda7 but still keep grub working? thanks

EDIT: ok heres what i did to fix it. basically reinstalled a fresh version of grub

booted a live CD and did

cp /usr/lib/grub/i386-pc/* /media/disk/boot/grub
grub
grub> root (hdx,y)
grub> setup (hdy)

---

