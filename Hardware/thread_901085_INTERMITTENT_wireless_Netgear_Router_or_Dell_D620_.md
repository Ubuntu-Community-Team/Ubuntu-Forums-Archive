---
title: "INTERMITTENT wireless: Netgear Router or Dell D620 problem??"
date: 2008-08-26
forum: Hardware
---

### Post by computersleeper on 2008-08-26
Hi and thanks for taking the time to read and if you have time to respond, thanks in advance!

I own a refurbished Dell Latitude D620 laptop that was sent to me by Dell last year. Currently, I am unable to connect my D620 to my family's wireless internet network (I am home from college). But I AM able to connect to my NEIGHBOR'S wireless network AND my Dad's Dell Inspiron 6000 works fine on OUR wireless network. 

I first received this D620 last summer when I was also at home from college. During that time, my computer was able to connect via LAN cable. When I went back to school, I ONLY used wireless. When I came back home for winter break, I was strangely unable to re-connect to my house's LAN cable and my ethernet ports did not light up. Furthermore, I was unable to make a LAN cable connection to OTHER routers and modems as well. 

I want to connect to my house's wireless network, but I can only get an INTERMITTENT connection. Meaning, I can load gmail.com but not log into my account, or I can do a google search but not connect to the links produced in the results. EVEN AFTER reinstalling Windows XP. Again, my D620 works fully on my neighbor's wireless network BUT intermittently on my OWN network, but my Dad's Inspiron works fully on OUR wireless network and router. 

I thought I would need to replace my motherboard since my ethernet ports seemed broken. HOWEVER, now they are working again! BUT I'm not sure exactly why! 2 possibilities: 

1) there is a power conservation mechanism on my Dell D620 that deactivates the network card when you unplug the power. I have read that this mechanism can actually really interfere with LAN line connections (and not wireless). So I deactivated that power conservation mechanism. 

2) i installed a new hard drive and reinstalled Windows XP. perhaps this cleared out residual software that was interfering with my LAN line connection? 

My family uses a ~3 year old Netgear MR814v2 router. I am told it is 802.11v and only capable of 11 mbps, whereas newer 802.11b models are capable of 54 mbps. I have talked to netgear about proper configuration settings -- e.g. setting it to the right channel (11). 

Do I need a newer router? But why does my Inspiron work fine but the D620 alone has intermittent wireless connection. Or are there possible problems with my D620 I have not considered? 

I am wondering if there is still something bizarrely wrong with my motherboard....even tho my ethernet ports are working now, i havent tested them on other LAN lines/routers/modems, just my own.  also, i feel like i need to restart my comp or flush the DNS in order to reacquire the signal, instead of just re-enabling, or repairing.  frankly, i just have a bad feeling that those will stop working again.  so yes, im not sure if it is hardware or software or just the router!!!  but i have tried so many things, like configuring the setting of my router, safe mode, disabling all my software in device manager, reinstalling the OS, new hard drive, looking for environmental interference, deactivating the power conservation mechanism, OHH and even buying an external wireless card.  

help!

-ASh ???

---

### Post by computersleeper on 2008-08-26
i also wanted to mention that I have tried updating all the drivers on my computer...the dell technicians did this for me guiding me or remotely accessing to download the drivers themselves.  

i have am paranoid that maybe since it is a refurbished model, there are some mixed up parts or something?  furthermore, i was paranoid that maybe i broke my ethernet ports and need to get a new motherboard, because my ethernet chord would pop out all the time, and i should have gotten a new one, because i knew that that was bad for the computer and could cause some sort of surge.  HOWEVER, it kept working while i was using the loose ethernet chord, and only STOPPED worked after months of only using wireless, so it did not just suddenly stop working as a result of a a discrete instance with the ethernet chord popping in and out.  and of course, now they seem to be working again!  ahh, i am so confused since all the different scenarios that it does or does not work seems to contradict!

---

### Post by IntuitiveNipple on 2008-08-26
There are several possible conflated issues but you add confusion by talking about Windows XP. As this is the Ubuntu forums I think it would be a good idea to mention which Ubuntu version you're using, and give the output of a few commands to help us get a picture:
```

uname -a

lsb_release -a 

lspci -nn

lsusb

```

**Non-working Wired Connection**
I had a similar experience some time ago now with a notebook. The wired connection just wouldn't work, and on the notebook in question, it had a hardware switch that physically switched between the wired and WiFi device. I began to suspect the wired hardware was broken since the LED didn't light when a known-good cable was connected.

Then, suddenly, it began working again when I was threatening it with 'return to manufacturer'. I investigated and the what I *think* had happened is one or more of the thin metal spring-connectors inside the socket on the PC had somehow been forced out of alignment so they did not mate correctly with the plug on the wire.

Sometimes some careful prodding with a jewellers (minature) screwdriver can fix such issues - I've done that on other systems with similar problems.

**Intermittent Wireless**
The first thing to check is the precise settings in the MR814v2 router, to ensure you've not somehow got a mismatch. Particular things to look for are some kind of proprietary *turbo* mode that usually will only work with other devices from the same manufacturer.

Check the precise model and revision and OS/drivers being used by PCs that can successfully connect to the router. Also, check how those other PCs are configured to connect. For example, are they using DHCP to get an IP address lease and DNS servers to use?

That last issue is relevant since the MR814v2 has a [known issue with failed DNS resolution](http://kbserver.netgear.com/kb_web_files/N101150.asp). Other PCs not using full DHCP, or over-riding DNS settings could, in theory, work where your PC doesn't.

There might be other MR814 issues so [check the Netgear knowledge-base](http://kbserver.netgear.com/products/MR814v2.asp).

**Confusion over Wireless Standards**
802.11b = 11 Megabits/second maximum raw transfer rate
802.11g = 54 Megabits/second maximum raw transfer rate

---

