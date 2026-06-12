---
title: "Installing Ubuntu- 0% resizing partition"
date: 2008-08-25
forum: General Help
---

### Post by clockwork9 on 2008-08-25
I am installing Ubuntu 8.04 on my Dell laptop and got to the step where you resize the partition. On that step i chose to give 100gb to my windows vista installation and 20gb to Ubuntu. After i clicked forward it got stuck on 0% complete and has been that way for the last hour or so. I did Checkdisk and defragmented windows before i tried this.

Computer: 
Dell Inspirion e1505
1.87ghz Intel duo core processor
2gb Ram
ATI 128mb mobility radeon graphics card
120gb hard drive
Windows Vista Home premium

---

### Post by abazoskib on 2008-08-25
thatas exactly what happened to me, so I actually installed a version of ubuntu from years ago(not the smartest move IMO) but eventually I upgraded all the way to heron. maybe you can install the previous version of ubuntu(7 i believe) and then upgrade using the upgrade manager to 8.

---

### Post by clockwork9 on 2008-08-25
thanks ill try that- i have an old laptop which i put an old 6 version on because the gui would crash on anything higher than that

---

### Post by Jonie on 2008-08-25
There are some issues with GParted, you may try to resize from command line, look for further info at:

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.CLIPartitioning]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.CLIPartitioning")

Be warned, that if you move NTFS filesystem, its boot sector must be updated in order to continue booting from it. TestDisk has a functionality to do so. Simple resize doesn't require such procedure.

---

