---
title: "Unstable internet since upgrade?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by WOOHOOHOO on 2009-08-09
Hi,

Since upgrading to Jaunty 9.04 a few months back. My internet connection keeps turning on and off all the time and it is a pain in the backside.

I can see from the lights on my router that it is just my connection disconnecting, everyone elses in the house is fine. I've tried new cables, using the old cables on another pc, and i cant solve it. It doesnt matter if i am the only person in the house or others are using, it always happens. I'm using latest Firefox and/or Swiftfox. ISP is no prob, as we have a high speed and the others dont have the same problem.

I've reinstalled 9.04 several times but still the same problem. Any ideas?

---

### Post by running_rabbit07 on 2009-08-09
Do you happen to know the brand and model of your network card?

---

### Post by garikaib on 2009-08-09
My advice is you should downgrade back to intrepid. I got my 9.04 cd two months ago and i tried both an upgrade and a clean installation but i had problems with everything from the jerky videos and shaky sound. All my printers refused to print even though i had received a notification telling me that my print job had been successfully completed.

---

### Post by phillw on 2009-08-09
Now this sound completely daft ......

If you are connected by ethernet cable (i.e. NOT WIRELESS) ... try a different cable.

If you do the install with ethernet cable, then switch to Wireless ... Don't !! - I had so, so much grief. The answer was to do a fresh install with out the ethernet cable.

I only suggest it, as I SERIOUS grief trying to get to wireless after installing with ethernet connected.

Hope it helps,

Phill.

---

### Post by running_rabbit07 on 2009-08-09
In the original post, he said he tried using different cables. I am guessing that reverting to Hardy may be the best bet. Hardy has the best support.

---

### Post by phillw on 2009-08-09
Soz ... wasn't paying attention :-(

Yup, it looks like back to Hardy may be an answer, but - this does not remove the problem.

How does the system perform when booted into 'Live CD' mode ?

Regards,

Phill

---

### Post by DaveRowell on 2009-08-09
Just for the record:  I upgraded to 9.04 a few days ago and have 2 problems (that I know about!).

1 - When a window closes the thin black border remains on the screen for a second or so after the window content disappears.  Old nVidia card that worked surprisingly well in the last 2 versions.

2 - Both Firefox 3 and Epiphany will shut down randomly.  Nothing consistent.  Once I was running Epiphany from a terminal and got several errors referring to GTK-4 widgets missing - it finally died on a segmentation fault.

---

### Post by WOOHOOHOO on 2009-08-09
@ runningrabbit - its a well old laptop (but never had issues with internet before). Not sure if this is right info, but i downloaded SysInfo and it said the following about my network stuff:
Ethernet Controller - Silicon Intergrated Systems (SiS) SisS900 PCi Fast Ethernet (rev 90)
Subsystem - Uniwell computer corp Device 5002
Modem - Silicon Intergrated Systems (SiS) AC'97 Modem Controller (rev a0)
Subsystem - Uniwell Computer Corp Device 4003.
Is that the right info?

@PhillW - yep, tried different cables. No difference. (what is live CD mode, you mean pressing Del at startup? If so, no difference.)

Its not slowing my system at all, i have very little on it in fact, purely for internet. Since typing this, disconnected 8 times.

I like 9.04, it runs well on my old crappy laptop and would prefer not to revert to old version and i guess some will become unsupported soon?

Thanks guys!

---

### Post by running_rabbit07 on 2009-08-09
> **WOOHOOHOO said:**
> @ runningrabbit - its a well old laptop (but never had issues with internet before). Not sure if this is right info, but i downloaded SysInfo and it said the following about my network stuff:
Ethernet Controller - Silicon Intergrated Systems (SiS) SisS900 PCi Fast Ethernet (rev 90)
Subsystem - Uniwell computer corp Device 5002
Modem - Silicon Intergrated Systems (SiS) AC'97 Modem Controller (rev a0)
Subsystem - Uniwell Computer Corp Device 4003.
Is that the right info?

@PhillW - yep, tried different cables. No difference. (what is live CD mode, you mean pressing Del at startup? If so, no difference.)

Its not slowing my system at all, i have very little on it in fact, purely for internet. Since typing this, disconnected 8 times.

I like 9.04, it runs well on my old crappy laptop and would prefer not to revert to old version and i guess some will become unsupported soon?

Thanks guys!

From what I can see, I don't understand why it doesn't connect. Do you have any Firewall settings on your router that may be inhibiting your connection?

Go to System>Administration>Network Tools. Does it show an IP address for IPv4 or IPv6? I have attached a screenshot of this tool. If it shows an IP address try to ping a wesite in the ping menu of the same tool. I am including a screenshot of me pinging [www.ubuntuforums.org]("http://www.ubuntuforums.org"). I am also including a screenshot of me doing a traceroute to Ubuntu forums. If you do the Netstat tab there should be a bunch of numbers in most of the lines. Let us know how these come out. If these tests are showing no results, then your system is not speaking to the router.

What Phil meant by LiveCd was using the install CD and selecting "try Ubuntu without making changes"

---

### Post by WOOHOOHOO on 2009-08-09
Hi Rabbit, thanks for your help. I dont have any firewalls that are bothering the router.

Yep, on the network tools, i have the ipv6 and v4 numbers (the same as yours in fact). I pinged ubuntuforums and no probs either.

The netstat is as attached.

I dont have the 9.04 cd, only the older one.

---

### Post by running_rabbit07 on 2009-08-09
it is pinging yet you can't connect through Firefox? I am stumped. There is definately a software issue in the OS.

Have you searched the bugs on the launchpad site to see if you can find a match? Or at least file a bug report. If there is already a matching report there may be a listed fix.

The IPv numbers are assigned by the router. Most routers use those same numbers.

---

### Post by running_rabbit07 on 2009-08-09
Do you have the same problems with epiphany or any other programs that access the web?

We need to figure out what software has the ability to change your settings. 

Is your cable modem or your network cable placed anywhere near and Air Conditioner or anything that turns on and off and uses high amperage motors? Fluorescent lights also put off EMI. If your wire runs by a new peice of equipment, try moving the wire or the equipment to see if that has an effect. 

Could be something new on the power supply circuit that is causing a sag in power to the modem, but that would cause the same problem for everyone on the network not just your system.

Intermittent problems are usually caused by EMI/RFI (electromagnetic interference/ radio frequency interference. Faulty hardware such as bad network card which is possibly having problems only when overheating. Bad cable connector of the computer or switch/router/hub.

I am just trying to throw out some possibilities here that could be causing the problem. If any of them click with you then check it out. I am not there to see things that might stand out as issues.

---

### Post by WOOHOOHOO on 2009-08-10
morning,

Yep, it happens on Swiftfox and foasterfox. I tried epithany but i ran into basic problems with that so i gave up.

I have a pc speaker near my laptop, i'll try moving that to see if that helps.

I'll have a look for this bug report, but i dont have a clue where. I've searched the problems alot before pozting on here and tried alsorts but no luck.

Og well, maybe time for a new laptop.

Cheers for your help, very much appreciated!

---

