---
title: "CPU overheating issues: where to submit the bug report?"
date: 2012-09-20
forum: Hardware
---

### Post by Jack Kelly on 2012-09-20
**Brief description of the problem**
I and many other people (just search this forum for "overheating"!) have found that their laptop CPUs get insanely hot when running Linux because the CPU fan does not turn on.  Or, to be more specific, the fan turns on when the laptop first turns on, remains on during BIOS POST, grub and the first few seconds of Linux's boot process but then turns off and stays off until the CPU gets near its critical temperature.

In my case, the CPU fan doesn't turn on until the CPU gets to 105 degrees C (that's not a typo: I do mean 5 degrees above the boiling point of water!  That temp is reported by the temp sensor on the CPU using the coretemp module, and I've double-checked using an IR thermometer pointed at the CPU heatsink).

I've read many, many forum theads on this issue.  I'm pretty confident there isn't a simple fix.  So what I need to know is: where do I report this bug?

Lots more details of this issue:

**This isn't a hardware issue**
The failure of the fan to start isn't a hardware issue: the fan is free from dust and the fan runs perfectly in Windows 7 / grub / the laptop BIOS screen.

**What's so bad about 105 degrees C?**
The processor's specification sheet states that the processor (an i5) can handle a max temp of 105 degrees C.  But the plastic keyboard immediately above the CPU almost certainly can't!  And my lap can't either.  And the motherboard probably doesn't enjoy the thermal stresses either.  There are reports on this forum of motherboards needing to be replaced and over forced shutdowns due to overheating.  So, however you look at it, a laptop CPU should never be allowed to get anywhere near 105 degrees C.  Windows 7 keeps the CPU below 70 degrees C, even under heavy load.

The fact that Linux allows the CPU to get so hot is a very serious bug IMHO.  As far as I'm concerned, bugs which can potentially wreck expensive hardware are a high priority.

