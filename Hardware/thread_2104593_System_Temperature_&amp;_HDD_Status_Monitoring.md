---
title: "System Temperature &amp; HDD Status Monitoring"
date: 2013-01-13
forum: Hardware
---

### Post by HtpcSystem on 2013-01-13
Dear Friends,

I'm searching for a program in order to monitor system temperatures of my HTPC. The key point is that I should be able to monitor those temperatures via web browser(web UI) interface from other computers.

In order to be more precise and clear about the expectation, hardware for temperature monitoring is as follows ;

* CPU & GPU --> AMD E350 
* SSD Harddisk --> Ocz Agility 3 60GB
* External USB HDD #1--> WD My Book Essential 1TB
* External USB HDD #2--> WD My Book Essential 2TB

The critical point is, lm-sensors, hddtemp like programs are not able to show temperature values for External USB HDD drives.

There are two software "Hardware Sensors Indicator" and "HDSentinel" that reads all temps including External USB HDD drives but both of them do not have any web UI option.
(*Windows version of HDSentinel has also web UI option and works like a charm!*)

I'm pretty suprised and upset that these things are already available in windows (!) but not in linux environment !

Anyway, I'm (we are) awaiting your kind support and recommendations

---

### Post by ahallubuntu on 2013-01-13
Use GSmartControl for hard drive status and temperature.  To access external hard drives, you may need to add options to the "smartctl" command.  Options you probably need are

-T permissive

and/or 

-d sat

---

### Post by HtpcSystem on 2013-01-14
> **ahallubuntu said:**
> Use GSmartControl for hard drive status and temperature.  To access external hard drives, you may need to add options to the "smartctl" command.  Options you probably need are

-T permissive

and/or 

-d sat

Does it have the option of web UI ?

---

### Post by dabl on 2013-01-14
No.

> **HtpcSystem said:**
> I should be able to monitor those temperatures via web browser(web UI) interface 

> 
There are two software "Hardware Sensors Indicator" and "HDSentinel" that reads all temps including External USB HDD drives but both of them do not have any web UI option.

> 
(*Windows version of HDSentinel has also web UI option and works like a charm!*)

I'm pretty suprised and upset that these things are already available in windows (!) but not in linux environment !


Where is all this coming from -- have you made any kind investigation of GNU/Linux at all?

---

### Post by HtpcSystem on 2013-01-14
The attidude is not to offend and make anyone angry or get into a harmful situation.

---

### Post by tgalati4 on 2013-01-14
You can install nagios/cacti, but that is a lot of overhead for just monitoring temperatures.  A better solution is to simply put some temperature monitoring applets on your panel and then set the preferences to send you an email/text message when they exceed limits.  That way you only get bothered when something is out of range.

Alternatively, you can write a script to display temperatures for all of your devices then call that script using ssh.

tgalati4@Dell600m-mint14 ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.5°C  (crit = +102.0°C)

Something like:

ssh yourusername@yourmachinename sensors

You can also install xsensors and remotely display temperatures on up to 10 different machines.  Try that on Windows.

ssh -2 -Y yourusername@yourmachinename xsensors

There are so many ways to do this, you just have to get creative.

---

### Post by dabl on 2013-01-15
> **HtpcSystem said:**
> The attidude is not to offend and make anyone angry or get into a harmful situation.

Speaking for myself, I'm not at all angry or offended.  But I noticed you joined the forum the same day you announced "the way things in Linux should be".  Isn't that just a wee tiny bit presumptuous, if you don't have a considerable experience with Linux to back it up?

Direct comparisons of Linux user interfaces to Windows user interfaces, and the availability of particular capabilities in Linux software to the Windows software, is unlikely to be a useful way to achieve your goals.  If your goal is to monitor the output of _some_ common sensors, Linux can do that.  Like many other hardware-specific software packages, the sensor hardware producers tend to write extensive driver packages for the Windows OS, and often don't write anything at all for Linux.  That leaves Linux users dependent on the open source community's generosity and inclination to develop driver software.  So you have projects such as [**[color=green]lm-sensors[/color]**](http://www.lm-sensors.org/) for driver software (similar to the situation with openprinting.org and printer drivers).

So, you can monitor CPU temps and hdd temps, and the speeds of some but not all fans, and you may get lucky and monitor a GPU here and there, but unless you can convince some open-source developer(s) that it's terribly important to drop everything and spend his time developing a browser front-end to the lm-sensor output, it's unlikely to happen.  (And I don't ever recall seeing another opinion suggesting that).

I hope that's informative, if not satisfying.  :)

---

