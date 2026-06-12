---
title: "problem with grub"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by adramalech on 2009-09-30
okay so this is how my hard drive partitions are setup...

/dev/sda1 <--- windows format ntfs
/dev/sda4<-- extended partition
    - /dev/sda5 <--- ubuntu 9.04 server format ext4
    - /dev/sda6 <--- swap

now i am wanting to be able to boot my server but are unable to make it boot by setting boot flag and i used to have ubuntu 9.04 desktop as a primary and i then deleted it and vista to make one parition for windows 7 but my issue is damn windows boot manager took over and it won't allow me to boot into my server...

any ideas should i try and just switch boot managers but booting to live cd and then installing grub....i tried this but i get bios error.... i am trying to install it on /dev/sda1 my windows 7 partition.......

also, i went to find where /boot/grub/stage1 is at in it says (hd0,4)...

any help would be greatly appreciated

---

### Post by shredder12 on 2009-09-30
I think you are having trouble with the final "setup" command..
The most basic way is to overwrite your MBR.. 
for that you need to use 
```
setup(hd0)
```

for more info on restoring grub..
read this..
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB)

---

### Post by adramalech on 2009-09-30
thanks alot when i get home today i am sure to give it a try i really thought maybe it was my error in syntax...:lolflag:

---

### Post by adramalech on 2009-10-06
okay sooo i have fixed my last issue and now i am having to deal with another one....same idea though

i have just made these changes to my laptop:
/dev/sda1 - ntfs windows vista
/dev/sda2 - ntfs windows vista recovery
/dev/sda3 - ext4 ubuntu 9.04 amd64
/dev/sda4 - extended
/dev/sda5 - linux/swap (logical)
/dev/sda6 - ext4   <-- gentoo amd64 (logical)


now i need to update my grub so that either the new gentoo install gets added on to my already grub mbr for ubuntu 9.04...meaning installing a logical parition to be recognized by grub...

or i uninstall grub off of ubuntu and install on gentoo...

my issue is that gentoo distro is on a logical partition but no matter how many times i tell grub: root (hd0,6) it tells me nothing found!!!

any help would be of great help since i spent 4 hours custom building my gentoo distro from scratch....the only way i can do anything with the gentoo side is if i chroot into it through ubuntu and then mount the three things to chroot the root the boot and (i forget) something else)

if no one knows of a way for me to do this then...is there a way for me to make gentoo a primary partition without having to lose all the data???

---

### Post by shredder12 on 2009-10-07
I think its jst a slight error..
when you say hd0, it means you are referring to the whole hard disk..
similarly..
(hd0,0) -> /dev/sda1
(hd0,1) -> /dev/sda2
...
....
(hd0,5) -> /dev/sda6
(hd0,6) -> /dev/sda7

so basically you are trying to access /dev/sda7 which doesn't exist..
use (hd0,5) instead.
I hope it works..

---

