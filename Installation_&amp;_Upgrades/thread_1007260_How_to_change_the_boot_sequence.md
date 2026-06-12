---
title: "How to change the boot sequence"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by fellowsh on 2008-12-10
Dear all, I have a multiple boot machine. It used to have a dual boot with XP 64 and XP 32. The OSs are in 2 separate hard disks.

I now installed UBUNTU 8.10 in a partition of the same disk which contains XP32.

Now, when I turn on the PC I have a screen very similar to this:
[http://www.psychocats.net/ubuntu/images/installinghardyplus23.png](http://www.psychocats.net/ubuntu/images/installinghardyplus23.png)

How can I change the settings so that Ubuntu is not the default but windows instead?
Thx
r

---

### Post by iponeverything on 2008-12-10
```
sudo nano  /boot/grub/menu.lst
```

uncomment and set "default num" near the top of the file.

---

### Post by davidbilla on 2008-12-10
Open menu.lst

$ sudo vi /boot/grub/menu.lst

In that file search for the line 'default 0'

Change it to 'default 3'.

---

### Post by fellowsh on 2008-12-12
> **davidbilla said:**
> Open menu.lst

$ sudo vi /boot/grub/menu.lst

In that file search for the line 'default 0'

Change it to 'default 3'.
Thank you m8

---

### Post by fellowsh on 2008-12-12
> **iponeverything said:**
> ```
sudo nano  /boot/grub/menu.lst
```

uncomment and set "default num" near the top of the file.
Thank u m8

---

### Post by Partyboi2 on 2008-12-13
You can follow [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") guide through. If you get stuck or still not sure how to make the changes open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /boot/grub/menu.lst
``` and someone should be able to help.

---

