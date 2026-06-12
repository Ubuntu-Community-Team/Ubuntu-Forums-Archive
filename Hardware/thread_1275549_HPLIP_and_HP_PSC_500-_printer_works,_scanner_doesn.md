---
title: "HPLIP and HP PSC 500- printer works, scanner doesn't."
date: 2009-09-25
forum: Hardware
---

### Post by murderslastcrow on 2009-09-25
So, been using this HP PSC 500 to print for a while now, but the scanning won't work. Thing is, this scanner is one of those old parallel port all-in-ones from HP, but not so old it won't work. I've seen people being able to get it to work by using modprob ppdev, enabling Parallel Ports with the HPLIP installer, etc.

Problem is, I can't seem to use Parallel Ports at all. It doesn't ask me in the HPLIP installer, whether automatic or custom, to enable them (pp-build=yes/no). Just doesn't ask.

It's kind of obnoxious. I don't even think root has access to the scanner or parallel ports. So if anyone could help me to get them enabled, or get the printing going, that'd be great.

P.S. Already installed the libsane-extras package, too. No good. Been using XSane to test for it, and it never detects any devices. Thanks in advance for your help.

---

### Post by murderslastcrow on 2009-10-03
Well, reverting to hpoj and uninstalling HPLIP seems to have solved the scanner problems by providing the 'legacy' parallel port support.

However, I can't seem to get the printer to work. XD It constantly says Stopped in the Printer State section of the printer's preferences. Backend does not exist? I'll have to look into this further. I'll come back here with updates, and if anyone has a suggestion, please leave a message.

---

### Post by hansdown on 2009-10-03
Hi murderslastcrow.

Do you have```
 xsane
``` installed?

---

### Post by hbbliss on 2009-10-16
You have to do a manual install of hplip to be able to specify parallel ports. See the detailed instructions at the web site. Be sure and use the slider at the dependencies step to ensure that all is specified. Same for the configure step. In this case add --enable-pp-build to the command line before executing. After a successful compile and install you can run hp-setup in a command line and you will get a page where you can click on the parallel button and then proceed. For some reason Xsane treats a parallel scanner as only accessible as root. See if the scanner appears when you do a sudo xsane.

---

