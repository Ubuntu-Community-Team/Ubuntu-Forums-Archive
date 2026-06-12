---
title: "Intel Wireless disconnect...pls check my syslog attached"
date: 2009-06-22
forum: Hardware
---

### Post by popfej on 2009-06-22
Hi,

I've got a built-in Intel Wireless ABGN card in my MSI Megabook.
Wireless is fine, when browsing internet or playing online downloading big files etc...

BUT

If I leave notebook idle for about 10-15 min (file downloading in progress in the background, so there is traffic on the card)
wireless gets disconnected. Only when I leave notebook alone :-s

If I simply reconnect my Wi-Fi, gets work again without any problems.

Syslogo:

iwlagn: Microcode SW error detected. Restarting 0x2000000.
Jun 20 22:15:01 msinote kernel: [11995.580706] iwlagn: Can't stop Rx DMA.
Jun 20 22:15:01 msinote kernel: [11995.581051] iwlagn: MAC is in deep sleep!


Looks like my card goes to sleep even if there is traffic on it.


Troubleshoot steps already done:

-network manager uninstall --> using WICD  instead of nm
-another driver for the card (ndiswrapper)
-all software updates downloaded for Ubuntu  (9.04)
-there was some kind of (official, automatic) kernel upgrade this week, but didn't solve the problem
-as I can remember it was working fine about 1-1,5 months ago (maybe a SW update caused some trouble??)
-tried disable wifi power management in gnome power manager --> no option for this 
-tried disable wifi power management in kde power manager --> no option for this 
-tried with this command: iwconfig wlan0 power off (shows power management is off, but still same problem)
-(other distributions worked fine on the same notebook, e.g.: suse / slax)
-has Ubuntu guys  (kernel / Intel driver) solved this issue? Should I try the newest kernel? (now I'm using default 9.04 kernel which comes with the DVD 64bit edition)
-is there same issue with wireless on 32bit version of Ubuntu?

Still looks like, my card goes to sleep after a while even if there's a lot of traffic.

Any ideas?
Should I disable APM/ACPI ?
Should I check /etc/default/acpi-support ?
Where else can I disable power management for Intel Cards?

(I saw a thead about disabling the display dimm in power management...maybe it fouls the Intel card...i'll try that)

Thanks in advance!

---

### Post by popfej on 2009-06-23
Update:


- tried to modify suspend/resume scripts in /etc/acpi folder
- changed router settings (e.g. encryption + channel)

None of above workded.

BUT

After these, I checked my loaded drivers. Ububtu told me that I have 2 nvidia drivers.
First one is default, second one is recommended. It was a little bit confusing, but I had no issues with video card. Anyway, I disabled all nvidia drivers and since that I had no wireless issues. I hope this is a perma solution. I'll test it today all day long. Hope that solves my problem.

(nvidia driver install history: i added a manual link to sources list in order to get the best nvidia driver....maybe that's why i had 2 different drivers that caused this problem)

Will update this post.

---

### Post by popfej on 2009-06-29
another update:

after a Jaunty clean install wireless was fine again.

Finally I installed the nvidia drivers and wireless is hacked again. :-s

I tried the built-in Nr. 180 driver  --> wireless disconnects again
I tried the built-in Nr. 173 driver  --> wireless disconnects again

Also tried the downloadable amd64 nvidia installer script (from nvidia official site) 

---> wireless disconnects again

Is it a know issue with nvidia driver? Or should I forget Intel wireless and change it to Atheros / Broadcom etc.... ? I'm fed up with this problem :-)

Cheerz!

---

