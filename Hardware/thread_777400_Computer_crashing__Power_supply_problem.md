---
title: "Computer crashing / Power supply problem?"
date: 2008-05-01
forum: Hardware
---

### Post by Flying Mandarine on 2008-05-01
Hi,

I have had several problems since the building of a new desktop computer, most notably with the nVidia drivers, although everything seems fine in regard to that now.

However, I am now faced with a curious problem: my computer screen turns off, or the keyboard and mouse don't respond anymore (but the screen and sound still work), or the computer simply restarts.

This problem happens only after my computer has been on for some time, and does it increasingly more during the day; I can play a video game for an hour without problem when I turn my computer on, but after having been on for ten hours, I can't even open too many Firefox tabs without the computer crashing (as described above).

I already discussed the topic in another [thread]("http://ubuntuforums.org/showthread.php?t=768749") (especially pages two and three), but since the nVidia problem was solved, I thought it'd be better to create another thread (I hope it's OK).

After what people posted, I thought it could be a problem with my power supply, but I am still not convinced since it is a 750W (but of a bad brand). I don't think it is a problem of heat though. I wonder if it could be linked to one part of the power supply not powerful enough for those rather high-end components I have?


Here's my configuration:

GeForce 9600 GT 512 mb (Twintech)
Power supply Advance EA4G-750, 750W
Dual Channel DDR2, XMS2, 2 x 1 Go, PC2-6400, Corsair
Hard drive DiamondMax 22, 500 Go, 7200 tpm, buffer 32 Mo, SATA II, Maxtor
Main board GA-P35C-DS3R ver. 2.1, socket 775, Gigabyte
Processeur Core 2 Quad Q9300 (2.50 GHz)


Thanks to everyone in advance!

---

### Post by Flying Mandarine on 2008-06-15
One month and a half after, the problem is still happening, although slightly different now:

I have a GA-P35C-DS3R mother board, and I saw there was an upgrade (to F10, I didn't try F11 as it is just a beta version), so I decided to install it.

Now, my computer doesn't suddenly crash anymore. However, if lots of things (well, not even that many actually) are running, something will crash (usually Firefox). Once one software has crashed, I cannot launch it again, and everything else begins to crash one after another. Nothing really works anymore, so that even clicking on the red button (to turn off the computer), nothing happens. I have to either hard reboot or do CTRL + SHIFT + F1 to access a terminal and reboot from there.

I sincerely hope someone might have a clue on what's going on.

Thanks in advance,

Flying Mandarine

---

### Post by Odrodzona-Sarmacja on 2008-06-16
Try turning networking off, when using graphic applications. It helps me against freezes generally. Also unistall "remote desktop" and "gnome vpn" to help against freezes when network connected and using firefox and only firefox. This way firefox never freezes my xubuntu 8.04.

I have also Nvidia, but just 128mb :) I guess having more memory in nvidia helps to stretch times between freezes.

---

### Post by Flying Mandarine on 2008-06-16
Wow thanks for the answer Odrodzona-Sarmacja, I was getting a bit desperate. :)

I will try that out and tell you how it goes. But I think I'd better try to fix the problem rather than evade it. My computer is rather new so well, it should handle those things pretty well.

Also, that might be of interest: I didn't use BOINC and it crashed, well, fairly regularly. Now I use BOINC (which use constantly, say, 85% of my Core 2 Quad) and it doesn't necessarily crash more, I think. So it wouldn't be linked to my CPU, it seems?

---

### Post by Odrodzona-Sarmacja on 2008-06-17
It is certainly something with xorg and nvidia... but cpu issue it could be as well... I don't get any cpu error messages in my syslog for sure.

---

