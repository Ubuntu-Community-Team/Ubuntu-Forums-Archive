---
title: "govern my CPU for performance?"
date: 2011-12-09
forum: Hardware
---

### Post by jmate24 on 2011-12-09
How do i govern my CPU for performance and make it so that it stays on performance for every boot?

---

### Post by MG&amp;TL on 2011-12-09
> **jmate24 said:**
> How do i govern my CPU for performance and make it so that it stays on performance for every boot?

Err...I guess by your signature that you don't mean overclocking?

I understand cpufreq will do this-
You could look at this: [http://www.ibm.com/developerworks/linux/library/l-cpufreq-1/index.html]("http://www.ibm.com/developerworks/linux/library/l-cpufreq-1/index.html") although obviously you need to tweak stuff in the opposite direction.

A few more hints as to what you are after?

---

### Post by TBABill on 2011-12-09
I think you can install CPUFREQ TOOLS and then ```
sudo cpufreq-set --governor performance
``` You may need to designate it for each cpu the system identifies, but the man page for cpufreq should help with that.

---

### Post by jmate24 on 2011-12-09
well i use amd 640 x4 processor and i once found on the forums how to set my cpu_frequency_govenor or some kind of setting like it in the /usr/....? folder using the terminal to set it then i added it to my rc.local file by starting the command with sudo so that it would be at performance at every boot but i cannot find it any more i even tried looking at my bookmarks and i cannot find it (the page/thread where it tells how to do it that way because i have tried it with cpufreqd and it did not work and the command is:

sudo cpufreq-set -g performance. but this command changed nothing the other command changed it i use lubuntu 11.10 and it's governor app does not allow for me to change the frequency i have to use the command line and i have all ready installed all of the tools and the sensord and lm-sensors and sensors including the cpufreq and cpufreq-tools and still no joy.

---

### Post by MG&amp;TL on 2011-12-09
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

Might want to look at that.

---

### Post by MoreOrLess on 2011-12-10
> sudo cpufreq-set -g performance. but this command changed nothing
On my laptop with Debian, I have to do each core separate (using -c). That said, the ondemand governor does a good job, and setting the governor to performance all of the time is just a waste of power in a lot of cases.

---

### Post by Dlambert on 2011-12-10
And the creator of un necessary mounds of heat! #-o

---

### Post by jmate24 on 2011-12-10
i don't think i need cron to set it i just need it to be on performance at every boot and i already set the processors to performance in the  /sys/devices/cpu/cpu*/... folder and it seems to be working when i used the RHEL instructions on how to set performance but i had to do it for each individual cpu core.

---

### Post by MoreOrLess on 2011-12-11
You can run the commands at boot using /etc/rc.local

---

### Post by jmate24 on 2011-12-12
i tried that with sudo cpufreq-set --governor performance but there was no joy it just said ondemand i how ever was able to go into the /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor and edit it with leafpad or gedit and change it from ondemand to performance and that works but i have to do it for every processor at every boot or every time i change from lubuntu to lxde or gnome.

i would like a unified way to start them at performance all the time using rc.local but not with sudo cpufreq-set --governor performance because it does not work.

there is another command out there that makes it performance at the start up if you put it into rc.local but i have to make sure that it is running by entering it into the terminal after i login and i don't want to have to do that i just want it to stay at performance. but i don't remember the command or the link to where i can get the commmand i know that it is in ubuntuforums i just don't know where i might try to google it.

i've had it before i just had my hdd die and i needed to replace it so i lost it.

---

### Post by MG&amp;TL on 2011-12-13
From some googling, cpufreq is the way to do things; how does it not work?

Why do you need it on full performance all the time; ondemand means it will compensate when it needs, right? Running it at full capacity all the time is a waste of power.

[http://www.google.co.uk/search?gcx=c&sourceid=chrome&ie=UTF-8&q=how+to+control+cpu+linux]("http://www.google.co.uk/search?gcx=c&sourceid=chrome&ie=UTF-8&q=how+to+control+cpu+linux")

---

### Post by jmate24 on 2011-12-15
i do not have a laptop i have a pc and i rip and  make my own home movies plus, if i don't do it then the movies i rip take 2-5x longer to rip or encode and decode them. I use WinFF, Thoggen, OggConvert and for my music I use Banshee and SoundConverter.

i have the latest kernel 3.0.0-12.20
I am using an AMD Athlon II X4 640 3.0Ghz Processor
16GB G.SKILL SNIPER DDR3-1866 PC314900 CL9-10-9-28 1.5V Memory
ATI Radeon HD5670 1GB GDDR5 Video Card w/a Acer LCD H203H Flat screen
2 Optiarc CD/DVD Writers and 1 ATAPI iHAS124 B writer
1 Apple Keyboard and Mouse (both wired)
M4A88T-V EVO/USB3 <GREEN> AM3,AMD 880G, SB710, Dual-CH DDR3 2000 O.C. 8+1 phase, CrossfireX, 128MB Sideport Video Memory, 1394 Firewire, 8-CH Core Unlocker up to 6 cores, Turbo Key II, TurboV EVO, EPU, 100% Solid Cap., Win7 Ready!, USB3.0
500W Dual 12V Rail Powersupply
750GB Segate HDD.

---

### Post by MG&amp;TL on 2011-12-16
OK, thanks for your hardware stats; maybe someone will be able to make something of them; but what doesn't work when you try cpufreq?

---

### Post by jmate24 on 2012-01-01
> **jmate24 said:**
> i do not have a laptop i have a pc and i rip and  make my own home movies plus, if i don't do it then the movies i rip take 2-5x longer to rip or encode and decode them. I use WinFF, Thoggen, OggConvert and for my music I use Banshee and SoundConverter.

i have the latest kernel 3.0.0-12.20
I am using an AMD Athlon II X4 640 3.6Ghz Processor
16GB G.SKILL SNIPER DDR3-1866 PC314900 CL9-10-9-28 1.5V Memory
ATI Radeon HD5670 1GB GDDR5 Video Card w/a Acer LCD H203H Flat screen
2 Optiarc CD/DVD Writers and 1 ATAPI iHAS124 B writer
1 Apple Keyboard and Mouse (both wired)

[M4A88T-V EVO/USB3 <GREEN> AM3,AMD 880G, SB710, Dual-CH DDR3 2000 O.C. 8+1 phase, CrossfireX, 128MB Sideport Video Memory, 1394 Firewire, 8-CH Core Unlocker up to 6 cores, Turbo Key II, TurboV EVO, EPU, 100% Solid Cap., Win7 Ready!, USB3.0]
500W Dual 12V Rail Powersupply
750GB Segate HDD.

--I just replaced the mother board above for a new one because it was frying itself (shorting out) with this one:

MSI 880GM-E43, AM3, AMD880G+SB710, 4*DDR3, Gb LAN ,5 SATA, 1 PATA, 1 Floppy, Military Class Cooling 20 Degrees C lower temp, Active Phase Switching, Easy OC Switch, Unlock CPU Core, HDMI ATI 4250
500W Dual 12V Rail Powersupply
750GB Segate HDD
500GB WD HDD.
but i figured out how to set it in the bios with this new motherboard so that the processor does not step down.

thanx.

---

