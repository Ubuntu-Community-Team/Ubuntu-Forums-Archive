---
title: "Ubuntu boot problem after vista installed..."
date: 2008-10-13
forum: General Help
---

### Post by smartashu on 2008-10-13
Hi friends....
I'm having a problem..
In my pc Vista and Ubuntu8.04 was running quite well..
But due to some problems in vista which was installed in primary partition ..i had formated vista..
first i deleted the primary partion and then formated to install vista.....
now i'm not able to boot my ubuntu..

plzz suggest me proper solution..
i have tried the following thing but i was unsuccessfull......
Boot from live cd, and use the following commands...
sudo grub
root (hd0,9)
setup(hd0)
quit

when i use the command to display the grub menu..
but there was nothing in the text file opened like boot/menu/1st..
plzz reply me.....i'm in deep trouble...

---

### Post by caljohnsmith on 2008-10-13
Are you sure Ubuntu is on sda10? How about trying this from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If that doesn't work, then please post:
```
sudo fdisk -lu
```

---

### Post by smartashu on 2008-10-13
yaa i tried all....

none of them worked....

ubuntu was not appearing in grub list....

i downloaded one software easybcd that worked..

now everything is fine......
thanks for reply

---

