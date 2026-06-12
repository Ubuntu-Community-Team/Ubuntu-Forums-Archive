---
title: "Ubuntu on External HDD"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by jaywalker13 on 2007-07-19
I run Feisty from an external hard drive. It's a CompactDrive PD70X (USB 2). The computer is a Dell Inspiron 9300 laptop (2GHz, 1GB RAM). It works pretty well, but there have been problems in getting it booted up each time. The boot order is set to boot  first via CD, then the external HDD, then the internal HDD which runs Windows XP Prof. I never knew when Ubuntu would boot up or whether it would just go to Windows. Also, when Ubuntu finally got going, the system would often crash just once, maybe after 10 minutes, but then be OK after restarting. Seems like it had lost contact with the CompactDrive. 

In the last 2 days, I think I have got the problem under control. ( Are the gremlins listening?) I now switch on the CompactDrive and let it boot into Windows. Then I check to make sure the computer has recognised the CompactDrive. Then, without unmounting the CompactDrive, I reboot. It seems to go to Ubuntu fine.

I had been having trouble with USB devices even attached to Windows recently; e.g. the Inspiron has 6 USB ports, but I added a 4 port hub to one of them. Worked but didn't like it much. And I got an additional external HDD (Le Cie Porche  320GB) which I left formatted FAT32 so it could be read by both Windows and Ubuntu. Maybe this was too much USB for the welfare of the computer. Maybe I forgot to unmount the Porche properly once or twice.

Any comments would be appreciated. What sort of things to consider when using an external HDD like this etc.

Jay

---

### Post by ubanchaos on 2007-07-19
why dont u just dual boot ubuntu and windows on the laptop their is no need to even have the external HD unless you are using it for saving just stuff

---

### Post by jaywalker13 on 2007-07-19
ubanchaos

Only bad reasons why I don't do that. Cowardice, ignorance etc. So much stuff and settings on the Windows that I don't want to lose or have to set up again if I partition the internal drive. Also scared that all the stuffing around I try to do with Ubuntu might stuff up the Windows partition.

You are right, I should just have a go at dual booting.

Thanks

Jay

---

### Post by sure_13 on 2007-07-19
You can easily boot from a GParted LiveCD or from a feisty livecd using the gparted application to repartition your internal drive without fear of losing anything windows. I've done it several times without any complications.

---

### Post by misfitpierce on 2007-07-19
Indeed gParted works quite well.. I did with another OS not win-doze ZzZz

---

### Post by ubanchaos on 2007-07-19
or like they said gparted works pretty well w/o lossing information

---

### Post by jaywalker13 on 2007-07-19
OK, I guess I have to give it a go. Just back up some absolute essentials first and make more space on the Dell's 80  GB HDD.

Actually I upgraded to Feisty from Dapper - Edgy, so I will have to download the Feisty Live CD and I guess a GParted Live CD?

Any advice appreciated on this. I'm a bit nervous about losing my Windoze stuff. I know W is bad, but I still can't scan, ocr or print with anything like the same quality via Ubuntu. Also can't do audio stuff like you can do with Reason, Sound Forge etc. Audacity, Timidity etc just doesn't come near it. Wish I could. I would really like to avoid having to use "hasta la Vista".

Jay

---

### Post by buntunub on 2007-07-21
Not to rain on the Gparted love fest here, but on my new hp laptop, Gparted refused to resize at all. It error'd out each and every time no matter what I tried. The only solution was to boot back into Vista and use its Disk Admin tool and that worked. Strange how Vista could do it properly and Gparted could not.

---

### Post by jaywalker13 on 2007-07-21
Interesting. Gparted seems like a good program but this is not the first time I have read of problems with it.

I downloaded the Live CD and tried to boot with it, but it could not get my video going. Said to use the Forcevideo script. I tried this but was asked for my video driver name, which I don't know  about.

Does anyone know how to find the name of their video driver? I'm using a Dell Inspiron 9300 laptop with a GForce Go 6800. Via Ubuntu, I looked up on ./nvidia-settings that the NVIDIA Driver Version is 1.0-9631, but that did not seem to be an option with the GParted Live CD Forcevideo script.

Thanks

Jay

---

