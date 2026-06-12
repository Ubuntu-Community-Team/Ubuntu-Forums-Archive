---
title: "Utilise udev rules for loop device mounting as HDD"
date: 2017-11-20
forum: Hardware
---

### Post by bladez99 on 2017-11-20
I am not well-verse on udev rules, but i am looking at ways how i can emulate / simulate a hdd (kernel device name) to pretend as thou a disk via utilising loop device. 
Currently loop device is able to create a block device and creates /dev/loop[0-9]* devices.
There is also option / command to use mknod to create a node in /dev/ emulating /dev/sd[a-z]*

However, doing so somehow doesnt show up is the command lsblk. lsblk still looks at the /dev/loop naming convention. 

This is how i create the loop device and remove : 

Create:
dd if=/dev/zero of=vdd.bin bs=1M count=50
mkfs.ext4 qa-vdd.bin
mknod /dev/sdx b 7 500
chown root:disk /dev/sdx
losetup /dev/sdx vdd.bin

 
To remove:
losetup -d /dev/sdx
rm /dev/sdx

But lsblk do not see this as /dev/sdx but sees this as loop500 (Ubuntu 16.04)


hence, i read udev rules, hoping that this is possible to be done via udev rules detecting loop device and assigning proper /dev/sd[a-z]* device name. 

Is this possible ?

Or any suggestion.

---

