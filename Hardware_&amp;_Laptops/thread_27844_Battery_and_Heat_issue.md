---
title: "Battery and Heat issue"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by Haugland on 2005-04-17
Hello,

I've been using Ubuntu/Kubuntu for a couple days now. Anyhow, I cannot no matter what I do, get my battery status to display properly. I believe it's related to that why my temperature is so high.

Right now the laptop is operating at  50 C. Seldomly it operates at 40 C and sometimes upwards of 60 C. I've used the laptop for a couple of months with Windows XP Pro and it's never gotten this hot (can tell by feel).

So, I was wondering if any of you could provide some possible solutions to get it working. I've tried searching and nothing I did seemed to work.

My Laptop:
Acer TravelMate 4000LCi
Intel Pentium M 710 (1.4 GHz, 400 MHz FSB, 2 MB L2 cache)
40GB HDD
DVD/CD-RW Combo
512MB DDR
802.11b/g

Thanks.

---

### Post by blueplazma on 2005-04-17
Do you have powernowd running?  You can check with ```
pgrep powernowd
```  If you get a number back, then it is running, otherwise it isn't.  It could be that your CPU is not being throttled down to an appropriate clock speed when it should be.

---

### Post by Haugland on 2005-04-17
[QUOTE=blueplazma]Do you have powernowd running?  You can check with ```
pgrep powernowd
```  If you get a number back, then it is running, otherwise it isn't.  It could be that your CPU is not being throttled down to an appropriate clock speed when it should be.[/QUOTE]
 I hadn't tried that before, but I did just now and got the number "7254"

---

### Post by duplex on 2005-04-18
I have exactly the same problem with my Notebook:

HP Omnibook XT1000
Intel mobile P3 - 1.2 GHz

Powernowd is running, but it seems that it doesn't read out the temperature correctly. Sometimes the temperature of my CPU is nearly 70° C and I can't touch the bottom of my notebook, because it's so hot.

Does anybody have an advise for me?

---

### Post by Haugland on 2005-04-18
Ok, I just went into Windows (after letting the Laptop cool) and checked the temperature. It was actually higher than in Linux, idling at 54 Celcius. So that's not an issue at all. Apparently my touch is nothing compared to the real sensors. Windows just ran the fan more because it used the CPU more than Linux does, resulting in it kicking in the fan more often to cool it.

So it's just a battery issue now. I have a feeling it's related to ACPI and the smart battery system Acer uses. I've tried some things, but couldn't ever get them to work properly. Any advice is greatly appreciated.

---

### Post by blueplazma on 2005-04-19
[QUOTE=Haugland]Ok, I just went into Windows (after letting the Laptop cool) and checked the temperature. It was actually higher than in Linux, idling at 54 Celcius. So that's not an issue at all. Apparently my touch is nothing compared to the real sensors. Windows just ran the fan more because it used the CPU more than Linux does, resulting in it kicking in the fan more often to cool it.

So it's just a battery issue now. I have a feeling it's related to ACPI and the smart battery system Acer uses. I've tried some things, but couldn't ever get them to work properly. Any advice is greatly appreciated.[/QUOTE]

I don't really know anything about the smart-battery thing Acer does, I've only used Dell so far...

---

### Post by mirtux on 2005-04-21
Hi,
   i've got a Travelmate 8005 and after some initial glitches, i'm running with cpufreq and speedstep-centrino module; in this situation normally i'm  on 43 C. Without it (and the CPU running full ahead i've too 50 C). I think that the most important thing is to have a good running scaling driver.

Regards,
MC

---

### Post by HolyKnight on 2005-04-26
Ok. How do you turn that feature off in ubuntu? I have run over 30 distros on my computer. My computer runs hot. I know, I over clocked it. I have never got this error with any other distro. Including VectorLinux, FeatherLinux, SlackWare, Red-Hat Core 2, Mandrake 10.2, BEERnix 1.0 just to name a few. Only ubuntu has this problem. I been told that ubuntu is great. However, It auto shuts down due to temp. when loading. Is there any way to turn the feature OFF?

---

### Post by wildcard on 2005-05-28
The fact that your battery isn't displaying properly in addition to the temps make me believe that you may not have the acpid power management daemon running. Go to synaptic, find both rcconf and acpid, and download them both.

Then go to a terminal window and type 'sudo rcconf' - in this window, see if you have acpid and apmd running. If you do, disable apmd, OK out of this window, then reboot. See if that helps.

---

### Post by ssck on 2005-05-29
hi all,

i am using an acer travelmate 2300.when i tried the 'pgrep powernowd' there was no value returned.does that mean the powernowd is not running ? if so, how do i get it to start up ?

i have the same issue of battery not showing the right value.how do i sort it out ?

any help appreciated.

thanks

---

### Post by ssck on 2005-05-29
[QUOTE=ssck]hi all,

i am using an acer travelmate 2300.when i tried the 'pgrep powernowd' there was no value returned.does that mean the powernowd is not running ? if so, how do i get it to start up ?

i have the same issue of battery not showing the right value.how do i sort it out ?

any help appreciated.

thanks[/QUOTE]


sorry, just to add : how to do u get speedstep to run ?

---

### Post by thechitowncubs on 2005-06-04
My travelmate runs really hot too. The fans never seem to go on. In windows it seemed to stay a lot cooler :/

---

### Post by mekanzoo on 2005-06-15
I'm using Fujitsu Lifebook E4010.  Its runs really hot too... 
any idea why..??

---

### Post by keithpeter on 2005-06-20
[QUOTE=HolyKnight]Ok. How do you turn that feature off in ubuntu? I have run over 30 distros on my computer. My computer runs hot. I know, I over clocked it. I have never got this error with any other distro. Including VectorLinux, FeatherLinux, SlackWare, Red-Hat Core 2, Mandrake 10.2, BEERnix 1.0 just to name a few. Only ubuntu has this problem. I been told that ubuntu is great. However, It auto shuts down due to temp. when loading. Is there any way to turn the feature OFF?[/QUOTE]

Same here although I'm not overclocking.

I use a Dell L400 12" laptop. The fans run fine on Windows Me, and weirdly when booting from an ms-dos disc. This laptop is 4 years old - should I be using apm in place of acpi?

When booting from cold into Ubuntu, the temperature reads from /proc/acpi/... but never switches the fan on. I've had the laptop closedown thru' overheating a couple of times now.

Any help appreciated as otherwise I'd be well happy to wipe WinME and use Ubuntu as it has all the software I need and more and is secure.

Cheers

---

### Post by snop on 2005-06-20
Hi, 

I own an Acer Travelmate 4001Wlmi. Check [http://ubuntuforums.org/showpost.php?p=220754&postcount=5](http://ubuntuforums.org/showpost.php?p=220754&postcount=5)  to see how I solved laptop's heat problems.

---

### Post by thechitowncubs on 2005-06-21
[QUOTE=snop]Hi, 

I own an Acer Travelmate 4001Wlmi. Check [http://ubuntuforums.org/showpost.php?p=220754&postcount=5](http://ubuntuforums.org/showpost.php?p=220754&postcount=5)  to see how I solved laptop's heat problems.[/QUOTE]
 Thanks a lot, this was the ONLY thing bugging me.

The front WAN LED lights are not required but that needs some tweaking too.

---

### Post by snop on 2005-06-21
> The front WAN LED lights are not required but that needs some tweaking too.


The wireless led can also work if you use the latest ipw2200 driver. Check  [this](http://ubuntuforums.org/showpost.php?p=167782&postcount=46)  and/or [ this](http://www.ubuntuforums.org/showthread.php?t=26623 ).

---

