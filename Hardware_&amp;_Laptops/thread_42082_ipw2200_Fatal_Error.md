---
title: "ipw2200 Fatal Error"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by jhuff on 2005-06-15
I am now having problems with my wireless connection on my Dell Inspiron 9300.  When loading up I am getting error messages when Linux tries to Configure Network Interfaces.  I have read some postings and it seems maybe a recent update could be to blame.  The problems only started a week or so ago.  

Do I need to update the driver?

Has anyone had a similar problem?  I can still get a network connection but the connection speed is slow, and it no longer seems to deal with the range extender I have connected to the wireless network.

The following are the error messages I get when starting up my system:

dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x00000100, Config: 00000142
ipw2200: Start IPW Event Log Dump:

---

### Post by luca_linux on 2005-06-16
Yeah, you should really update your driver and firmware. There've been a lot of fixes.
Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by jerome bettis on 2005-06-16
i'm not so sure about 1.0.4 with the new firmware.  my connection drops off a lot ... a lot more than with 1.0.3

now i can't get 1.0.3 to compile with this kernel cause it's patched with suspend2 and they didn't fix that till 1.0.4

argh

---

### Post by luca_linux on 2005-06-16
Sorry, but I'm not getting any problem with ipw2200 1.0.4 and firmware 2.3.

---

### Post by jhuff on 2005-06-17
Updating the driver did work.  I know little about Linux so it was a painful process.  I lost wireless capability for two days while I tried to figure out what went wrong with installing ipw2200 1.0.4 as described in [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

I finally got it working after I did the following:
1.Followed the instruction from  [http://nickselby.com/articles/technology/?a=1807](http://nickselby.com/articles/technology/?a=1807)  for adding kernel headers
2.Manually deleted the directories that were not deleted by the remove-old script.
3.Installed "build-essential"

---

