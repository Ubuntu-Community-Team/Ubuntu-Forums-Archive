---
title: "error in upgrade !"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Gladiator-prog4me on 2009-07-06
hello 

i got this error  : 

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.40 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.



ubuntu 9.4

---

### Post by taurus on 2009-07-06
If you are running 9.04 (jaunty), how come you have repos for breezy?  

```
cat /etc/apt/sources.list
```

---

### Post by FWD on 2009-07-06
Hi, I upgraded from 8.04 to 8.10. I too received similar messages as Gladiator-prog4me. The "W: Failed to fetch [http://packages.freecontrib.org/ubun...zy/Release.gpg](http://packages.freecontrib.org/ubun...zy/Release.gpg) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out" error. Tho I can't say if the URL's were the same.

I am booting into BusyBox (initramfs). That suggests to me that it isn't seeing the HD ?!?

I think my main error was when prompted to remove/delete old/obsolete files, I replied yes. In the process, I believe that it shut down and deleted services needed for accessing the net. The prior upgrade I did, I replied no to removing/deleting obsolete files and the upgrade went smoothly.

At this point, I found this link:

[http://www200.pair.com/mecham/spam/waiting_for_root_file_system.html](http://www200.pair.com/mecham/spam/waiting_for_root_file_system.html) 

and am going to follow at least some of the steps outlined there.

I will also be looking at this link:

[https://wiki.bnl.gov/dayabay/index.php?title=Offline_Software_Installation_on_Ubuntu_8.10%2C_Intrepid_Ibex](https://wiki.bnl.gov/dayabay/index.php?title=Offline_Software_Installation_on_Ubuntu_8.10%2C_Intrepid_Ibex)

and see where that gets me.

I feel that part of the problem could be that I am using an older system.

It is an:

ASUS MB, 900Mhz AMD Athlon, with Promise ATA 100

The Promise is plugged in as an after thought (so it seems)as when booting, after the BIOS process, it then goes to the Promise and searches for any drives attached thereto.

In closing, I think that when upgrading, one should NOT delete/remove Old/Obsolete files. There are apps out there that can do it at a later date if space is needed.

That's all for now. Will get back when and if I resolve the problem.


FWD

Mosher's Law of Software Engineering:
   Don't worry if it doesn't work right.  If everything did,
   you'd be out of a job.

---

