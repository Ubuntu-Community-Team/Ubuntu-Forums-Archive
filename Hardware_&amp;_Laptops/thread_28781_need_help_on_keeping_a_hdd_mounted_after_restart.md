---
title: "need help on keeping a hdd mounted after restart"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by martinez9049 on 2005-04-21
hi, i have a sata hdd that i mount by typing 
$ sudo mount -t ntfs -o umask=0222 /dev/sda1 /mnt/Media
and all works fine. but when i restart the computer i have to remount it. how can i make linux mount it when it's starting up? btw, i have a 3ware raid card so i *don't think* i have to load any drivers prior to mounting as i've been told the driver is native.

thanks,
ismael m

---

### Post by Leif on 2005-04-21
Add it to your /etc/fstab file. smt like :

/dev/sda1 /mnt/Media ntfs    umask=022      0       0

---

### Post by Leif on 2005-04-21
Actually, that doesn't look right on second thought. you should make a folder under media (sudo mkdir /media/windows) and mount it there :

/dev/sda1 /media/windows ntfs umask=022 0 0

---

### Post by martinez9049 on 2005-04-21
ok i added that but when i restart and go to a file manager and go to that directory it tells me that only root can mount the directory. i suppose that if i enabled gdm to login as root it would solve that problem but i don't want to do that.

thanks,
ismael m

---

