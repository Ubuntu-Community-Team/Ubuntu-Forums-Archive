---
title: "Suspend to Ram, Sony SZ330 6.10"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by leadweight on 2006-12-19
Can anyone tell me how to make a Sony SZ330 suspend to ram?  My machine appears to suspend to ram, but will not wake up.  Suspend to disk works, but it is very slow to wake up, might as well shut down and reboot.  Running Ubuntu 6.10.  Unfortunately, this is a show stopper.  This machine has dual video, both Nvidia Go 7400 and Intel, but the problem is the same with either video.

---

### Post by nmincone on 2006-12-19
STF for some additional info, there is much posted on this topic already.

---

### Post by leadweight on 2006-12-19
> **nmincone said:**
> STF for some additional info, there is much posted on this topic already.

I know how to use he search button, thank you.  There is some stuff dealing with Dapper, not 6.10.  Some of it links into bug reports with no further explanation.  Perhaps someone would be kind enough to tell me what works.

---

### Post by locks on 2006-12-19
I have a sony SZ28GP, older Australian spec of you machine (Core duo 2GHz, T2500).  Cant really help you out too much, apart from mentioning some of my observations.
- Suspend to ram and Hibernate both work fine for me (most of the time...)
    -Neither work if I have the wireless switched _off_
    -Am using the intel graphics card (havent setup Nvidia for Linux yet)
    -Running Edgy 6.10

I seem to remember reading something about windows being hibernated in the back ground may also cause issues.
Maybe updating to the latest Nvidia driver would help?

---

### Post by nmincone on 2006-12-21
Everyone with suspend/hibernation problems, please see below, this might help.


[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
[How to suspend and hibernate a laptop under Linux]("http://www.linux.com/article.pl?sid=06/05/24/1716222")
[Laptop testing team wiki...]("https://wiki.ubuntu.com/LaptopTestingTeam/")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

---

### Post by leadweight on 2007-01-04
I have looked around at solutions for other laptops.  They are all so technical that I have no idea how anyone could have worked them out.  If this suspend 2 thing is so great, why does it have to be so hard to install?

I tried using Dapper.  It would go into S3 and come back up, but sometimes the wireless or sound would not work.

If it is any consolation to the developers, Suse 10.2 did not get it right either.

-Ron

---

