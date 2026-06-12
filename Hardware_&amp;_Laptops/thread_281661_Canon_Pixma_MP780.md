---
title: "Canon Pixma MP780"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by Abaddon on 2006-10-21
I've recently installed the Edgy RC, and tonight, I did a bit of chasing around to see if I could get my printer working.

I have a Canon Pixma MP780 Multifunction.  The scanning works well via XSane, but printing had been an issue - I've had the half-page bug that's been reported on the forum.

I managed to find [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/") this page, where a Japanese fellow has done some DIY'ing on the Canon drivers.

The files are all there, all .deb'ed up and ready to go.

My only issue with installing them in Edgy was that the pstocanonbj deb needs libcupsys2-gnutls10 which *isnt* available for Edgy, and broke my dependencies.  I fixed that with a simple sudo synaptic, and then booted my Dapper live CD, installed the libcupsys from the dapper Repos.

For some strange reason, apt-get -d wouldn't work for me, so I did it via Synaptic (make sure you go to Synaptic --> Settings --> Preferences --> Files --> Temporary Files and then click on "Leave Downloaded Files in the cache").

I then copied the deb onto my hard-drive, rebooted edgy, installed the libcupsys and then the pstocanonbj and hey presto!

So, in summary:

1.  Download the debs - libcnbj-2.5, bjfilter-2.5,  pstocanonbj from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian/")
2.  Download [libcupsys2-gnutls10]("http://packages.ubuntu.com/dapper/libs/libcupsys2-gnutls10") and install.
3.  Install libcupsys first, then the debs from step 1
4.  Admin --> Printing --> Add New Printer --> Select your printer
5.  Step two of the Printer wizard click on Install Driver
6.  /usr/share/cups/model/canonpixusip4100.ppd
7.  Happy Printing :KS

---

### Post by haggel on 2006-11-13
This worked for my Canon I950 as well.  Thanks!!!

---

### Post by thommo on 2007-03-07
hi there,
I have tried this, and it won't let me install the libcupsys2-gnutls10
I get:
Reading state information... Done
Note, selecting libcupsys2 instead of libcupsys2-gnutls10
libcupsys2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

any ideas?

---

### Post by K.B. on 2007-07-04
I also have this printer and the scanner drivers are working but I can't get printing under control and really don't want to pay for something like Turboprint.

Anyone found anything lately to get it working?

---

