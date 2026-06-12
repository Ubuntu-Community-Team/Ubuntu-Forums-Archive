---
title: "Reinstall HP printer not found"
date: 2009-05-21
forum: Hardware
---

### Post by lindsay7 on 2009-05-21
I had to reinstall Ubuntu 9.04 and now my HP882 deskjet is not seen in the printer set up under system/administration/printing.  When I type lsusb in the terminal the printer is shown, but it can not be found when I try to set it up.  Can someone help me with this?

---

### Post by lindsay7 on 2009-05-21
I tried to run hplip-3.9.4b.run and I am getting this error message.

Can anyone point me in the right direction to get this printer to work.

error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
stevepoulton@stevepoulton-desktop:~/Desktop$

---

### Post by 11hjpphty76lkjj on 2009-05-24
In the install directory (for example: ~/hplip-3.9.4b) there is a install .log file.

Please post the log.

Thanks.

Aaron

---

### Post by lindsay7 on 2009-05-26
Hi, thank you for the reply. I am out of town for a few days and when I get back I will get to that computer and post the response.

I appreciate your interest in helping.

---

### Post by lindsay7 on 2009-05-27
I looked at my drive and no info was there in the log. I fix the problem I had reinstalled Ubuntu. I think the problem was caused by Remastersys which was the system that was on my computer and (because of another reinstall from this backup) or at least thats when it showed up. I trid reinstalling the OS from my wife's Remastersys disk and one from my computer and the same problem with the printer not being recognized existed. I could see the printer when I typed lsusb but the printing function under system/administration/printing just would not find the printer at all.

---

