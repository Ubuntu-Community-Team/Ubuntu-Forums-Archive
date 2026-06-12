---
title: "[SOLVED] Stuck with Vista on a Laptop? (Temperature Issues)"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by Maximos on 2008-01-23
Hi all,

Looking for some help here, as I'm a big fan of Ubuntu (and other varieties of Linux) and would love to have it running without concern on my newly-purchased Compaq Presario C700 laptop.  The concern is this: the CPU temperature when Windows Vista is running consistently varies from 32-39 degrees Celsius, whereas in Linux (in Kubuntu/Ubuntu, and in gOS) it runs consistently at a range of 48-62 degrees Celsius.  At the extremes, that's a difference of 30 degrees Celsius, which makes me uneasy.  I don't want to so much as risk overheating the machine, or even potentially shortening its life by running it consistently at higher (thought not extremely high) temperatures.  As such, I'm wondering if anyone has any advice.  In particular, I'm looking for ways to force the fan to run more in Linux, or for any other suggestions along the lines of making things cooler (except for purchasing products like cooling pads; I'm a poor college student).  If something can't be figured out, I guess I'll end up sticking with Vista, as much as I don't want to. (The only other possibility that's obvious to me is that someone might convince me that the temperature difference is not that significant... But that'll be tough, as I'm **very** protective of this laptop right now.)

I've read various threads on these forums about similar issues, but haven't seen any real solutions that will work for me.  The machine is new, so dust isn't an issue.  There does not appear to be a setting in the BIOS that controls the temperature at which the fan begins to run.  There is no file in my /proc/acpi/fan directory (that may be the wrong directory path, but hopefully you know the one I mean; I might not be getting the path exactly right as I'm not currently in Linux to check it), so it doesn't appear that I can control the fan through acpi.  In both Kubuntu and gOS, I've managed to monitor the temperature levels (using a gadget in gOS and using either one of ksensors or ktemperature in Kubuntu), and even apparently set the maximum temperature -- however, this only helps to a limited extent.  The most that it seems to do is get the fan running if the temperature goes anywhere above 50 degrees C; using this method, I can get the temperature to usually stay in a range of 48-55 degrees C, but that's still 23 degrees higher than Vista's extreme, and I can't get the fan to start up at temperatures any lower than that (even if I set the "maximum temperature" to something lower than 50, the fan doesn't kick in until it passes 50).  That's the state of my problem.  Any thoughts?

(If it's relevant, the laptop has a 1.6ghz Pentium Dual-Core processor (800mhz each core), 1 GB of RAM, and currently dual-boots Kubuntu and Vista.  I can offer other specs if necessary.  Thanks!)

---

### Post by gn2 on 2008-01-23
How are you measuring the temperature in Vista, most monitoring programs in Windows (all versions) are notoriously inaccurate.

[Core Temp]("http://www.majorgeeks.com/Core_Temp_d5665.html") is the best, and [here's]("http://www.alcpu.com/forums/viewtopic.php?t=211") how to make it work in Vista.

---

### Post by Maximos on 2008-01-23
I've been using SpeedFan.  I'll try that one out and let you know what it reports.  Thanks for the reply!

---

### Post by Maximos on 2008-01-23
This is very interesting.  I ran CoreTemp, and the temperatures it reports (in Windows Vista) are nearly identical to those reported by the sensors in Linux -- roughly a temperature range of 47-53 degrees Celsius right now.  This suggests that I have nothing to be concerned about, assuming that CoreTemp is more accurate than SpeedFan.  Even while CoreTemp tells me that the CPU is at 50 degrees, SpeedFan says that it is at 36 degrees.  I'll do a search on my own in a bit, but does anyone have any links to material about the inaccuracy of temperature monitors in Windows, or about the particular accuracy of CoreTemp?

Thanks much so far.  This is currently looking promising!

---

### Post by gn2 on 2008-01-23
This explanation from the creator of Core Temp should shed some light: [http://www.overclockers.com/articles1378/index.asp](http://www.overclockers.com/articles1378/index.asp)

---

### Post by Maximos on 2008-01-23
Here's an update, and it's good news.  As I mentioned above, CoreTemp reports that the CPU runs (in Vista) at basically the same temperature which ksensors reports (in Linux).  I've now also installed (in Vista) a monitoring program called PCWizard2008, as well as the Intel Thermal Analysis Tool (the CPU is an Intel product).  Both of these programs report temperatures nearly identical to the temperature reported by CoreTemp.  This means that CoreTemp, PCWizard2008, the Intel Thermal Analysis Tool, and ksensors and ktemperature (in Linux) all agree that the machine typically runs at a range of 47-55 degrees Celsius.  SpeedFan is the only odd one out, reporting the low temperatures in the 32-39 degree range.  

I'm thinking, therefore, that SpeedFan is simply mistaken.  I've read that it has problems with other systems and that one of these problems is reporting a temperature which is 15 degrees lower than the actual temperature.  Perhaps not coincidentally, you'll note that 32 degrees (the low temperature reported by SpeedFan) plus 15 equals 47, which is exactly the low temperature reported by the other monitoring tools I've used (except for ktemperature and ksensors; they report a low of 48, but they seem not to be very sensitive -- I've only seen them ever read 48 degrees or 55 degrees, nothing in between).  So, Linux appears to be handling things just fine. :)

Thanks again for the help!

---

### Post by Maximos on 2008-01-23
One final update.  I've done some additional investigating on Speedfan and have read that it apparently has the problem of the 15 degree difference with some of Intel's newer processors, specifically the dual-core and Core Duo processors.  The upcoming version of Speedfan is supposed to correct this.  Since my computer has a dual-core processor, I registered at the SpeedFan website and downloaded the beta of the upcoming version.  It recognizes my processor in a way that the current (stable) version of SpeedFan does not.  More importantly, it now gives the same temperature reading as CoreTemp, ksensors, PCWizard2008, etc.  So, I think it's safe to say that the problem has been diagnosed and remedied here.

---

