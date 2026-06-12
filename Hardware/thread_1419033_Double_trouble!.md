---
title: "Double trouble!"
date: 2010-03-01
forum: Hardware
---

### Post by clydeseal on 2010-03-01
Okay so I installed ubuntu onto my external HDD about a week ago. I really like the os and I was going to see if I could put it on my OLD crappy laptop and see if I could get it to work. I got this laptop from a friend he said that he had gotten into some viruses and it had been wiped clean several times, but it still didn't work right.

So I used the same copy of Karmic Koala that I installed on my external HDD (which works fine) to install onto the old laptop. The laptop recognizes the disc and I boot from it. I install ubuntu, and chose the erase hardrive option just to be sure. The installation goes fine.

So I start it up for the first time and I get GRUB loading, when I select to run Ubuntu from GRUB is says "Error: no such device #############" (#############=a whole bunch of numbers and letters and dashes). I  did some research and I found a temporary solution. When I get into GRUB I can press e to edit command, if I delete the line that says -search floppy- and press ctl+x to boot, then I can start it up without any problems. However, I have to delete this line EVERY time I boot if I want it to work. Is there some way that I can permanently delete this line.

Once I got it to boot I got a notification that says "DISK FAILURE IS IMMINENT" I figure that the viruses must have damaged the hard drive. Is there any disk repair tool/chkdsk?

---

### Post by clydeseal on 2010-03-01
Good news! I was able to solve the "no such device error" I am still getting the notification for "DISK FAILURE IS IMMINENT"

---

