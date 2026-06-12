---
title: "System clock not syncronized"
date: 2009-11-13
forum: Hardware
---

### Post by loghete on 2009-11-13
I installed Ubuntu 9.10 on my laptop about a month ago, and the last couple of weeks I've noticed the system clock won't keep in sync. I installed ntp so it should be syncing automatically but apparently it isn't because every time the computer wakes up from suspend the clock is incorrect.

Any ideas what's wrong? Never had this problem on Windows (and not the first few weeks after Ubuntu clean install either, I think) so it shouldn't be a hardware problem.

---

### Post by loghete on 2009-11-17
Still experiencing the same problem. I have to manually run /etc/network/if-up.d/ntpdate every now and then. I guess I could make it run automatically every 10 minutes or so but that doesn't sound like the most convenient solution.

---

### Post by bethenco on 2009-12-30
Have you tried the following?

From the top panel, run System -> Administration -> Time and Date and then make sure it is set to "keep synchronized with internet servers" rather than "manual".

I was having the same problem: the time wasn't staying synchronized even though I had ntp installed. However, my setting in the above was "manual".

---

### Post by loghete on 2010-01-11
Yes, it is set to automatically syncronize, and I've tried selecting different servers to syncronize from.
It seems to syncronize correctly every time I start up the laptop, but if I leave it on it keeps lacking behind.

---

### Post by kgarbutt on 2010-01-11
Just a total guess, but does your computer have a battery that needs to be replaced. At one time, I had an older computer and I had to change the battery to keep the clock correct. Just a guess.

---

### Post by loghete on 2010-01-13
Well that could be possible, but the problem most often occurs while the laptop is in standby mode (turned on and screen down) and powered by the cable. Also, would a laptop have an extra battery for the clock in addition to the main one?

---

### Post by jromer on 2010-01-13
I'm having the same problem.

I'm running Hardy and recently changed from kernel 2.6.24-17 to 2.6.24-26 and now I'm having the same problem with my clock settings. 

I notice my clock is off by 5 hours which is my adjustment from GMT. I've used both manual and automatic server updates nothing seems to work, Also, it's not a battery problem because I dual-boot windows and under win xp the clock is OK.

---

### Post by Capoeira on 2010-01-29
same here.

was working fine until about a week ago. problem seems that ntpd inicalizes before dhcp:


demon.log:

