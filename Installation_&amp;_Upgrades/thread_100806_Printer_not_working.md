---
title: "Printer not working"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by sitara on 2005-12-08
I have recently installed Kubuntu (Breezy) in place of Xandros. I added my printer (HP PSC500) and everything looked fine. I didn't print a test page because I felt quite sure it would work in Kubuntu as it had in Xandros (with the same HPIJS driver). 

I have two problems:

1) I installed HPOJ and tried to run /etc/rc2.d/s19hpoj as root (tried both sudo and logging on as root) to get the scanner part of the 'all-in-one' working. The setup program failed, with a message saying that PTAL-MLCD failed to start. The syslog says that there is an authentication problem with PTAL-MLCD. 

2) I set the printer up as shared, and eventually managed to add it to another Kubuntu system on my home network (quite a mission compared with Xandros and Linspire). I tried to print a test page. It gets through to the queue on the host system, but doesn't print. Only then did I try to print a test page from the host system. It doesn't print either. The printer says it is 'stopped', but it won't restart. I tried restarting the CUPS server from the KDE control centre, but it says there is no CUPS server running. I restarted it from the terminal and it restarts OK.

Any suggestions would be welcome.

Thanks in advance 

Keith

---

### Post by daller on 2005-12-30
This Is A Dublicate! - See this instead: [http://ubuntuforums.org/showthread.php?t=100807](http://ubuntuforums.org/showthread.php?t=100807)

---

### Post by sitara on 2006-01-06
Hi Daller, I know it's a dublicate - I posted both problems. I have searched for the problem in the forums and tried all the suggestions I found, without success. It's been about a month now and I still don't have my printer working properly, that's why I've posted a copuple of times. I have used the printer/scanner successfully with Suse, Xandros and Linspire, but can't even get printing working without intervention with Kubuntu. It's kind of critical because I use it for my business.

The first hurdle seems to be that the printer has the wrong owner/permissions. The user is root and the group is lp. If I chmod ugo=rw /dev/lp0  then the printer works until I reboot. The problem is that I have staff using the printer, who (quite rightly) don't know what a command line is, so if I'm not around, no printing gets done.

I don't know where to fix the printer permissions permanently, or what the correct permissions are. I would appreciate some help with that.

Keith

---

### Post by daller on 2006-01-06
[QUOTE=sitara]Hi Daller, I know it's a dublicate - I posted both problems. I have searched for the problem in the forums and tried all the suggestions I found, without success. It's been about a month now and I still don't have my printer working properly, that's why I've posted a copuple of times. I have used the printer/scanner successfully with Suse, Xandros and Linspire, but can't even get printing working without intervention with Kubuntu. It's kind of critical because I use it for my business.

The first hurdle seems to be that the printer has the wrong owner/permissions. The user is root and the group is lp. If I chmod ugo=rw /dev/lp0  then the printer works until I reboot. The problem is that I have staff using the printer, who (quite rightly) don't know what a command line is, so if I'm not around, no printing gets done.

I don't know where to fix the printer permissions permanently, or what the correct permissions are. I would appreciate some help with that.

Keith[/QUOTE]

This is an ugly workaround, but you could add the command to this file:

/etc/init.d/bootmisc.sh

(At the end of the file, just a line above the ": exit 0"-line)

Good luck!

---

