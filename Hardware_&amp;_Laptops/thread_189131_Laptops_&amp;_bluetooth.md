---
title: "Laptops &amp; bluetooth"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by kreso on 2006-06-04
Hi, I own a HP nx8220 laptop which has an integrated bluetooth adapter. Can anyone tell me how I can use it to transfer files between my cell phone? I've tried running some bluetooth programs but with no luck. the computer doesnt see any devices nor does the cell phone see any active devices.

---

### Post by toorima on 2006-06-04
Gnome bluetooth manager have never been very good but kde's worked very well for me and others in breezy, haven't tried it in dapper yet but this thread could be helpfull [http://ubuntuforums.org/showthread.php?t=75978](http://ubuntuforums.org/showthread.php?t=75978)

---

### Post by kreso on 2006-06-05
yes, I've read that topic and no luck :(

I think the problem is in the fact that my bluetooth adapter is integrated into the laptop?

---

### Post by toorima on 2006-06-05
So is mine, have a dell inspiron 8600 and have no problem with bluetooth
What problems do you have?

---

### Post by kronepils on 2006-06-05
Have you tried to scan for devices with "hcitool scan" in a terminal?

It should list all visible devices, and also tell you if it doesn't recognise your bluetooth adaptor.

Stupid question: Have you made sure your phones bluetooth is visible??


Good luck!

---

### Post by kreso on 2006-06-06
ofcourse I've turned bluetooth on the phone on :P

here's the output:

kreso@laptop:~$ sudo -s
Password:
root@laptop:~# hcitool scan
Device is not available: No such device
root@laptop:~#

---

### Post by kreso on 2006-06-06
Well, I've finally figured out what the problem was, this is one of those things that should enter a FAQ or something :)

on windows, on my laptop, HP provides a "HP Wireless Assistant" program in which you can disable /enable wifi and bluetooth, and apparently, when you disable it, you literely power it down ](*,)  
So, if you've disabled bluetooth or wifi for that matter in that program, it will not be recognized in linux.

BTW: Congrats to the ubuntu development team for a great release!

---

### Post by Jason_25 on 2006-06-06
Konqueror works great for bluetooth on KDE, but if you don't want to install the KDE stuff on gnome, you can use obexftp at the command line.

---

