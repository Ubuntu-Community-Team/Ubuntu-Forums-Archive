---
title: "Ubuntu installation hang at &quot;Starting partitioner&quot;"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by ahbeng78 on 2006-02-18
Hi all,

I've a new Ubuntu(5.10) installation CD from the official web site, when i try to install on my PC (where this system have WinXP SP2 installed with 3 partition, i plan to install on the last drive, E drive), everything start pretty well  , but then while it try to load/start the partitioner at "Starting partitioner", at about 41%, it just hang (I've wait for long enough, about 30minutes), but no luck, no response at all, then i try to reset the system and start over again, but still the same, then after that i shutdown totally. In the next day morning, I try to install again, but hey,  still the same problem, hang at the "Starting partitioner", I've confirmed that the content of the CD is OK. 

Anyone has idea of this? Any solution? Or this is the bug of Ubuntu? huh?

---

### Post by kpachar on 2006-02-18
[QUOTE=ahbeng78]Hi all,

I've a new Ubuntu(5.10) installation CD from the official web site, when i try to install on my PC (where this system have WinXP SP2 installed with 3 partition, i plan to install on the last drive, E drive), everything start pretty well  , but then while it try to load/start the partitioner at "Starting partitioner", at about 41%, it just hang (I've wait for long enough, about 30minutes), but no luck, no response at all, then i try to reset the system and start over again, but still the same, then after that i shutdown totally. In the next day morning, I try to install again, but hey,  still the same problem, hang at the "Starting partitioner", I've confirmed that the content of the CD is OK. 

Anyone has idea of this? Any solution? Or this is the bug of Ubuntu? huh?[/QUOTE]

I too have the same problem. I'd like to add here some more info regarding this problem.
1. These modules were not found : ide-mod, ide-probe-mod, ide-detect.
2. I did Ctrl+Alt+F2 and opened the shell. I ran the "find" utility starting from / to search for these modules. They were not found.
3. I loaded the "download installer components" module and connected to the US ubuntu HTTP site. The list of modules that showed up did not have these modules.
4. I too checked CDROM integrity and found that it was OK.
5. I had downloaded ubuntu-5.10-install-i386.iso and burnt it to a CD.
6. When normal install is chosen (by pressing ENTER at boot: ) it shows a series of "killed". This happens at the onset of the partitioner. The 3rd(or 4th) terminal shows restarting "debian-installer" repeatedly.
7. Prior to that, it shows as many "file not opened" (or something similar) as there are number of partitions on the disks.
8. I have one 10GB disk and one 40 GB disk. Xandros, PCQLinux, DSL and Puppy Linux run without problems on it. 

Please help me install Ubuntu.
--Thanks in advance.

---

### Post by ale_jrb on 2006-02-18
I have this problem as well... Help!

---

### Post by Mustard on 2006-03-14
[QUOTE=kpachar]I too have the same problem. I'd like to add here some more info regarding this problem.
1. These modules were not found : ide-mod, ide-probe-mod, ide-detect.
2. I did Ctrl+Alt+F2 and opened the shell. I ran the "find" utility starting from / to search for these modules. They were not found.
3. I loaded the "download installer components" module and connected to the US ubuntu HTTP site. The list of modules that showed up did not have these modules.
4. I too checked CDROM integrity and found that it was OK.
5. I had downloaded ubuntu-5.10-install-i386.iso and burnt it to a CD.
6. When normal install is chosen (by pressing ENTER at boot: ) it shows a series of "killed". This happens at the onset of the partitioner. The 3rd(or 4th) terminal shows restarting "debian-installer" repeatedly.
7. Prior to that, it shows as many "file not opened" (or something similar) as there are number of partitions on the disks.
8. I have one 10GB disk and one 40 GB disk. Xandros, PCQLinux, DSL and Puppy Linux run without problems on it. 

Please help me install Ubuntu.
--Thanks in advance.[/QUOTE]


How much RAM do you have on your system? (just out of curiousity)

I'm trying to find a common thread to this 'killed killed' problem when running the partitioner.

---

