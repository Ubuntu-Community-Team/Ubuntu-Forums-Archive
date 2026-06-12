---
title: "Edgy poor performance"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by GermFY on 2006-11-12
Hi all, I was using the 6.06 version of Ubuntu and yesterday I decided to upgrade to Edgy. Everything went fine (I upgraded using the gksu "update-manager -c" command) Some minor alerts where shown during install and configuring process. ](*,) 
But now the system feels incredibly slow. I use my computer for programming and general websurfing. Launching any application takes and incredibly amount of time and then the HD starts having a lot of activity. If everything is up and running the performance is good. On Dapper I had a good performance at all, now even starting the system up takes too long. 
Anything I might missed during the installation process? Is there a place I can view the logs of the installation and try to fin out if anything went wrong and I might missed? Any help will be great appreciated.

Best,

G

---

### Post by 23meg on 2006-11-12
Enter the command *top* in a terminal and see if any processes are taking up too much memory or CPU time. Keep the window open as you perform different tasks to see if something particular is hogging your computer.

Are you sure you have a swap partition and that it's mounted correctly?

---

### Post by GermFY on 2006-11-12
Well Xorg seems to be aroung everytime consuming as much as 4 to 5% of the CPU. Other apps like Acrobat Reader or Eclipse or Firefox consume as much as 30% but when finished loading everything returns to normal.
About the swap partition, I'm not sure about it. I did the default 6.06 installation (I have no other boot partitions in my computer) and then did the upgrade I had Dapper for almost 4 months and everything worked faster than Windows XP. So maybe there's no swap partition....

---

### Post by GermFY on 2006-11-12
Confirmed: There's a linux-swap partition and it's 1.42 gig long.

---

