---
title: "sata and ide drives changing names on reboot"
date: 2008-10-08
forum: General Help
---

### Post by Jonsnipes1 on 2008-10-08
im running 32bit hardy kubuntu on an asus motherboard amd.. i have 4 harddrives 2 ide 2 sata

each time i reboot the computer the drive names are changing order.. first the ide drives will be sda and sdb, then the next time the two sata drives will be sda sdb..  this is messing up my mounts and links..  strangly enough though the system runs fine when this happens and i can access all of my files even though the main system drive is also changing places... but causes me to reboot twice every time i need to reboot or change the fstab each time..  anyone had experience with this?? 

i was using 64bit 8.04, 32 bit 7.04 and 7.10 with no trouble..

thanks -jon

---

### Post by bodhi.zazen on 2008-10-08
This is why you list your drives in fstab by uuid or label rather the by /dev/sdxy

To see your drives by uuid :

```
blkid
```

and for fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Jonsnipes1 on 2008-10-09
thanks..  when i run blkid i just returns to a promt.. ive tried various switches and running as root / not root but get nothing back from the command

---

### Post by Jonsnipes1 on 2008-10-09
never mind..  got it to show through another command...  thanks for the help

---

### Post by crom.osec on 2008-10-09
You can try this article: [http://www.osec.ro/en/index.php/KB_Kubuntu:_Removable_storage_alias](http://www.osec.ro/en/index.php/KB_Kubuntu:_Removable_storage_alias)

---

