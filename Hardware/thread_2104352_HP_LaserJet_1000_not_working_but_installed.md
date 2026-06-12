---
title: "HP LaserJet 1000 not working but installed"
date: 2013-01-12
forum: Hardware
---

### Post by Not install on 2013-01-12
hello I have managed to install the LaserJet 1000 HP printer in ubuntu but its still not printing I'm using ubuntu 12.04 lts from the live cd

I plugged in the printer Ubuntu picks up the printer says it need the plug in then proceeds to automatically downloads the plugin and asks me to accept the install which I have done The LaserJet 1000 clearly shows up in printers menu  shows up in printers 

then to test a page from the properties menu select test print page the printer sits there not processing

from with office print a page sit there just does not proceeds at all printer status stays at idle says processing for a second then back to idle 

look into printer jobs all printing jobs seems to be strangely  paused try to press continue printing trys to process for a brief second then back to pause as I watch the printing jobs screen

I'm sure I have the latest hplip installed by default in ubuntu 12.04 lts that's required for the laser jet 1000. Which is hplip 2.7.12 ubuntu lts hplip by default is higher than this version that requested by hplip to work with the version  and the driver plug in gets auto installed the moment I plug in my printer so I don't see this as a problem ether

so Ubuntu forums  what's going on here ?...

some one please have a fix solution to help me use my printer with injury


Many thanks for reading my post hopefully a solution is a simple solution look forward to hearing your suggestions and possible reason as to why this strange problem is occurring  as I'm currently enjoying using ubuntu as my main os and would like to keep using it as my main os

---

### Post by agillator on 2013-01-12
First, you installed ubuntu from the live cd; you are not trying to print from the live cd, right?

Second, how are you connecting your printer, usb or network?

When you print something it is added to the queue, so if an earlier print job has hung, everything else is waiting for that job to finish. When testing, be sure all previous jobs have completed or are cancelled and removed.

The latest version of HPLIP is 3.12.11. I would suggest going to the hplip site and downloading hp's version, purge Ubuntu's version, install the hp version and see if that helps. If not, give us the information I asked for above and we'll try to find out where the problem is.

---

### Post by Not install on 2013-01-13
> **agillator said:**
> First, you installed ubuntu from the live cd; you are not trying to print from the live cd, right?

Second, how are you connecting your printer, usb or network?

When you print something it is added to the queue, so if an earlier print job has hung, everything else is waiting for that job to finish. When testing, be sure all previous jobs have completed or are cancelled and removed.

The latest version of HPLIP is 3.12.11. I would suggest going to the hplip site and downloading hp's version, purge Ubuntu's version, install the hp version and see if that helps. If not, give us the information I asked for above and we'll try to find out where the problem is.


and just conveying it by that cable and not on network  yes the job is added to queue regardless even if it the only job it end up in a cue and sits there I'm sure the live cd of ubuntu I'm using already comes pre installed with the lawyers version of hplip of 3.12.11 am I right if so I don't see how updating would help as it already as the lastest version


I'm sure you can help with solve this matter please




yes I'm printing direct from the live cd which I'm told by a previous post I asked from here if I can print from the live cd and was told I could 

the printer has like a parallel port one end and USB port that goes to the computer the be exact is this cable in the picture below

[IMG]http://kbsinc.com/media/catalog/product/cache/5/image/9df78eab33525d08d6e5fb8d27136e95/p/a/parusb.jpg[/IMG]

---

### Post by Not install on 2013-01-13
> **agillator said:**
> First, you installed ubuntu from the live cd; you are not trying to print from the live cd, right?

Second, how are you connecting your printer, usb or network?

When you print something it is added to the queue, so if an earlier print job has hung, everything else is waiting for that job to finish. When testing, be sure all previous jobs have completed or are cancelled and removed.

The latest version of HPLIP is 3.12.11. I would suggest going to the hplip site and downloading hp's version, purge Ubuntu's version, install the hp version and see if that helps. If not, give us the information I asked for above and we'll try to find out where the problem is.


yes I'm printing direct from the live cd which I'm told by a previous post I asked from here if I can print from the live cd and was told I could 

the printer has like a parallel port one end and USB port that goes to the computer the be exact is this cable in the picture below

[IMG]http://kbsinc.com/media/catalog/product/cache/5/image/9df78eab33525d08d6e5fb8d27136e95/p/a/parusb.jpg[/IMG]


