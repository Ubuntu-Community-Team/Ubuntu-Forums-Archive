---
title: "Mounting NTFS drives"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by Brando569 on 2005-08-21
hey whenever i mount an ntfs drive it wont let me browse it, it says i dont have enough permissions. then i go to chmod it and it says i cant change the permissions cuz its a read only file system. this is my fstab:

/dev/sda1	/mnt/maxtor	ntfs		rw,exec,users,group,owner     0	      0

how can i get it so that i can browse the drive w/o being a member of the root group?

---

### Post by rpgcyco on 2005-08-21
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

You can't write to NTFS drives either, as it will corrupt it.

- Rpg Cyco

---

### Post by sridenour on 2005-08-21
[QUOTE=rpgcyco][http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

You can't write to NTFS drives either, as it will corrupt it.

- Rpg Cyco[/QUOTE]
Actually you can, even Kanotix includes this little tool so you can fix a Windows install.
[http://sourceforge.net/projects/linux-ntfs](http://sourceforge.net/projects/linux-ntfs)

Although yes there is still a chance for file corruption.

---

### Post by Brando569 on 2005-09-22
what were the options? i cant remember them and ubuntuguide.org is down....

---

### Post by aysiu on 2005-09-22
[QUOTE=Brando569]what were the options? i cant remember them and ubuntuguide.org is down....[/QUOTE] [http://www.frankandjacq.com/ubuntuguide/5.04/#automountntfs](http://www.frankandjacq.com/ubuntuguide/5.04/#automountntfs)

---

