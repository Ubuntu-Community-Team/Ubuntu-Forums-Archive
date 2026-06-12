---
title: "Dialup modem installation"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by mass_ga on 2006-01-10
I installed Ubuntu-Linux and I have configured the dialup modem Agere AC '97 and its driver (I think so!). I have tried to use Wvdialconf to set up the dialup connection and some errors occurred. The modem works but the procedure stops because authentication fails. I am absolutely sure that username and password are correct. Have you some suggestions? Thanks a lot. :p :p 

Max

---

### Post by chakra_dude on 2006-01-10
i got the same problem. help anyone?

---

### Post by Sef on 2006-01-10
I found this post on linuxquestions.org site (slackware forum):  > Please test the alternate ltmodem-2.6.-alk-b1.tar.gz at [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) or the  ltmodem-2.6-alk-7b1.tar.gz which has the same core code.

Link to post: [http://archives.linmodems.org/20799]("http://archives.linmodems.org/20799")

Link to source code: [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/]("http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/")

How it was installed (on slackware): > As promised, here's my report: I 
- downloaded the source, shepperd had pointed me to,
- ran make in the directory that was contained in the archive file
- copied the *.ko files into a newly created directory /lib/modules/2.6.13/other
- loaded the module with #modprobe ltserial
- plugged the modem cable to my laptop
- created a softlink /dev/modem pointing to device file /dev/ttyLTMS0
- added the modem to my KPPP configuration
- dialed into my ISP

In short: SUCCESS without a single problem!

Thank you all, and shepperd in particular!

Link to Howto: [http://www.linuxquestions.org/questions/showthread.php?t=375618](http://www.linuxquestions.org/questions/showthread.php?t=375618)

---

