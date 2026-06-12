---
title: "Need help with my DVD-RW"
date: 2009-01-25
forum: Hardware
---

### Post by Azyl on 2009-01-25
I need help! This is the first situation that got my thinking to go bag to a Mycrosoft OS because i bougth a brand new DVD-RW i tested it at the store to see if it realy works and come back home and instal it on my computer, all looked ok when i insert a dvd it mount`s them even before editing the fstab (witch i modified and asigned a mount point), if i enter a blanck dvd or cd it opens it with brasero and i tryed to burn a dvd and at 99 % it gives an unexpected eror can`t set label ,the dvd gets ejected and is a gonner it can`t be recogniezed on any computer i modified brasero to not close the sesion on the dvd to not eject it and to simulate before burning, it simulates says that everything is ok and proceds to burn the dvd and i get the same eror and dvd is useles, i tryed even with the gnome/nautilius burning feature still nothing, i instaled K3Burner but it doesn`t recognize the DVD-RW only my old cd-rom if i use the comand line for cheching for writers it only checks my cd-rom witch ofcourse doesn`t have any burning capabilities. I instaled a device manager program to see if the sistem actualy see my DVD-RW and it does.

What shoud i do next i was thinking of reinstaling ubuntu maybe this way the dvd gets intaled corectly but i don`t wana lose all my programs and settings

I just want to get it to burn disk and later i can warry about enableing DMA mode and the rest so please give me an advice

And by the way the DVD-RW is not a ide device it on sata
PS: I`m sorry for my bad English.

---

### Post by hansdown on 2009-01-25
Hi Azyl.

dvd-rw disks don't work very well. Try using dvd+ rw disks. They work much better.

---

### Post by Azyl on 2009-01-25
Yes i`ved read about it but the thing is a tried even with a blanck cd not DVD and still it didnt work, thanks for your reply.

---

### Post by cariboo on 2009-01-25
I seem to have intermittent problems with Brasero, especially with dvd+r's, I have since switched to K3b and no lnoger have any problems.

K3b is in the repositories.

Jim

---

### Post by Azyl on 2009-01-25
i have k3b instaled only that it doest detect my dvd-rw it only detects my old cd-rom and i can`t make it recognize the drive so if you know a way to that please tell me. Thanks for the ideea

---

### Post by Azyl on 2009-01-26
I fixed the problem were my dvd-rw wasn`t recognized it was a fstab eror i begin to hate that litle config file only if someone would think of a program that has the soulporpouse of dealing with mounted device (i have that program mountmanager but it doesnt solve anything). Now i have tried burning a dvd using K3B all was ok no eror no nothing until i inserted the disk back into my computer and the disk is not recognized all i get is an unable to mount in nautilius what now?

---

