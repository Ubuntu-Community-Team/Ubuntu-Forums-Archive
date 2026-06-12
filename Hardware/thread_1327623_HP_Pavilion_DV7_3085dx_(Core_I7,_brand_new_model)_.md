---
title: "HP Pavilion DV7 3085dx (Core I7, brand new model) + Ubuntu... Issues galore"
date: 2009-11-15
forum: Hardware
---

### Post by bwmcadams on 2009-11-15
(Running 9.10, Karmic, with latest updates)

So, I'm hoping that posting as much as I know will get me some responses to help me along on this.  I recently acquired a new laptop, an HP 17" with Core I7; it's the 3085dx which is the off-the-shelf Best Buy version (yes, I know, but I needed a machine quickly and that was best option).

6 Gigs of DDR3, discreet Nvidia GPU (1 gig dedicated), 500 gig SATA disk, etc.

It seems HP has been less than forthcoming in providing proper Linux support (something I didn't expect as for me, stuff has always just worked).  It ships w/ Windows 7 and HP's official response seems to be on the pavilion and envys that "we certify for Windows Vista/7 and provide no support past that".  After getting past HP shipping the machine with 4 primary partitions defined for Windows, I got Ubuntu running with mostly no issues.  I had noticed when I reboot after being in ubuntu that I get a "Your machine has been running hot, please check fans arent blocked" warnings, which I've chalked up to simply some software probe not reporting back to the BIOS.

The one other issue I've had is a failure to wake up from suspend.  It works fine in Windows of course, but under Ubuntu when I wake the machine up I get a blank screen with a blinking white cursor.  I've tried adjusting the configs to turn reposting video on and off, to no luck.  As I was digging around I found some stuff about ACPI and found out my machine was in fact overheating, as the system wasn't properly managing fans.  I also found in dmesg "Unable to parse ACPI, possibly buggy BIOS" messages.  I added a suggested option of acpi_osi=!Linux to kernel parameters - my temp sensors are SIGNIFICANTLY lower now and I notice the fans running, although I still get the "BIOS Overheat" warning at reboot. I also get about 8 pages more of ACPI output and ACPI seems to boot more correctly now however.

I'm now of course concerned about everything not working.  I'm more concerned of the system overheating due to not talking to the BIOS correctly, not being able to suspend, etc.  While Windows 7 is not nearly as bad as past attempts, it still isn't suitable for my needs.

I'm looking for any and all help to nail down full support for Fan control and temperature sensors on this machine, making suspend work, etc etc.  I've attached sanitized dmesg, dmidecode and lshw output.  I'm happy to provide other output as needed but looking for a solid direction to head in to resolve any outstanding issues on this.  Windows is not an option, and I've come to the realization of shortcomings too late to return the box at this point.

-b

---

### Post by gordintoronto on 2009-11-15
Have you tried lm-sensors and sensors-applet?  Try searching in Synpatic.

---

### Post by bwmcadams on 2009-11-15
Yes, these just report sensor data.  They don't fix the fact that the machine is NOT running the fans properly, or that it won't suspend...

---

### Post by sinus0 on 2009-11-17
> **bwmcadams said:**
> (Running 9.10, Karmic, with latest updates)

So, I'm hoping that posting as much as I know will get me some responses to help me along on this.  I recently acquired a new laptop, an HP 17" with Core I7; it's the 3085dx which is the off-the-shelf Best Buy version (yes, I know, but I needed a machine quickly and that was best option).

6 Gigs of DDR3, discreet Nvidia GPU (1 gig dedicated), 500 gig SATA disk, etc.

It seems HP has been less than forthcoming in providing proper Linux support (something I didn't expect as for me, stuff has always just worked).  It ships w/ Windows 7 and HP's official response seems to be on the pavilion and envys that "we certify for Windows Vista/7 and provide no support past that".  After getting past HP shipping the machine with 4 primary partitions defined for Windows, I got Ubuntu running with mostly no issues.  I had noticed when I reboot after being in ubuntu that I get a "Your machine has been running hot, please check fans arent blocked" warnings, which I've chalked up to simply some software probe not reporting back to the BIOS.

The one other issue I've had is a failure to wake up from suspend.  It works fine in Windows of course, but under Ubuntu when I wake the machine up I get a blank screen with a blinking white cursor.  I've tried adjusting the configs to turn reposting video on and off, to no luck.  As I was digging around I found some stuff about ACPI and found out my machine was in fact overheating, as the system wasn't properly managing fans.  I also found in dmesg "Unable to parse ACPI, possibly buggy BIOS" messages.  I added a suggested option of acpi_osi=!Linux to kernel parameters - my temp sensors are SIGNIFICANTLY lower now and I notice the fans running, although I still get the "BIOS Overheat" warning at reboot. I also get about 8 pages more of ACPI output and ACPI seems to boot more correctly now however.

I'm now of course concerned about everything not working.  I'm more concerned of the system overheating due to not talking to the BIOS correctly, not being able to suspend, etc.  While Windows 7 is not nearly as bad as past attempts, it still isn't suitable for my needs.

I'm looking for any and all help to nail down full support for Fan control and temperature sensors on this machine, making suspend work, etc etc.  I've attached sanitized dmesg, dmidecode and lshw output.  I'm happy to provide other output as needed but looking for a solid direction to head in to resolve any outstanding issues on this.  Windows is not an option, and I've come to the realization of shortcomings too late to return the box at this point.

-b


Hi

I have exactly the same problem on dv7-3090er. Obviously it affects the whole dv7-30xx family. I found that kernel doesn't sees any sensors to read temperature, etc. No surprise it believes that CPU is cool. 
BTW how do you read temperatures ? I'm trying to play with it a bit but it's hard without actual temperatures.

---

### Post by gordintoronto on 2009-11-17
> **sinus0 said:**
> Hi

I have exactly the same problem on dv7-3090er. Obviously it affects the whole dv7-30xx family. I found that kernel doesn't sees any sensors to read temperature, etc. No surprise it believes that CPU is cool. 
BTW how do you read temperatures ? I'm trying to play with it a bit but it's hard without actual temperatures.

Have a look at lm-sensors.  However, it might not support the I7.  I have a Phenom II, and it is not supported.

If you reboot, you can probably get the CPU temperature reading in the BIOS setup somewhere.  I forget exactly where it appears on my machine, but it's there.

---

### Post by sinus0 on 2009-11-25
> **gordintoronto said:**
> Have a look at lm-sensors.  However, it might not support the I7.  I have a Phenom II, and it is not supported.

If you reboot, you can probably get the CPU temperature reading in the BIOS setup somewhere.  I forget exactly where it appears on my machine, but it's there.

They're blind. lm-sensors provides only HDD temperature. However I was able to make lm-sensors detect termal zones with "acpi_osi="Linux"". Sensors came up and were showing 58-60 C. With no chance to make fan cool them. Last idea I have about is a buggy DTST table in ACPI. It does have abuggy code from the vendor, but errors seem to be of language scope or structure rather than algorithmic. I'd love to spend a week or so learning ASL but do not have that much time. PLaced a post on the DTST bugfixing forum - hopefully they could help me with that.

---

### Post by Qaranthir on 2009-12-15
The "overheating"-warning is gone with the nu BIOS-update:
[ftp://ftp.hp.com/pub/softpaq/sp46501-47000/sp46749.exe](ftp://ftp.hp.com/pub/softpaq/sp46501-47000/sp46749.exe)
Read the thread at the HP-support-forum:
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-questions/dv7-3085dx-Bios-updates/td-p/157612/page/12](http://h30434.www3.hp.com/t5/Other-Notebook-PC-questions/dv7-3085dx-Bios-updates/td-p/157612/page/12)

This program updates the current BIOS version (F.04) to the newest (F.13).

---

### Post by uilton on 2010-03-31
The BIOS update is unavailable on HP ftp server. Qaranthir could you send me the file?

---

### Post by Qaranthir on 2010-04-03
> **uilton said:**
> The BIOS update is unavailable on HP ftp server. Qaranthir could you send me the file?
[http://dl.dropbox.com/u/4973635/sp46749.exe](http://dl.dropbox.com/u/4973635/sp46749.exe)

---

