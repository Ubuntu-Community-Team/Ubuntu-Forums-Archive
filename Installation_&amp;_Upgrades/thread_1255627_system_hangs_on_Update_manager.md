---
title: "system hangs on Update manager"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by Terrywho on 2009-09-01
Hello to ubuntu forums;
I just installed ubuntu studio 9.04 (jaunty) on my Dell Inspiron E1705 (1GB RAM, 160 GB HD).  I downloaded the install DVD from the Ubuntu Studio web site and burned the DVD on my fedora 11 system.  The installation went great, then the first time I logged on, the package manager notified me that I had 233 files of software updates, so I clicked on the Install Updates button.  The small window "Downloading Package Files" appeared, the first file downloaded ok but on "Downloading file 2 of 233" the entire system just hung.  No mouse and keyboard does not respond.  I powered the system off and tried again with the same result.  I tried "sudo apt-get upgrade" from a terminal but that just popped another Update Manager window that also hung.
Any help would be greatly appreciated,  Thank you

---

### Post by Partyboi2 on 2009-09-01
Hi, try changing your download server in Software Sources (System>Admin>Software Sources) to another one then reload the package list and try updating again.

---

### Post by Terrywho on 2009-09-01
Thank you Partyboi2,
I was able to get through the 233 files by changing the server, although the system still hung about 6 or 7 times to get all 233 files.  Fortunately the update manager saved its progress so that when I had to power down start again, the update manager began where it had left off.

Thanks

---

