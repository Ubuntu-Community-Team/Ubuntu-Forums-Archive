---
title: "Brother dpc-140W query"
date: 2013-02-14
forum: Hardware
---

### Post by erikja on 2013-02-14
Hi.
I have a Brither dpc-140W printer.

Can it print wireless in Ubuntu ?. Ubuntu 12.04 LTS 32bit.

/Erik

---

### Post by kurt18947 on 2013-02-14
I'm pretty sure the script available here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

will be helpful if you're familiar with the terminal and BASH scripts.  If not, post back and I'll try to help.  Installing the scanner is less automated, especially if you're using a 64 bit O.S.  The scanner driver is a .deb file that can be installed like any other but there are two issues not addressed by the installer.  One is that only SUDO users can scan by default, the other is that the installer places certain files in the wrong place. Both problems are addressed in the scanner FAQ

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html)

These are the issues I've run into.

---

