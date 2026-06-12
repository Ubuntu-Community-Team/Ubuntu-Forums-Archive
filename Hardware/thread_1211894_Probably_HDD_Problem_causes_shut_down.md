---
title: "Probably HDD Problem causes shut down"
date: 2009-07-13
forum: Hardware
---

### Post by Donny Darko on 2009-07-13
Dear All,

I have been using Ubuntu for quite some time. I have a dual boot system with windows 7 and hardy gnome desktop and also KDE 4.1. Now, since few days I am facing this problem, It has happened some times around 7-8 in last 15 days and not very regularly. The system shuts down while working with in 2 sec. It happens both on ubuntu and on windows7 so I figured that the problem is surely hardware related and I checked for CPU temperatures which happen to be in the range of 40-50 C, and I don't think that this is the cause of the problem. Next I looked at Hard drive Seagate 320 GB internal, and it turns out that after running all the tests successfully using 'seatools' from seagate it shutsdown in the similar way while running Long drive self test. The short drive self test, SMART test, short generic and long generic all passed successfully. It also shuts down in the same fashion while running error checking from windows. It does not give any error ever, and when you start it up again it doesn't show the screen that windows or ubuntu was shut down improperly last time and checks the drive for errors. Anybody has a clue what could be the problem ? I am typing this using the same system and same hard drive. It has happened rarely considering I need to use my notebook almost 12 hrs a day. System config is:

Dell Inspiron 6400
Intel core duo T2400 @ 1.83 Ghz
RAM 1 GB DDR2 667 Mhz
Seagate 320GB hard drive 5400rpm

Thanks and regards

---

### Post by PsyMonkey on 2009-07-13
Try runing a memory test.  I think it is one of the options in the grub menu.  Else just download memtest86+ and boot from the iso/cd.

---

### Post by Donny Darko on 2009-07-14
Tried the memory test, turns out fine.

---

