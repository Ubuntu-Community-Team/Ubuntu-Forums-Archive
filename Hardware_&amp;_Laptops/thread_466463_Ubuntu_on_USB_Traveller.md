---
title: "Ubuntu on USB Traveller"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by C.S.Cameron on 2007-06-06
Installed Ubuntu 7.04 on a Kingston Traveler 4G.
Upgraded the files, Set Google as my homepage, set up my Gmail account as a bookmark, Installed Skype and logged in.
After loading every program that looked like it might be useful and many that were default, still have a gig and a half of disk space.
I have tried the dongle on every computer in the house. 
It is like having a portable operating system with all my personal stuff installed.
Sound worked on all computers, internet on the ones with wired connections, will look at wireless when it becomes a priority. 
The problem:
While on the living room computer, (Nvidia 7800), I installed the Nvidia drivers.
This worked great on that computer , and the HDTV looked great, but when I plugged it into my office computer that uses a 8800GTS card, I got X failure.
I took it back upstairs, disabled Nvidia in the Restricted Manager and it worked fine, even in the office, until,
I tried loading up on the 8800 computer what Nvidia referred as 'Graphics Drivers, 8800, Linux X86',  the 9755 build.
Then everything  went bad, Tried everything, ended up re-formating the dongle and reinstalling.
Everything seems to work great and is very fast, except no duel monitor in the office.
Has anyone been able to get a 8800 card working with Ubuntu? Does anyone know a way to temporarily disable it when plugging into a generic computer?
Thanks
Cork

---

### Post by t4thfavor on 2007-06-08
There is a command that enables the Nvidia driver, I am sure there is a command to disable it. If so you could add that command to one of you shutdown scripts so that it is unloaded every time. 
I don't know what the command is, nor do I know where the shutdown scripts are. But a quick google search should be all you need.

---

### Post by C.S.Cameron on 2007-06-08
Thanks for the reply.
I think I have to reboot to install it so not sure how uninstalling it on shut down would work.
I was wondering about something like a duel boot, where I could just say NO (to Nvidia or yes to ATI).
It is useful having a portable O/S, but would be better if it could handle all the hardware on the most common boxes I plug it into.

---

### Post by t4thfavor on 2007-06-09
Im not talking abou t uninstalling it, I am just talking about disabeling it. As in sudo nvcontrol disable (Not the actual command, but something similar). I know I have to issue some command after installing to enable the nvidia driver. Maybe   "nvidia-settings" or something like that.

(Not recommended)
Other than that you could grep your startup sripts for lines containing Nvidia and see what you can comment out so that it doesnt start on boot.

---

