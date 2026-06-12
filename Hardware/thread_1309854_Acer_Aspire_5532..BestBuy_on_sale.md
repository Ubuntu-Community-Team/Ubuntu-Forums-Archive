---
title: "Acer Aspire 5532..BestBuy on sale"
date: 2009-11-01
forum: Hardware
---

### Post by Snosrap68 on 2009-11-01
Want to get the Acer Aspire on sale at Bestbuy.com , but not sure about 9.10 or 9.04 compatibility. 

Snosrap
Auburn, AL

---

### Post by Snosrap68 on 2009-11-03
No replies.  With a little more research I purchased the Acer Aspire 5532 with AMD 64 bit processor and Windows 7 64 version.  Installed 64 bit 9.10 with no issues.  All drivers and everything is working so far.  Woot,.,..Woot.  Oh, I did a 60GB partition for Ubuntu and using Grub to dual boot with 7.  No issues there either.

Snosrap
Auburn, AL

---

### Post by stickhead on 2009-11-08
Just bought one myself; great price. I'm waiting for Ubuntu 64 to download then I'll be able to get this thing going. Did all the laptop specific things work for you (i.e. battery indicator, suspend etc.)?

---

### Post by dad311 on 2009-11-14
I bought one of these, everything seems to work great except the wireless.

The wireless card works great with the Live CD, but when installed to the hard drive the signal fades in and out, then drops the connection.  After dropping the connection, Ubuntu keeps asking for the network password(guess it forgot).

Because the card works with the live CD, there must be an easy fix.  ANYONE KNOW WHAT IT MIGHT BE?

thx

---

### Post by kbm on 2009-11-18
Well, no answer for you, but I am having the same problem.  Looks like the ath9k driver is crashing.  Most times after the wireless goes on me, it will not shutdown (dlg comes up, but then does nothing), and the konsole shell does not work right (text does not show until you clear scroll-back and reset).  Also looks like any attempt to authenticate (sudo etc.) kind of just dies.  Strange.  I'm figuring that the wireless driver crash is taking other apps with it (low level, DMA problem maybe?).  There are some DMA errors after the issue that show up in syslog.

About the live CD thing.  Mine often takes quite a while to die, so you may not have been running the live CD long enough for it to happen.  We seem to have better luck if my wife (it's her machine) logs out when she is not using it.  A pain, but until this gets fixed...

Anyway, I'm still looking, but if anyone has any ideas... please let me know.

Opps, almost forgot.  It's running Kubuntu 9.10.  Using the default network manager.

---

### Post by Snosrap68 on 2009-11-21
Sorry no reply to the lights and indicator question...I have been away.  Yes all the things I need and look for work.

The Atheros driver fixes the wireless connect issue.

Snosy

---

### Post by kbm on 2009-12-03
> **Snosrap68 said:**
> 
The Atheros driver fixes the wireless connect issue.

Snosy

What do you mean by the Atheros driver?  The ath9k module is loaded by default for me and I've updated to the latest kernel (-15), but I still get the driver crashes.  Did you have to do anything specific to get a different driver?

---

### Post by NikolajSkov on 2009-12-03
Hi guys,

I'm running Ubuntu 9.10 64 bit on an Acer Aspire 5536 and are having the same problems with the wireless connection dying suddenly. Sometimes it just keeps asking for the WEP/WPA key, other times it just dies. A reboot is needed to get a connection again.

BTW, I am running Windows Vista on an identical machine and are not having any problems with the wireless connection.

Can anybody tell me how I can see which driver I am using?

Cheers,
Nikolaj

---

### Post by Snosrap68 on 2009-12-03
Also, install the following and all should be good:

  	 	 	 	 	 	  linux-backports-modules-2.6.31-14-generic
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic


Snosy:p

---

### Post by kbm on 2009-12-07
I installed:
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

The kernel specific stuff came as dependencies.  The system has been up for 2 days now with no wireless drop.  I've even done a fairly large file sync between it and another machine, which would have tanked the connection pretty quickly in the past.  No problems.  Looks like this is the fix.  Thanks all.

NikolajSkov, to see your driver, I believe that lsmod will show you if the ath9k module is loaded.  This site has a lot of info that will help you as well:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by razagee on 2009-12-07
hello,

sorry to say that i have no [information]("http://www.beautyforall.org") on Acer.

---

### Post by gbthomps on 2009-12-31
I am planning on buying one of these today.  My old dell inspiron 1150 has charging problems, I think due to the constant overheating.  At this price, I can't pass up the chance to replace it.  Sounds like there are no compatibility issues other than the fix for the wireless provided in this thread.
 
I have been running 9.10 on my dell.  Should I be using the 64 bit version on the new acer?  What is the difference?  Any advice would be greatly appreciated.  Thanks.

---

