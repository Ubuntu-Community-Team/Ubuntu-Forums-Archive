---
title: "Edgy: Mounting Cdrom and DVD (automount)"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by User_Program on 2006-11-23
I have a problem with my dvd drive and cdrom drive mounting in edgy. Sometimes it mounts (automounts) fine other times I have to mount it with 

sudo mount /dev/hdd  ect

It always mounts fine I use sudo mount 

This happens it seems  when installing a game, ripping more then one cd ect.  I have also noticed that when I reboot and login the first cdrom or dvd I insert mounts fine the second and so on have to be mounted manually.

Using Kubuntu edgy
 
fstab entry for cdrom and dvd drive
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


and jumpers and ide cables are set correctly.

Any help would be great! thanks in advance.

---

### Post by ingo on 2006-11-25
my fstab entries are the same and things appear to be working fine :( 

not sure what the perpetrator of this particular problem might be...

---

### Post by tanari on 2006-11-25
I also have this problem. All blank DVDs must mount with sudo :(. Can mount only some DVDs with content.

---