```
Jan 29 03:39:54 estudio ntpd_initres[1455]: host name not found: ntp.ubuntu.com
Jan 29 03:39:54 estudio ntpd_initres[1455]: couldn't resolve `ntp.ubuntu.com', giving up on it
Jan 29 03:39:54 estudio ntpd_initres[1455]: host name not found: 0.south-america.pool.ntp.org
Jan 29 03:39:54 estudio ntpd_initres[1455]: couldn't resolve `0.south-america.pool.ntp.org', giving up on it
Jan 29 03:39:54 estudio ntpd_initres[1455]: host name not found: 1.south-america.pool.ntp.org
Jan 29 03:39:54 estudio ntpd_initres[1455]: couldn't resolve `1.south-america.pool.ntp.org', giving up on it
Jan 29 03:39:54 estudio ntpd_initres[1455]: host name not found: 2.south-america.pool.ntp.org
Jan 29 03:39:54 estudio ntpd_initres[1455]: couldn't resolve `2.south-america.pool.ntp.org', giving up on it
Jan 29 03:39:54 estudio ntpd_initres[1455]: host name not found: 3.south-america.pool.ntp.org
Jan 29 03:39:54 estudio ntpd_initres[1455]: couldn't resolve `3.south-america.pool.ntp.org', giving up on it
Jan 29 03:40:04 estudio console-kit-daemon[1162]: WARNING: Couldn't read /proc/1112/environ: Failed to open file '/proc/1112/environ': No such file or directory
Jan 29 03:40:07 estudio dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan 29 03:40:07 estudio dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 29 03:40:07 estudio dhclient: All rights reserved.
Jan 29 03:40:07 estudio dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 29 03:40:07 estudio dhclient: 
Jan 29 03:40:07 estudio dhclient: Bind socket to interface: No such device
Jan 29 03:40:08 estudio dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan 29 03:40:08 estudio dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 29 03:40:08 estudio dhclient: All rights reserved.
Jan 29 03:40:08 estudio dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 29 03:40:08 estudio dhclient: 
Jan 29 03:40:08 estudio dhclient: Listening on LPF/wlan0/00:1e:2a:b2:5d:09
Jan 29 03:40:08 estudio dhclient: Sending on   LPF/wlan0/00:1e:2a:b2:5d:09
Jan 29 03:40:08 estudio dhclient: Sending on   Socket/fallback
Jan 29 03:40:08 estudio dhclient: DHCPRELEASE on wlan0 to 10.0.0.1 port 67
Jan 29 03:40:08 estudio dhclient: send_packet: Network is unreachable
Jan 29 03:40:08 estudio dhclient: send_packet: please consult README file regarding broadcast address.
Jan 29 03:40:17 estudio dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan 29 03:40:17 estudio dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 29 03:40:17 estudio dhclient: All rights reserved.
Jan 29 03:40:17 estudio dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 29 03:40:17 estudio dhclient: 
Jan 29 03:40:18 estudio dhclient: Listening on LPF/wlan0/00:1e:2a:b2:5d:09
Jan 29 03:40:18 estudio dhclient: Sending on   LPF/wlan0/00:1e:2a:b2:5d:09
Jan 29 03:40:18 estudio dhclient: Sending on   Socket/fallback
Jan 29 03:40:19 estudio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan 29 03:40:19 estudio dhclient: DHCPOFFER of 10.0.0.4 from 10.0.0.1
Jan 29 03:40:19 estudio dhclient: DHCPREQUEST of 10.0.0.4 on wlan0 to 255.255.255.255 port 67
Jan 29 03:40:19 estudio dhclient: DHCPACK of 10.0.0.4 from 10.0.0.1
Jan 29 03:40:19 estudio dhclient: bound to 10.0.0.4 -- renewal in 34768 seconds.
Jan 29 03:44:53 estudio ntpd[1451]: Listening on interface #4 wlan0, fe80::21e:2aff:feb2:5d09#123 Enabled
Jan 29 03:44:53 estudio ntpd[1451]: Listening on interface #5 wlan0, 10.0.0.4#123 Enabled
```


in fact until a week before it didn't sync on startup either...but synct some minutes later. now it doesnt sync anytime

---

### Post by loghete on 2010-01-30
Oh, nice catch. That might be the problem for me too. How would one fix this?

---

### Post by Capoeira on 2010-01-30
i want to know too

---

### Post by IcarusR on 2010-01-30
Has anyone checked on launchpad to see if this bug has been registered & if not register it ??

---

### Post by Capoeira on 2010-01-30
[https://bugs.launchpad.net/ubuntu/hardy/+source/ntp/+bug/114505](https://bugs.launchpad.net/ubuntu/hardy/+source/ntp/+bug/114505)

---

### Post by Capoeira on 2010-01-31
there is a patch in the bug-report wich one there told to work in 9.10 too. how do I use the patch?

---

### Post by Capoeira on 2010-02-01
up


changed the ntp file in init.d with the patch ans it doesent work. do i have to add the patch to the existing file or do i have to exclude the content of the existing file?

how do i use the patch?

---

### Post by Capoeira on 2010-02-02
and to the top



let's find a solution....ntp not working is not acceptable

---

### Post by Capoeira on 2010-02-03
up

---

### Post by Capoeira on 2010-02-03
wrong forum?
please put in right catagory

---

### Post by loghete on 2010-02-03
After some struggling I managed to apply the patches, and it did change something but it's not working any better. The only change is that when Ubuntu boots, the ntp is slightly delayed (it takes a few seconds before the clock synchronized). I believe this is exactly what the patch was meant to do, but the synchronisation still isn't working after the computer wakes up from suspend.

So all in all, the 'patch' only made it worse and I'm still looking for a solution.

---

### Post by Capoeira on 2010-02-03
> **loghete said:**
> After some struggling I managed to apply the patches, and it did change something but it's not working any better. The only change is that when Ubuntu boots, the ntp is slightly delayed (it takes a few seconds before the clock synchronized). I believe this is exactly what the patch was meant to do, but the synchronisation still isn't working after the computer wakes up from suspend.

So all in all, the 'patch' only made it worse and I'm still looking for a solution.

can you tell me how to apply the patches?

---

### Post by loghete on 2010-02-06
Well, I didn't get the automatic patching to work so I manually looked up the right place in the ntp files, and added the '+' lines to them while removing the '-' lines.

---

### Post by Zanven on 2010-04-25
> **jromer said:**
> I'm having the same problem.

I've used both manual and automatic server updates nothing seems to work
I'm using karmic xubuntu on a computer without an internet connection. It dual boots win 7 and Xubuntu and the clock is fine in windows. I can't manually change the time. I'll change the hours, minutes or even date and as soon as a second passes it changes everything back to the incorrect time it was at before.

---

### Post by Capoeira on 2010-05-31
after installing Arch-Linux from scratch I rememberd this thread and I will post this link wich could help you guys. There you can find how to start ntpd ou openntp postconnecting with networkmanager or Wicd....in my case I use Wicd, and it works like a charm

[http://wiki.archlinux.org/index.php/Network_Time_Protocol](http://wiki.archlinux.org/index.php/Network_Time_Protocol)

---

### Post by emarkay on 2010-08-03
Is this still an issue?

---

### Post by loghete on 2010-08-05
No, it works now that I've reinstalled Ubuntu.

---

