---
title: "Different Fan Problem"
date: 2010-01-20
forum: Hardware
---

### Post by luckyfox on 2010-01-20
I have read around, and haven't seen anything like my particular problem.

I have a Toshiba Satellite a135-s2326 and am running Ubuntu 9.04 Jaunty Jackalop

I have moved from a perfectly working Vista machine, to Linux. Ubuntu 9.10 absolutely WOULD not install. I had problem, after problem, after problem... Finally, someone suggested using  Jaunty Jackalop and it worked without a hitch!

Well, kinda... I have noticed that although the fan IS working (I can see it spinning), it only spins for a short period of time, then stops. The machine seems to be running RATHER hot. When I was running vista, the fan was RATHER noisy at times, as this laptop usually runs a little hot... However, Ubuntu seems to not want to utilize the fan like Vista had been.

When checking the temp via the console, I get these results:
lucky@lucky-laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +100.0°C, crit = +100.0°C)  

That is the entire result...

Now, I know that 48 isn't particularly hot, but when the mousepad (area) is hot enough to BURN, it still only says 48 to 49... So is there a problem here? Or what...

I'm rather stumped. I have tried some of the other fixes I have read, but my problem seems to be rather different, as I can tell that the fan works... Just for very short periods of time, and it doesn't run particularly fast.

Is there anything else I can check, or try?

Someone help! I have seen a million different forum topics, and very few answers! Assuredly, someone knows a fix or work-around!

---

### Post by luckyfox on 2010-01-20
Bump

I have seen at **LEAST** a few dozen un-answered threads of this nature...

And **several** unanswered bug-reports... Whats going on??

---

### Post by arvevans on 2010-01-20
This is a recurring discussion/problem.  Do a Search on "Toshiba Fan" in this discussion group and you will find several answers that relate to your problem.

---

### Post by luckyfox on 2010-01-20
> **arvevans said:**
> Do a Search on "Toshiba Fan" in this discussion group

That is really my problem. There is VERY few answers to this problem, besides going back to Vista.

I have tried quite a few of the mentioned solutions, and have not had any luck. I only get one hit on a 'core temp' which seems to be rather invalid due to the extreme heat coming off of the machine.

Most of these fan posts either have an answer that doesn't work, or no answer at all.

Anything??

---

### Post by arvevans on 2010-01-20
Toshiba laptops, mine included, use ACPI firmware to control the fan, but it is not complete in it's own right.  The operating system (Windows, Linux, etc.) need to provide some control functions for the ACPI applets that operate the fan.

If you go to Synaptic Package Manater, and do a search for "Toshiba" the first two results talk about Linux drivers for controlling the fan on Toshiba laptops.  I installed "toshutils" first, then "fnfxd".  Not sure which fixed my fan problem, but now it runs when needed, and shuts down when not needed.

There is also a common problem with plugged fan ports, and with hair wound in the fan bearings (usually cat hair!).

Hope this helps.

Arv
_._

---

### Post by luckyfox on 2010-01-20
[QUOTE=arvevans;8698094]I installed "toshutils" first, then "fnfxd".

Update: terminal > sensors only results in the original outcome:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (high = +100.0°C, crit = +100.0°C)  

Currently Installed Packages related:
libsensors4
libsensors3
lm-sensors
xsensors
mbmon
xmbmon
eee-applet
libsensors-applet-plugin
sensord
toshutils
fnfxd
toshset
sensors-applet

ANY help is appreciated!

---

### Post by luckyfox on 2010-01-24
> **luckyfox said:**
> I have read around, and haven't seen anything like my particular problem.

No fix found. ):

Bought a cooling pad. Works, although had to sacrifice the mobility of the laptop.

Solved? ...Well, sorta.

---

