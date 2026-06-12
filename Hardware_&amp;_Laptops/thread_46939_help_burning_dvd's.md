---
title: "help burning dvd's"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by rachii on 2005-07-06
i have a plextor 716sa.  the sata model on a nforce2 mobo.  ubuntu detects it and it can read cd's/dvd's no problem.  BUT only half of the time will it burn a disc.  when it does burn, it goes smoothly and no problem and i am very happy.   but now it isnt again.  if i dmesg i get loads of errors similiar to this: ```
cdrom: This disc doesn't have any tracks I recognize!
SCSI error : <0 0 0 0> return code = 0x2
ata1: command 0xa0 timeout, stat 0x78 host_stat 0x0
SCSI error : <0 0 0 0> return code = 0x2

``` any clue on how i can keep it working, or any questions about my hardware/setup would be appreciated.

thanks

---

### Post by scoon on 2005-07-07
Hey there, 

Do you get the errors with the same brand of disc ?  Sometimes, different brands of discs make some burners real unhappy. 

regards, 

scoon

---

### Post by rachii on 2005-07-09
HEY, thanks for replying, i thought i was lost!
anyway, i only have the one brand of disc, they are great discs, and they have always worked well before (in windows, and ubuntu, and fedora) and they are one of the recommended ones for my drive.  
its weird.  like the other day, i was backing up one of my dvd's just to test out various software. and then burned the image, and everything was great.  then the next day i tried to backup some data files onto a dvd, and whatever program i used (nautilus, k3b, gnomebaker) they all just sit there at 0%  and various processes in the system monitor are zombied or asleep!  i dont know if i changed some setting somewhere to set it off or what?  but im sure that when i reinstall for breezy it'll all be straightened out and clean for me...but it would be nice to get it going again for now.

---

### Post by scoon on 2005-07-09
Hey there, 

Open up a shell when things aren't burning coreectly and type dmesg.  If there is a problem, it should present itself there.  Also try and keep track of what you are upgrading so you don't smash a working set up.  And good luck w/ breezy, I am going back to hoary for now.  

regards, 

scoon

---

