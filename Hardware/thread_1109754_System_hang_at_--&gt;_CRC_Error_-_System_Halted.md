---
title: "System hang at --&gt; CRC Error - System Halted"
date: 2009-03-29
forum: Hardware
---

### Post by Grey08 on 2009-03-29
Hello

I was using Kubuntu Desktop 8.10 doing Remote Desktop viewing my Ubuntu Server 8.10 (with Ubuntu Desktop GUI), right after i closed the connection at Kubuntu, the ubuntu pop up a message "blah blah Crashed", and i ended up hard reset the system. After this, system hangs at " CRC Error - System Halted" everytime when i try to boot into desktop.

At first i thought it was desktop corrupted, so i pressed "ESC" the Grub there and select "Recovery Mode", but the system still hangs at "CRC Error". So i was thinking it was the time to reinstall and when i tried to run "Kubuntu Desktop 8.10 without installing" option at system boot up, suprisingly it is still "CRC Error - System Halted".

What's wrong with it?? What should i do? Is it possible fix it without reinstall the system, because i have configured it as a Web server and FTP server, and this took me for 2 weeks for figured out how to configure them.


Best regards,
Grey08

---

### Post by Grey08 on 2009-03-29
Ok, I have solved the problem.

After Googled with CRC Error, i learned that, It is not only Hard disk would cause this problem, the other possibilities are:
1.Overheating problem
2.BAD RAM
3.HDD cable is losen (slightly losen would cause that too)
4.BAD HDD
5.Improper shutdown

I have run memtest86 and it has nothing error, and when i opened my case i found that my RAM wasn't plugged in tight, so i guess this is the problem.

---

### Post by secure on 2009-08-18
for me my ram is loose

---

### Post by alex.pancescu on 2009-08-19
> **Grey08 said:**
> Ok, I have solved the problem.
 
After Googled with CRC Error, i learned that, It is not only Hard disk would cause this problem, the other possibilities are:
1.Overheating problem
2.BAD RAM
3.HDD cable is losen (slightly losen would cause that too)
4.BAD HDD
5.Improper shutdown
 
I have run memtest86 and it has nothing error, and when i opened my case i found that my RAM wasn't plugged in tight, so i guess this is the problem.
 from experience i can tell you that the hdd is much more probable than the ram
to check the ram you can use memtest from just every linux livecd, i would recommend to let it make at least two passes...
for the hdd side, you could take a look on the manufacture's web site and see if there are any check tools listed there
hope this helps...

---

