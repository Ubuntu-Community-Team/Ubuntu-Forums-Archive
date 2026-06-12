---
title: "mptbase: ioc0: error on dell poweredge"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by mrweirdo on 2006-05-29
I just scored a free dell poweredge 1400 dual 800mhz p3 SCSI system however I am having problems with ubuntu on it cuasing the system to hang during boot up right when it starts to load the kernel.  I'm using Breezy and it hapens both when i boot the origonal install cd as well as the install I have running on my system. 

The error message right after booting the kernel is as follows:
Mptbase: ioc0:  error - wait ioc_ready state timeout(15)!
Then it just sits there for quite some time and eventualy resumes the booting process with no errors after this one. Anyone know why it might be doing that and how I can get rid of the error? Its realy more of a major annoyance more then anything as it causes the system to take for ages during boot or a restart.

---

### Post by Ptero-4 on 2006-05-29
It seems like something is not being initialized quick enough and ubuntu have to wait a lot, you may try to find this "mptbase" and reduce it's timeout to something lower so that your system doesn't wait so much for something that in the end doesn't seem to be causing major issues.

---

### Post by mrweirdo on 2006-05-30
ah I know whats causing it now. Its the HP DAT 72 SCSI tape drive. Seems to be it trys to read a tape during boot for some reason and if it doesnt find one in the drive that error shows up.

---

