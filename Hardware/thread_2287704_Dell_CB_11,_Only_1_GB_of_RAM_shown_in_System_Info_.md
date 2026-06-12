---
title: "Dell CB 11, Only 1 GB of RAM shown in System Info on 15.04"
date: 2015-07-21
forum: Hardware
---

### Post by Leo_Massey-Dickson on 2015-07-21
Hello, I have clean installed Ubuntu 15.04 on my Dell Chromebook 11 using John Lewis's custom Bios. The issue I have is that in the system information and in I-Nex, It is saying that I have only 1GB of memory when I really have 4. Is this just an incorrect reading for some reason, or is only 1GB of RAM really being used? Thanks in advance!


EDIT: I think I realise what has happened... during the install, I was having issues getting grub to load properly, so I told it to load with 1024m of memory, looking at the grub config file...this is still in there so I am assuming it is booting with only 1024. I shall edit it and see.

EDIT 2: So, I changed the memory amount to 4gb in the grub config file and now it reads 1.9. Now to remove the set amount and let it figure itself out. 

EDIT 3: So, clearing the amount of RAM in the grub config worked. It now shows and uses (judging by the speed) the 4GB of RAM. YAY :D 

Before - [http://i.imgur.com/Wdu0gtM.png](http://i.imgur.com/Wdu0gtM.png) 1GB RAM.

After - [http://i.imgur.com/jI1hGQ7.png](http://i.imgur.com/jI1hGQ7.png) 4GB RAM

---