and just connecting it by that cable and not on network  yes the job is added to queue regardless even if it the only job it end up in a cue and sits there I'm sure the live cd of ubuntu I'm using already comes pre installed with the latest version of hplip of 3.12.11 am I right if so I don't see how updating would help as it already as the lastest version. I have tried to wait and see if printing job as finished but after hours still sits there


its like ubuntu recognises the printer and displays it in the printer properties panel  but does not communicate to send the printer out of the printer just processing then goes to idle nd won't print anything 

what's going on here


I'm sure you can help with solve this matter please .

---

### Post by Not install on 2013-01-13
I also tried again to delete the printing jobs that werein cue and print Fresh single document it just sits there for hours and on paused. I analyse and continue printer and no results

what's going on here?

---

### Post by agillator on 2013-01-13
I'm not sure what's going on. However, the symptoms are similar to ones I see when a computer loses contact with a networked printer. In that case often all that is necessary is to reestablish the network connection by rebooting the computer or restarting the printer and then 'resuming' the print job in the print manager. However, I don't know that that is the case here. My suggestion would be to replace Ubuntu's HPLIP with HP's and see if that makes a difference. If not, try simply resuming a stopped job, assuming it is the only job in the queue, of course. Gather all this info, including what you have already told us and the picture of your cable, and contact HP customer support. In my experience they have been quite helpful unlike many other manufacturers.  [Added] However, word of note. I keep forgetting you are running Ubuntu from the cd and not installing it. That could be the problem. So, I think the first thing to do is to make some room on your hard drive, install Ubuntu and then see what happens. That could very easily be the source of the problem.

---

### Post by Doug S on 2013-01-13
Note: I am writing this reply largely from memory, as my notes are a little vague. There may be some erronious content.
 
I did manage to make my HP LaserJet 1000 printer work as a shared CUPS printer on an Ubuntu server, but it was some work. I retired that printer about a year ago.
 
The difficulty with the HP1000 is that it does not have any built in processing/ rendering and it pre-dates the way that hplib expects to communicate with HP printers. Last time I checked (well over a year ago) there were no drivers from HP for MAC's, windows 7, or linux.
 
I ended up using the foo2zjs driver, but not the version from ubuntu the [one from the web site]("http://foo2zjs.rkkda.com/") . Also, it ends up that some firmware needs to be downloaded to the printer every time it is powered up. My notes say: "Use hotplug/udev/ script that comes with f002zjs or do it manually: cat /usr/share/f002zjs/firmware/sihp1000/pl > /dev/usb/lp0" In the end the printer looks like a generic postscript printer.

---

### Post by agillator on 2013-01-13
Thanks for the information. That is the first HP printer I have heard of that doesn't work with HPLIP. I didn't realize the HP 1000 was that old. You live and learn. Glad you got it working. You might mark the thread 'solved'.

---

### Post by Not install on 2013-01-14
> **Doug S said:**
> Note: I am writing this reply largely from memory, as my notes are a little vague. There may be some erronious content.
 
I did manage to make my HP LaserJet 1000 printer work as a shared CUPS printer on an Ubuntu server, but it was some work. I retired that printer about a year ago.
 
The difficulty with the HP1000 is that it does not have any built in processing/ rendering and it pre-dates the way that hplib expects to communicate with HP printers. Last time I checked (well over a year ago) there were no drivers from HP for MAC's, windows 7, or linux.
 
I ended up using the foo2zjs driver, but not the version from ubuntu the [one from the web site]("http://foo2zjs.rkkda.com/") . Also, it ends up that some firmware needs to be downloaded to the printer every time it is powered up. My notes say: "Use hotplug/udev/ script that comes with f002zjs or do it manually: cat /usr/share/f002zjs/firmware/sihp1000/pl > /dev/usb/lp0" In the end the printer looks like a generic postscript printer.


Thankful doug I will have to try your method and will let you know if it worked I might need some extra help from you if that's ok


so do you have to download a file evrytime you turn on the printer? Which file do you have to keep downloading

ALSO YOU SAY UBUNTU SERVER CAN I NOT USE IT ON BANTU STANDARD AND NOT SERVER.

---

### Post by Doug S on 2013-01-14
The downloading of the firmware to the printer on power up can be automated. In the end I never had to think about it.
 
Yes, I think it should work with Ubuntu desktop version, I was just saying what I did it on is all.
 
As a first step, I would suggest to try the Ubuntu package library version. Their web site says not to, but it said the same thing two years ago. However, I did note a HP1000 related note in the change log from just yesterday.

---

