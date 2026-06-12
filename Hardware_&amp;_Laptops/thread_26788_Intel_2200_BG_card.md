---
title: "Intel 2200 B/G card"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by silversun on 2005-04-13
It seems like my Intel 2200 BG card on my laptop (Compal CL56) is very flaky. 
There are times when I boot up the system and it wont even start the device (because if it is on, i can see an orange light). 
Furthermore, I activate it and I set the essid but still does not work. 

Whats even more annoying is that it takes a lot of time to configure network interfaces during bootup. 

Any ideas?

---

### Post by circussideshow on 2005-04-23
I also have a CL56 with the Intel 2200 BG wireless.  I am experiencing some similar issues where it would drop the connection about every 15 minutes and I would have to go System > Administration > Networking and deactivate / reactivate for it to start working again.  Then I booted up the other day and it wouldn't get past the starting of the networking devices or whatever its called, I had to Ctrl-C it.  Ever since then, I cannot get wireless to work at ALL.  I spent about a day reinstalling the ipw2200 from sourceforge, and even trying ndiswrapper.  Nothing worked.  So since it worked with the out of the box install, I reinstalled Hoary.  Still did not work.  Now I get 4 lines after it tries to start the network pertaining to something about dumping events, blah blah.    It's not a hardware issue because I can boot to an XP partition and use wireless all day long with no problems.  Please help.   ](*,)

---

### Post by blueplazma on 2005-04-23
I'm using the same card on a Dell Inspiron 8600 with no trouble at all.  What driver are you using?  The ndiswrapper one or the ipw2200 kernel module?  I'm using the latter successfuly.  I would suggest taking a look at /var/log/syslog and dmesg to see if there's some kind of error popping up.

---

### Post by luca_linux on 2005-04-24
The time out issue has been solved as many others: Ubuntu has an old driver version (0.19) while the latest one is 1.03...so you all had better install the latest driver and firmware from ipw2200.sourceforge.net.
Here's a howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

The led light has nothing to do with the driver, since it's controlled by acpi and not by the driver and by the wireless card activation.

---

### Post by circussideshow on 2005-05-16
Care to elaborate on the ACPI thing?  I have a CL56 with a killswitch for the wireless, and I think that's my issue (even though it worked first install...), I saw this evidence in the dmesg log.  I tried to install the Acer switch drivers per this site: 

[http://heim.ifi.uio.no/~krisvh/linux/cl56.html](http://heim.ifi.uio.no/~krisvh/linux/cl56.html)

and got the actual driver from here:

[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)

Now I just have to figure out how the crap to compile and install this stuff (took me like an entire day to get kernel source installed, I still don't really get what I did, kernel-headers what?)

Any help would be appreciated.  :-|

---

### Post by kwood129 on 2006-10-31
Has anyone made any real progress with this issue?  I have two hard drives here (one windows and one Ubuntu Edgy).  If I unplug the laptop during the day it will lose the orange LED and the only way I have found to consistantly get it back is to swap drives and boot to windows.  If I do this then it will come on just fine everytime I start it unless I unplug it again.  I never have problems with it dropping out but its more than annoying to have to swap drives just to get the card up and running.  All I really need is a way to get the card to initialize (power up and have the light on).  Does anyone have a clue how to do this?

---

