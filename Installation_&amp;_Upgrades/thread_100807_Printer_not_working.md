---
title: "Printer not working"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by sitara on 2005-12-08
I have recently installed Kubuntu (Breezy) in place of Xandros. I added my printer (HP PSC500) and everything looked fine. I didn't print a test page because I felt quite sure it would work in Kubuntu as it had in Xandros (with the same HPIJS driver). 

I have two problems:

1) I installed HPOJ and tried to run /etc/rc2.d/s19hpoj as root (tried both sudo and logging on as root) to get the scanner part of the 'all-in-one' working. The setup program failed, with a message saying that PTAL-MLCD failed to start. The syslog says that there is an authentication problem with PTAL-MLCD. 

2) I set the printer up as shared, and eventually managed to add it to another Kubuntu system on my home network (quite a mission compared with Xandros and Linspire). I tried to print a test page. It gets through to the queue on the host system, but doesn't print. Only then did I try to print a test page from the host system. It doesn't print either. The printer says it is 'stopped', but it won't restart. I tried restarting the CUPS server from the KDE control centre, but it says there is no CUPS server running. I restarted it from the terminal and it restarts OK, but the printer still doesn't print.

Any suggestions would be welcome.

Thanks in advance 

Keith

---

### Post by Sef on 2005-12-30
To get the printer working, download the HPLIP driver and install it:

sudo apt-get install hplip

If that does not work, try this post:  [http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1600]("http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1600")
 
If the scanner isn't working, download libsane extras and install it:

Go to System ------->Administration --------> Synaptic Package Manager

Go to search, and type in lib-sane extras, click on it twice, and the apply button will light up.  Click on it and it will install.

---

### Post by sitara on 2006-01-02
Thanks for the input. I have been able to get the printer working, but seem to have a problem with permissions. The owner of /dev/lp0 is root and the group is 'lp'. Owner and group have write access, but others have no access. If I give others write access, the printer works. Problem is, every time I reboot, the permissions are reset.

I appreciate the help.

Keith

---

