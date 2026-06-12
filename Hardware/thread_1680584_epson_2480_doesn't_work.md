---
title: "epson 2480 doesn't work"
date: 2011-02-02
forum: Hardware
---

### Post by iparorratza on 2011-02-02
[SIZE=2]Hi, I am a new ubuntu user. I would appreciate you to help me running my epson perfection 2480 photo scanner in ubuntu 10.10. Error message when I open XSane: [COLOR=Red]Failed to open device 'snapscan:libusb:001:002':Invalid argument[COLOR=Black].[/COLOR][/COLOR]
Thank you in advance.[/SIZE]

---

### Post by markrayne on 2011-02-06
I am finding exactly the same problem - Ubuntu 10.04 and Epson 2480.  On the other hand XSANE finds my Canon N650U scanner without any difficulty if I plug the same USB cable into that instead. Just a shame the Canon scanner can't be used either under Linux because of the awful grinding noise bug (reported elsewhere) that gets it shortly after attempting to scan.  I thought I read that this "snapscan:libusb:001:002':Invalid argument bug" has been fixed, but that doesn't appear to be the case for the Epson 2480 scanner.

---

### Post by iparorratza on 2011-02-11
Thanks for answering. Mine it is a just XSane problem. I perfectly used my epson just befoore installing XSane. Take care.

---

### Post by giorgio_fornara on 2011-02-27
Did you try like this this thread?
[http://wwww.ubuntuforums.org/showthread.php?t=917383](http://wwww.ubuntuforums.org/showthread.php?t=917383)

No matter if it's for older Ubuntu revision.

For epson 2480 you will need Esfw41.bin file, insead.
You'll find it on the scanner's installation CD.

If you came from an update from previous Ubuntu revision to 10.04 simply copy this file from /usr/local.old/share/sane/snapscan/Esfw41.bin to /usr/local/share/sane/snapscan/Esfw41.bin

---

### Post by iparorratza on 2011-03-05
Thanks for answering giorgio, I will try that way.
I did not update from 10.04, I am a 10.10 rookie and I was able to scan with simplescan; Xsane, however, no luck.
Take care.

---

### Post by p999t on 2011-03-18
Have a look at the following which should give you a good start

[http://ubuntuforums.org/showthread.php?t=1384307&highlight=epson+2480](http://ubuntuforums.org/showthread.php?t=1384307&highlight=epson+2480)



Good Luck

Peter

---

### Post by iparorratza on 2011-12-31
I finally got xsane working, I was just a capital letter problem in esfw41.bin file. Be careful because this file in the driver cd is Esfw41.bin.
Thanks for answering

---

