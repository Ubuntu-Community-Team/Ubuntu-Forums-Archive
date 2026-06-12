---
title: "Need help with install, please help!!!!"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by joek71 on 2009-06-21
Hi Guys

I am having a problem installing Ubuntu:
I get his error:
11.858728 Firmware Bug: Power Now K-8 
Your BIOS does not provide ACPI_PSS

I am running Opteron 175 with DFI MotherBoard(NF4-Expert) With 2 Gigs of RAM(OCZ)

Please help me install this, thanks.

---

### Post by presence1960 on 2009-06-21
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If those options don't work try the text based alternate installer. get it here : [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Sef on 2009-06-21
The alternate cd is easy to use.   It has an easy to use command line install; however, doing a manual install would take some patience.   If you wanted to use the whole disk, it would be easy to use.

---

### Post by joek71 on 2009-06-22
Thank you guys, for your help.  Is this a bug? Will Ubuntu fix this issue?

---

### Post by joek71 on 2009-06-22
how about if i am installing it within windows? cause i have vista running now and want both systems.

---

### Post by presence1960 on 2009-06-22
if you are installing it from within windows you will use wubi. just insert the ubuntu Live CD while windows is running and follow the directions. In my opinion an install to a partition is much better, but that is your choice. Two pitfalls of wubi are once you set the size of Ubuntu that's it and performance of wubi is degraded by windows fragmentation. See here: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)  for a tutorial with screenshots of installing via wubi. Note just below #11 about the possible performance degradation due to Windows fragmentation.

---

### Post by joek71 on 2009-06-22
No if i install it from the disk, but i dont want to loose WINDOW how can i do this?

---

### Post by Sef on 2009-06-22
> No if i install it from the disk, but i dont want to loose WINDOW how can i do this?


You can dual boot.  Read the [Illustrated Dual Boot]("http://members.iinet.net/%7Eherman546/index.html").

---

### Post by raymondh on 2009-06-22
or this

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

