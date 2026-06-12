---
title: "Issues with external USB drive"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by TK2e on 2009-02-24
I have been using my laptop for a while with dualbooting Ubuntu 8.10 and WinXP, though mostly using Ubuntu. Due to various circumstances I have been using WinXP for a couple of weeks only. Last weekend I went back to Ubuntu and updated all packages. After this; ISSUES :mad:

I am using an external drive with FAT32, which can be mounted as usually. Then:
- When I am accessing my external USB HDD, Nautilus may suddenly lock and will not be forced quit.
- When Nautilus hangs, no other Nautilus can be started. If one try, this process will hang as well.
- When trying to start Konquerer, nothing happens. When accessing processes, one can see it is "hanging".
- When trying to start Amarok, nothing happens. Same as Konquerer. All my mp3's are on the external drive.
- All of the above errors "requires" the laptop to be restarted to be able to use Ubuntu properly again.

Any other experiencing these problems?
Any suggestions?

TIA

---

### Post by Pumalite on 2009-02-24
Where is XP?
Where is Ubuntu?
Where is Grub?

---

### Post by TK2e on 2009-02-24
XP is in the laptop.
XP Program Files and main part of Windows applications installed is on USB HDD.
Ubuntu and Linux applications are on laptop.
GRUB is on laptop.

------
Adopt, Adapt and Improve

---

### Post by Pumalite on 2009-02-24
Check your external drive:
TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by TK2e on 2009-02-24
Isn't TestDisk only for recovering bootable disks? Both my OS' are on the internal HDD. WinApps and other files are on the external HDD.

My suspicion as the why Konquerer is not starting up, is that I have accessed the external HDD last, then K. was used the last time.
Amarok may not start, due to mp3 library is set to external HDD.
Why Nautilus starts fine and the develop issues with the external HDD puzzles me.
WinApps are running fine from the external HDD in WinXP.
Has there been an update to the file system drivers lately, which could cause this problem?

----------
Adopt, Adapt and Improve

---

### Post by TK2e on 2009-02-24
Just made some test in Windows on the external HDD. Seems there's some consistency problem, which cannot be solved, so I have to move the files to other locations to do a format of the drive.

Booted into Ubuntu without the external drive attached. This made Konquerer and Amarok start up. Konquerer with an error message, due to the fact, that the external drive had been accessed before the latest shutdown of K.

Sorry for the horn blowing, but at least I received some hints here.
Thanks for the assistance

----
Contingency plans? What contingency plans?

---

