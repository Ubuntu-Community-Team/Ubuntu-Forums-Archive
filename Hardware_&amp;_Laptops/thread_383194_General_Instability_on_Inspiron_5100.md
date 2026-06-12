---
title: "General Instability on Inspiron 5100"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by pldobs on 2007-03-13
I have a Dell Inspiron 5100 with a 120 gig HD and a Gig of ram.  I have recently installed Ubuntu and XP dual boot.  I have been experiencing a lot of general instability.  I'll list some of the problems I've been having below.

1.  If I switch user or log out as one user and log in under a different one, within a minute my keyboard becomes unresponsive and I cannot run most programs.  I also cannot bring up the screen to logout shutdown, etc.  At this point I have to kill the power and reboot.

2.  Just working along, sometimes surfing the web, or doing Java development or using OpenOffice.org.  My mouse lock up, or keyboard lock up or both and usually cannot reboot as in problem #1.

3.  Sometimes but not always, if the screen saver is on for a long time, by screen blanks out and I cannot get it back.

4.  My Network manager sometimes forgets how to reconnect to my wireless network.  I wonder if this has something to do with hard reboots due to problems 1-3

I have spent countless hours getting Ubuntu configured just right.  Please don't tell me I have to reload (unless it's the truth of course).

Any ideas? Thanks for all your help!

---

### Post by konungursvia on 2007-03-13
Linux has been tested far less on laptops than other more common and standardized hardware. Did you try Dapper Drake (ubuntu 6.06)? It may be slightly better. If all else fails, I suggest you try Debian 3.0, which runs well on older laptops in my experience. It is also similar enough to ubuntu (which is based on debian) that you can still read and follow most of the great advice here as well.

---

### Post by ow66 on 2007-05-02
I also have an old 5100 and have the same problems. I only have 40GB HD and use a Belkin wireless card. No dual boot, just Linux. I upgraded it to Feisty Fawn and have not had the system lockups as before. However, the wireless driver is more flaky than before. If I suspend, or restart, the DHCP configuration won't work. If I toggle it to local conf ipv4, and then back to auto DHCP, then it will work. An annoyance. In the previous version, I had no wireless problem whatsoever. Aside from the wireless annoyance, this version seems to be more stable.

---

### Post by JoshuaRL on 2007-12-24
I've got the same laptop and noticed a lot of problems getting the graphics card to work since fglrx doesn't support Mobility M7.  But I found this thread and I think it may help us.

[http://ubuntuforums.org/showthread.php?t=580134](http://ubuntuforums.org/showthread.php?t=580134)

---