**The desired fix**
The problem is not to do with throttling the CPU.  The problem is really very simple: the fan should just be on all the time.  (I'm seriously considering just permanently connecting power to the fan.)

**Things I've tried**
_Alternative Linux distros_
I'm running Ubuntu 12.04 64-bit so I thought I'd try some alternatives.  They all exhibited exactly the same behaviour of the fan:
[LIST]
[*]Fedora 17 64-bit live CD (kernel 3.3.4)
[*]Ubuntu 12.10 64-bit live CD (kernel 3.5)
[*]Ubuntu 12.04 32-bit live CD (kernel 3.2)
[*]Ubuntu 11.10 64-bit live CD
[*]Ubuntu 11.04 64-bit live CD
[*]Ubuntu 10.10 64-bit live CD
[/LIST]

_[FONT="Courier New"]lm-sensors[/FONT] and [FONT="Courier New"]fancontrol[/FONT]_
I ran [FONT="Courier New"]sensors-detect[/FONT]. It told me to add the [FONT="Courier New"]coretemp[/FONT] module to [FONT="Courier New"]/etc/modules[/FONT], which I did.  [FONT="Courier New"]sensors[/FONT] reports the temperature of both my physical CPU cores.  [FONT="Courier New"]pwmconfig[/FONT] complains that "There are no pwm-capable sensor modules installed" so I can't use [FONT="Courier New"]fancontrol[/FONT].

_[FONT="Courier New"]i8kutils[/FONT]_
Just reports the fans are set to "-1" and refuses to change them.  (Yes, [FONT="Courier New"]i8kmon[/FONT] is loaded.)

_Tinkering with the [FONT="Courier New"]/proc/[/FONT] or [FONT="Courier New"]/sys/[/FONT] file system_
I don't have a [FONT="Courier New"]/proc/acpi/fan[/FONT] directory. The directories [FONT="Courier New"]/sys/class/thermal/thermal_zone?/[/FONT] appear to only describe a few heat sensors on the motherboard (not the CPU temperatures reported by [FONT="Courier New"]coretemp[/FONT]) and I can't seem to modify the [FONT="Courier New"]trip_point_0_temp[/FONT] files.

The CPU temps seem to live in [FONT="Courier New"]/sys/class/hwmon/hwmon1/device[/FONT].  If I attempt to change the max from 95 degrees C to 50 degrees C by running [FONT="Courier New"]sudo bash -c "echo 50000 > /sys/class/hwmon/hwmon1/device/temp2_max"[/FONT] I get the following error: [FONT="Courier New"] bash: /sys/class/hwmon/hwmon1/device/temp2_max: Permission denied[/FONT]

When my CPU fan does run (i.e. when the CPU temp gets near to 105 degrees C) nothing changes in [FONT="Courier New"]/sys/class/thermal/cooling_device?/cur_state[/FONT].  i.e. Linux doesn't appear to acknowledge that the fan has started to run.

Incidentally, Hardware Monitor (running under Windows) can't find my CPU fan either (but the fan just magically works under Windows).  So clearly my fan isn't exposing itself very clearly to the OS.

_Boot options_
The following all had no effect:
[list]
[*][FONT="Courier New"]acpi.power_nocheck=1[/FONT]
[*][FONT="Courier New"]acpi_osi=Linux[/FONT]
[*][FONT="Courier New"]acpi_osi=linux[/FONT]
[*][FONT="Courier New"]acpi_osi=Windows[/FONT]
[*][FONT="Courier New"]acpi=strict[/FONT]
[/list]

The only thing I tried which had any effect on my CPU fan was starting with the boot option [FONT="Courier New"]acpi=off[/FONT].  This allowed the fan to continue spinning even while Ubuntu was running.  But completely disabling ACPI isn't a workable option for a production system.

_Talking directly to the fan controller over I2C_
I guessed that my fan controller might be connected to the southbridge via I2C.  So I tinkered with [FONT="Courier New"]i2c-tools[/font] but [FONT="Courier New"]i2cdetect[/font] always complained that the [FONT="Courier New"]/dev/i2c-?[/font] files were not valid I2C devices.  I tried loading a number of i2c-related modules but to no avail.

**What's controlling my CPU fan?  The ACPI subsystem?**
The evidence is somewhat contradictory.  On the one hand, setting the boot option  [FONT="Courier New"]acpi=off[/FONT] successfully enables the fan, which suggests that the ACPI subsystem is switching off my fan during a normal boot.  On the other hand, there's a bunch of evidence suggesting the fan isn't controlled by ACPI on this laptop:

I dissassembled my DSDT and found that [FONT="Courier New"]PNP0c0b[/font] is not present (which apparently is the code for a fan controller).  Also, the evidence above in the "Tinkering with the [FONT="Courier New"]/proc/[/FONT] or [FONT="Courier New"]/sys/[/FONT] file system" section would suggest that my fan's controller isn't exposed over ACPI (or, alternatively, it is exposed over ACPI but Linux doesn't know how to handle it).

**My guess at what's happening**
This is total guess work but I think this is how it's working at the moment: [FONT="Courier New"]coretemp[/font] queries the CPU and finds that it can handle max temp of 105 degrees C.  [FONT="Courier New"]coretemp[/font] is not responsible for controlling the fan (apparently) so some other subsystem (hwmon?  acpi?  the BIOS?) must be taking the max temperatures stated by [FONT="Courier New"]coretemp[/font] and using these as the set points for the fan.  Without allowing me, the user, any input.  Not cool.  If I wanted to use an OS which bans the user for modifying interesting system parameters I would've bought myself a Mac ;)

**My system config**
HP ProBook 6450b with 4GB of RAM and a magnetic hard disk.  I'm running the latest HP BIOS.

From CPU-Z (running on Windows):

_CPU_
	Name		=	Intel Core i5 450M.  Two cores, each with 2 threads.
	Codename	=	Arrandale
	Specification =	Intel(R) Core(TM) i5 CPU       M 450  @ 2.40GHz
	Package (platform ID) =	Socket 989 rPGA (0x4)
	CPUID		= 6.5.5
	Extended CPUID	=	6.25
	Core Stepping	=	K0

_Chipset_
Northbridge		=	Intel Havendale/Clarkdale Host Bridge rev. 02
Southbridge	=		Intel HM57 rev. 05
Memory Type =			DDR3

_Monitoring_
Mainboard Model =		146D (0x000000DF - 0x00002220)
LPCIO Vendor	=	SMSC
LPCIO Vendor ID	=	0x55
LPCIO Chip ID	=	0x4C

**Summary**
So, in summary: I'm 99% sure there's a bug in there somewhere.  The fan really, really should turn on long before the CPU gets anywhere near 105 degrees C.  I guess I have two questions: firstly, does anyone know a fix?!  If not, does can anyone suggest to which bug reporting system I should submit this bug?  It appears to be associated with the Linux kernel rather than Ubuntu.  But to which linux subsystem dev team should I submit the bug?

---

### Post by einonm on 2012-09-21
The drivers that control temperature sensing and fan control are part of the Linux kernel (/drivers/hwmon) - so your best bet is to post to the relevant kernel mailing list. Just give the relevant kernel version, hardware specs and issue description.

On a recent checked out kernel tree, I can run the scripts/get_maintainer.pl script on the directory, which gives:

$: ~/Source/staging$ scripts/get_maintainer.pl -f drivers/hwmon/
Jean Delvare <khali@linux-fr.org> (maintainer:HARDWARE MONITORING)
Guenter Roeck <linux@roeck-us.net> (maintainer:HARDWARE MONITORING)
[email]lm-sensors@lm-sensors.org[/email] (open list:HARDWARE MONITORING)
[email]linux-kernel@vger.kernel.org[/email] (open list)

So I'd try posing a message with your issue to the list at [email]lm-sensors@lm-sensors.org[/email] (there's probably no need to post to [email]linux-kernel@vger.kernel.org[/email]).

