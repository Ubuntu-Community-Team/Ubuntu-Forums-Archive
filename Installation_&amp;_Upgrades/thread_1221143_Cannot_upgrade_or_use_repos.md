---
title: "Cannot upgrade or use repos"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by i-like-knives on 2009-07-23
I have tried to apply several changes today, and I keep getting the following errors, can someone please help? Thanks much
I am using Gutsy, and would like to upgrade to a newer version,,,not to mention able to use synaptic.
--------------------------------------

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009b-0ubuntu0.7.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009b-0ubuntu0.7.10_all.deb)
  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.4_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.2.1-1ubuntu4.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.2.1-1ubuntu4.4_all.deb)
  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.2.1-1ubuntu4.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.2.1-1ubuntu4.4_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.4_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

---

### Post by cariboo on 2009-07-23
THe end of life for Gutsy was April 18/09, so the repos have been closed. Try pressing Alt-F2 and typing:

```
gksu update-manager -d
```

If you want to upgrade to the current version you will have to do it in steps 7.10-->8.04-->8.10-->9.04.

---

### Post by drs305 on 2009-07-23
Here is the End of Life (EOL) guide for upgrading releases.
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

It's for Ubuntu. I don't know if Kubuntu has a similar page. You could do the upgrade to Hardy and then install the kde desktop if you don't find anything else.

---

### Post by Bucky Ball on 2009-07-23
I would save all your data and install afresh. Going in steps is going to be a never-ending nightmare.

8.04 LTS for super stability, varying degrees of stability for anything higher. :)

---

### Post by Bucky Ball on 2009-07-23
Firefox bookmarks can be saved by going to:

Bookmarks->Organise Bookmarks->Import and Backup 

... or by right clicking on folder in there and saving them individually.

8.04 LTS can be got from here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Get the appropriate version for your machine. Make an ISO with Brasero (pretty sure that was in 7.10) and boot from that.

If you are into torrenting, which is faster and more reliable, you can get the appropriate one from here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Good luck. :)


* ps: I started doodling with 7.04 originally. I think you're are going to like 8.04 (and beyond). Would be interesting to hear what you think.
* pps: If you have trouble with the Desktop ISO, try the Alternate - i386 is for all machine that aren't 64bit and AMD 64 is for all machines that are (this is regardless of AMD/Intel processor).

---

### Post by slakkie on 2009-07-30
> **drs305 said:**
> Here is the End of Life (EOL) guide for upgrading releases.
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

It's for Ubuntu. I don't know if Kubuntu has a similar page. You could do the upgrade to Hardy and then install the kde desktop if you don't find anything else.

Actually this is for all Ubuntu flavors.

---

