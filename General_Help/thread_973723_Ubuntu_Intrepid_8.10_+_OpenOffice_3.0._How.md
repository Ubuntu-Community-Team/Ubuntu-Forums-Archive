---
title: "Ubuntu Intrepid 8.10 + OpenOffice 3.0. How??"
date: 2008-11-07
forum: General Help
---

### Post by Roasted on 2008-11-07
I downloaded OpenOffice 3.0 for Ubuntu Intrepid 8.10 64 bit.

I CD'd into the directory and ran the dpkg command as instructed.

This is what I get.

```
jason@jason-intrepid:~/Desktop/OpenOffice3/DEBS$ sudo dpkg -i *.deb
dpkg: error processing ooobasis3.0-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-binfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-calc_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-core01_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-core02_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-core03_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-core04_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-core05_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-core06_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-core07_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-draw_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-binfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-calc_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-draw_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-help_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-impress_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-math_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-res_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-en-us-writer_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-gnome-integration_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-graphicfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-images_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-impress_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-javafilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-kde-integration_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-math_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-onlineupdate_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-ooofonts_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-ooolinguistic_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-pyuno_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-testtool_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-writer_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.0-xsltfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-calc_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-dict-en_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-dict-es_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-dict-fr_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-draw_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-en-us_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-impress_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-math_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-writer_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org-ure_1.4.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 ooobasis3.0-base_3.0.0-9_i386.deb
 ooobasis3.0-binfilter_3.0.0-9_i386.deb
 ooobasis3.0-calc_3.0.0-9_i386.deb
 ooobasis3.0-core01_3.0.0-9_i386.deb
 ooobasis3.0-core02_3.0.0-9_i386.deb
 ooobasis3.0-core03_3.0.0-9_i386.deb
 ooobasis3.0-core04_3.0.0-9_i386.deb
 ooobasis3.0-core05_3.0.0-9_i386.deb
 ooobasis3.0-core06_3.0.0-9_i386.deb
 ooobasis3.0-core07_3.0.0-9_i386.deb
 ooobasis3.0-draw_3.0.0-9_i386.deb
 ooobasis3.0-en-us_3.0.0-9_i386.deb
 ooobasis3.0-en-us-base_3.0.0-9_i386.deb
 ooobasis3.0-en-us-binfilter_3.0.0-9_i386.deb
 ooobasis3.0-en-us-calc_3.0.0-9_i386.deb
 ooobasis3.0-en-us-draw_3.0.0-9_i386.deb
 ooobasis3.0-en-us-help_3.0.0-9_i386.deb
 ooobasis3.0-en-us-impress_3.0.0-9_i386.deb
 ooobasis3.0-en-us-math_3.0.0-9_i386.deb
 ooobasis3.0-en-us-res_3.0.0-9_i386.deb
 ooobasis3.0-en-us-writer_3.0.0-9_i386.deb
 ooobasis3.0-gnome-integration_3.0.0-9_i386.deb
 ooobasis3.0-graphicfilter_3.0.0-9_i386.deb
 ooobasis3.0-images_3.0.0-9_i386.deb
 ooobasis3.0-impress_3.0.0-9_i386.deb
 ooobasis3.0-javafilter_3.0.0-9_i386.deb
 ooobasis3.0-kde-integration_3.0.0-9_i386.deb
 ooobasis3.0-math_3.0.0-9_i386.deb
 ooobasis3.0-onlineupdate_3.0.0-9_i386.deb
 ooobasis3.0-ooofonts_3.0.0-9_i386.deb
 ooobasis3.0-ooolinguistic_3.0.0-9_i386.deb
 ooobasis3.0-pyuno_3.0.0-9_i386.deb
 ooobasis3.0-testtool_3.0.0-9_i386.deb
 ooobasis3.0-writer_3.0.0-9_i386.deb
 ooobasis3.0-xsltfilter_3.0.0-9_i386.deb
 openoffice.org3_3.0.0-9_i386.deb
 openoffice.org3-base_3.0.0-9_i386.deb
 openoffice.org3-calc_3.0.0-9_i386.deb
 openoffice.org3-dict-en_3.0.0-9_i386.deb
 openoffice.org3-dict-es_3.0.0-9_i386.deb
 openoffice.org3-dict-fr_3.0.0-9_i386.deb
 openoffice.org3-draw_3.0.0-9_i386.deb
 openoffice.org3-en-us_3.0.0-9_i386.deb
 openoffice.org3-impress_3.0.0-9_i386.deb
 openoffice.org3-math_3.0.0-9_i386.deb
 openoffice.org3-writer_3.0.0-9_i386.deb
 openoffice.org-ure_1.4.0-9_i386.deb
jason@jason-intrepid:~/Desktop/OpenOffice3/DEBS$ 

```

---

### Post by lifestream on 2008-11-07
Grrr pleaze too yoose  zhe search!
[http://ubuntuforums.org/showthread.php?t=973655](http://ubuntuforums.org/showthread.php?t=973655)

BTW you got the wrong deb. maybe your pc is 34 bit, not 64.

---

### Post by Roasted on 2008-11-07
Excuse me for not having found what I was looking for in the search and resorting to participating in the Ubuntu community by adding a thread. The search function is the first thing I always check, yet nothing related to what I was experiencing showed up in search. Kthx.

---

### Post by Yellow Pasque on 2008-11-07
> I downloaded OpenOffice 3.0 for Ubuntu Intrepid 8.10 64 bit.
You clearly downloaded a 32-bit .deb
Try: [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

---

### Post by Roasted on 2008-11-07
> **Temüjin said:**
> You clearly downloaded a 32-bit .deb
Try: [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

Man. I suck. I didn't realize that. I just clicked on the deb file they had on the site... Didn't even take notice.

Thanks for the info guys. I'll tackle it in the morning. I'm typing this from my Vista laptop as a zombie. The energy required for me to get up to my desktop and try these methods out are entirely too much to ask of me at this time. Have a good one.

---