---

### Post by Jack Kelly on 2012-09-24
That's great, thanks loads for the reply!

[I posted to lm-sensors](http://lists.lm-sensors.org/pipermail/lm-sensors/2012-September/037258.html) as you suggested and Guenter suggested that I should post to the linux-acpi list, which I have just done.

Thanks again for your reply.
Jack

---

### Post by einonm on 2012-09-24
No problem. If you do find a solution (or anything of interest) please remember to note it on the thread and mark is as resolved!

---

### Post by madtom1999 on 2012-09-30
I've been wrestling with a PC desktop that ran fine under 11.10 and under 12.04 just runs the cpu fan at one speed and overheats when CPU usage gets high -its 4 core so ok for most thing but not all!

---

### Post by Jack Kelly on 2012-10-09
A quick update:

I've been discussing this issue on the Linux ACPI list.  The full discussion is available here: [http://comments.gmane.org/gmane.linux.acpi.devel/55802](http://comments.gmane.org/gmane.linux.acpi.devel/55802)

---

### Post by Jack Kelly on 2012-11-26
I failed to find a software fix so I did a hardware fix!  Details and photos on my blog: [http://jack-kelly.com/ensuring_the_fan_runs_on_my_hp_probook_6450b_laptop](http://jack-kelly.com/ensuring_the_fan_runs_on_my_hp_probook_6450b_laptop)

---

### Post by LuciferRex on 2012-11-26
Love it!  Glad I don't have that issue.  My favorite part was [quote]I'm just some dude from the internets. [quote]

---

### Post by LuciferRex on 2012-11-26
Love it!  Glad I don't have that issue.  My favorite part was > I'm just some dude from the internets.

---

### Post by Jack Kelly on 2012-11-26
Glad you like it ;)

---

### Post by Shuudoushi on 2012-11-26
Go into your BIOS; find fan speed/control/temp control and change the temp at which the fan kicks on. This is a bios problem not hardware or OS.

---

### Post by Shuudoushi on 2012-11-26
Also please remember to mark solved problems with the [SOLVED] tag found in the thread tools.

---

### Post by Jack Kelly on 2012-11-26
> **Shuudoushi said:**
> Go into your BIOS; find fan speed/control/temp control and change the temp at which the fan kicks on. This is a bios problem not hardware or OS.

Please (re)read my original post.  The specific issue described in this thread is most definitely is not something that can be fixed with a simple BIOS setting (that was the first thing I tried.)

***edit*** Actually, sorry, you're right: I had forgotten to mention in my OP that I had already tried to fix this issue using a BIOS setting.  I'll edit my  OP.

***edit of my previous edit*** Turns out I can't edit my OP now  so I'll mention it here:  IIRC, there is a BIOS setting which mentions the fan.  This BIOS setting has two settings.  I tried both settings but no joy.  I searched several times through the BIOS for other options but no joy.  You're absolutely right that if we lived in a sane and fair world then this problem should be fixed in 30 seconds with a simple tweak of a BIOS setting.  But my HP ProBook doesn't have a useful BIOS setting to do that.  From which we can infer that we definitely do not live in a sane or fair world ;)

---

### Post by Shuudoushi on 2012-11-26
> **Jack Kelly said:**
> Please (re)read my original post.  The specific issue described in this thread is most definitely is not something that can be fixed with a simple BIOS setting (that was the first thing I tried.)

Lol np :P

---

