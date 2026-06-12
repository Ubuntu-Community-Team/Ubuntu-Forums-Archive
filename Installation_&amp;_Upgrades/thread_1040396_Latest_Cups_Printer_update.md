---
title: "Latest Cups Printer update"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Felicity_X on 2009-01-15
I have had my Ubuntu system around nine months and am absolutely delighted with it. :P All the system upgrades have gone like clockwork, no problem, until today> :(

A set of patches to the cups printer system came through.  The system made an error while trying to reset up zdesktop, producing the following error:

E: zdesktop: subprocess post installation script returned error exit status 1.

When update had finished only the cups common files patch was left on the list, so I tried to download it again with exactly the same results except that the patch was removed from the download list, which I presume means that it has not loaded and is no longer available for download.

Is there anything I can do about this?  Was this a glitch in the software, or something with my system?

Can someone help, please? :confused:

THIS IS NOW SOLVED

Thank you very much Partyboi2

---

### Post by Partyboi2 on 2009-01-16
Can you please open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by markskerr on 2009-01-17
I am also having the exact same problem. After running the update manager from the terminal here is the error that was retuned:

/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:1: parser error : Document is empty

The extended_cl.xml is on my system but it is empty which is causing the problem.

Thanks for any help

Mark:)

---

