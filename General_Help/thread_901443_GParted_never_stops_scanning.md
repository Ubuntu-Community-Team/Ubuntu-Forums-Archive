---
title: "GParted never stops scanning"
date: 2008-08-26
forum: General Help
---

### Post by yessirsir on 2008-08-26
I just installed another HD (FAT32 system file) as slave in my machine and since then the GParted does not stop scanning  ..it just hangs. its not that it takes a while, it really doesnt respond after starting to scan. i never get to see the available partitions list.

I have read threads about it and i found that this might be due to the floppy drive being enabled in the BIOS, so i did turn it off. 

Unfortunately the same problem still occurs. I wanted to go and get some data out of that second HD and then format it. But for now it is not mounted. i would have mounted it but i actually use GParted to know the drive path ( ex: /dev/sda1, /dev/hdd#) since i cant seem to see this info anywhere else. Anyway i would still need GParted afterward to change the filesystem. 

Im new to Linux and I aslo don't have access to Windows (i only installed Wine), so i am not sure how to proceed to resolve this matter. I tried the Live CD session too but same thing occurs. 


Maybe i needed to do something that i didnt know about before plugin-in that extra HD ? or maybe if i mounted it first it would be ok ?

---

### Post by yessirsir on 2008-08-26
ok its been 6 hours ...maybe more , and nothing changed i just can't figure out why this GParted scans forever. whatever post i read its just not what im looking for ....

Floppy is off in bios so it's not that :(



Edit: errr... not good , now i got in the /media folder, i wanted to create a folder in there cause i thought i need to do that to mount this second drive (since i cannot use GParted to do it :S) but as soon as i selected "open terminal here " (in /media folder) the OS crashed displaying a bunch of error msg ...i didnt have time to read anything ,it was too fast , and then it reloaded by itself back to the login screen .... 

probably a lost cause

---

