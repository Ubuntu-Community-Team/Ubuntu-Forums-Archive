---
title: "Help with cd's!!"
date: 2008-04-27
forum: Hardware
---

### Post by aflog on 2008-04-27
Hiya...

I have a 52x CD-R drive in my computer at the moment. It can read everything perfectly fine in windows, but in linux, it continues to reject blank CD-R's. (by reject i mean, does'nt mount or anything, then ejects it after a minute or so). The line i have for it currently in /etc/fstab is > /dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0 and im at a loss. Im using Xubuntu 8.04 with XFCE 4.4.2... it's been suggested i tell xfce to stop trying to autmount a cd when i put it in, but i don't know how :S

Any help is appreciated. 

Thanks

Jayden

---

### Post by aflog on 2008-04-27
Update: It may be that its not /dev/hdd but /dev/sdd, it seems when i updated to 8.04 everything became sdxx instead of hdxx. If that has any affect... :S

Jayden

---

### Post by aflog on 2008-04-27
I was also just thinking, is there maybe some kind of plugin or library i need to download to deal with this type of cd? Im so lost lol

PS: Doesn't work yet ;)

Thanks

Jayden

---

### Post by aflog on 2008-04-27
...nvm too late... i got really pissed with it this morning and took to it with a hammer :)

Jayden

---

