---
title: "Xsane/scanner working with 5.04 but not with 5.10"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by red_Marvin on 2005-11-26
(I moved this topic from desktop support)
The scanner is an Agfa Snapscan e50 and worked flawlessly with 5.04 but
in 5.10 xsane returns an error when I start it:

Couldn't open unit 'snapscan:libusb:001:003' wrong argument.

(translated froms Swedish)
Any suggestions?

---

### Post by _4ace on 2005-11-26
try typing 

sane-find-scanner

and then

scanimage -L

don't know too much about this but it worked for me.

---

### Post by red_Marvin on 2005-11-30
I was going to write a long story on how stuff didn't work, and while I while doing
that I tinkered a little with stuff, searched google etc.
After some more tinkering I found that I missed a snape50.bin (driver?/firmware?)
and that I needed a path to it in the /etc/sane.d/snapscan.conf. The bin file was 
found on the winstallation cd and the problem was solved :D .
I am currently keeping the file in /etc/sane.d, is there any other place that is
more "standardizationally appropirate" to keep it? /usr/share?

---

### Post by dyrer on 2006-11-29
my HP 5300c is supported and recognized by Sane, but preview is working and scan freeze my scanner

---

