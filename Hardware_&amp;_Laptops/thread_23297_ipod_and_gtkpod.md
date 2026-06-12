---
title: "ipod and gtkpod"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by ewlabonte on 2005-04-01
I have an interesting problem. I have ubuntu 4.10 running on my dell
inspiron 1100 laptop. When syncing my ipod under Gnome, I mount it (sudo mount /dev/sda2 /mnt/ipod) and run gtkpod as an ordinary user. After I shut gtkpod down I
run "sudo eject /media/sda2" from bash. It usually gives me an error
message "eject: unable to eject, last error: invalid argument", but it
*does* eject the ipod. 

When I sync my ipod from WindowMaker (my preferred window manager) I mount
the ipod as in Gnome, but if I run gtkpod as an ordinary user, it can't
read the ipod. Inadequate permissions. I have to run it as root, which is
not very desirable. Also, I can't eject /media/sda2 because sda2 fails to
appear in the /media directory. 

Can anyone explain this to me?

---

