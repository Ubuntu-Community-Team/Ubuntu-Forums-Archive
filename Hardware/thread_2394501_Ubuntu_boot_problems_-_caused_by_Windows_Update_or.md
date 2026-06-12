---
title: "Ubuntu boot problems - caused by Windows Update or Hardware?"
date: 2018-06-17
forum: Hardware
---

### Post by istvan5 on 2018-06-17
Hi !

Can be that this boot up problem occurred because I did a normal Windows Update of my Windows 8.1 ?
Or it was a real hardware problem?

**SError, Emask**

Ubuntu 16.04.4 LTS
Windows 8.1

1. I logged in Windows 8.1 I installed the updates
2. i had to restart pc, but was too slowly so I landed at Ubuntu login
3. again, I landed at Ubuntu login
4. I restarted pc, now even the normal boot messages from the BIOS were very slowly
5. then I started Ubuntu,
6. now the errors occured, see screenshots
7. I let Ubuntu be, and started and logged in in Windows 
8. Next day, I had no problems with the Ubuntu boot up and login, it worked again
--> so the question is, can it be that the Windows Update messed up something ?
--> or, was it a real hardware problem ?

[ATTACH=CONFIG]280131[/ATTACH][ATTACH=CONFIG]280132[/ATTACH][ATTACH=CONFIG]280133[/ATTACH]


thx for your opinions

---

### Post by oldfred on 2018-06-17
Windows 8 or 10 uses fast start up or hibernation. And the Linux NTFS driver will not mount read/write any hibernated NTFS to prevent damage.
And Windows will turn on fast start up with major updates, even if off before. 

So is Windows fast start up on now.
And are you mounting any NTFS partitions with fstab and it had to time out on read/write to load read only?

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

