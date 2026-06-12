---
title: "back to 9.04"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Seankn on 2009-09-10
Ok I REALLY NEED HELP!!

I resently upgraded to ubuntu 9.10 and did not like it I NEED to go back to 9.04

I still want all my programs and documents..

I have no Backups or any thing....

---

### Post by privatejarhead on 2009-09-10
since you've installed 9.10 over 9.04 and you didnt make any backups, you almost cannot get your data back

i say almost because when 9.10 (or an other os for that matter) installed, it didnt delete every last thing on your hard drive. instead, it will keep the files there until it needs more disk space for other files (hence it will overwrite the old information). now, i dont know personally how to recover the data on your hard drive, but there are a good number of data recovery gurus that seek out these sort of threads, so just wait a day or two and somebody is bound to help you out more than i have.

all i can advise you to do at this point is to STOP USING SAID COMPUTER IMMEDIATELY! the more you use it, the more overwriting will take place, thus more data lost. just shut down the computer in question, use a different computer to check the forums for answers, and if all else fails, do not be afraid to take your machine to a computer repair shop. granted, you will have to pay them (maybe a lot), but if the data on your hard drive is valuable to you, you should get someone who knows how to retrieve data.

---

### Post by privatejarhead on 2009-09-10
also, not all 100% of your data can be recovered. apart from overwriting the hard drive, some of the data might be corrupted by the install. do not touch anything until you get better help than i can provide

---

### Post by mbrush on 2009-09-10
Assuming you didn't wipe the drive and actually did an upgrade, you should be able to salvage most of it.

Export the installed packages: 

dpkg --get-selections > ~/packages.list

Copy your home directory somewhere temporarily.

Backup whatever else you think might be important.

Then reinstall 9.04, copy your home directory back over, import the package list (--set-selections i believe), and copy in your config files.

There are lots of things that might not work straight away, or at all, but you should be able to get it roughly back to the way it was after some toying around.

Just backup any files you are going to copy over on the 9.04 to make sure you can restore them.

Good luck.

---

### Post by raymondh on 2009-09-10
I have used [apton CD]("http://aptoncd.sourceforge.net/") to transfer apps and repos _from 9.04 to same 9.04_.  ***I have never used/tried with different version transfers***.  You may want to research further.

In the meantime, I would (at least) start backing-up personal data and files you have in Karmic..... just in case a clean re-install of 9.04 is inevitable.  This is assuming that current Karmic is working.

Good luck.

---

