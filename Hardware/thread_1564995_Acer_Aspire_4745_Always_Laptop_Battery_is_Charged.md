---
title: "Acer Aspire 4745 Always Laptop Battery is Charged"
date: 2010-08-31
forum: Hardware
---

### Post by lordamit on 2010-08-31
UPDATE:
It is fixed when the bios is upgraded from 1.15 to 1.18

Hi.

I am using Ubuntu 10.04 in Acer Aspire 4745

This laptop is known for having some issues. But most of them are solvable.

Unfortunately, there is one little problem I can not fix yet. I searched as much as possible in many threads, but none gave any satisfactory answer.

**Problem:**

The gnome-power-manager always shows that "Laptop battery is charged" whether the ac power is plugged in or not.

**Ubuntu details:**

uname -a gives
```

Linux lordamit-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

```**Battery details:**

**cat /proc/acpi/battery/BAT1/info** gives:
```

present:                 yes
design capacity:         4400 mAh
last full capacity:      4400 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            BAT1      
serial number:           11        
battery type:            11        
OEM info:                11    


```**cat /proc/acpi/battery/BAT1/state** gives:

```
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         10000 mV
```Someone in some other person's problem suggested that kpowersave works in this similar situation. Please give me suggestions excluding the usage of kpowersave.

---

### Post by lordamit on 2010-09-01
The thing that just pissed me off is that it took me around 5 hours(Yeah, I have a slow internet) to download Ubuntu 10.10 Alpha 3 with the hope of battery and CD-Rom eject button issues solved.

The only problem solved was the sound, as the Alsa used there was of version 1.0.23

But still, the battery indicator shows that "Laptop Battery is charged" regardless of AC power plugged in or not.

And the same goes for the eject button.

Anyway, I tried system testing today, and found some interesting information.
here they are:

```
Handle 0x0014, DMI type 22, 26 bytes
Portable Battery
	Location: Fake
	Manufacturer: -Virtual Battery 0-
	Manufacture Date: 10/12/2007
	Serial Number: Battery 0
	Name: CRB Battery 0
	Chemistry: Lithium Ion
	Design Capacity: Unknown
	Design Voltage: Unknown
	SBDS Version: Not Specified
	Maximum Error: Unknown
	OEM-specific Information: 0x00000000
```
I do not know if they would be much of help, but I can hope.

Can someone please help?

---

### Post by su-37 on 2010-09-14
Ive got the same problem on another acer aspire.

---

### Post by ursnaresh on 2010-10-02
in my acer 4745
i have three problems they are

1.battery power is always chaarged

2.cd rom eject button is not working

3.headset is not working 

these 3 problems i am facing in ubuntu only they are working fine in windows 7


so someone kindly help me if you know abt these bugs...............

am new to  ubuntu

thanks in advance

---

### Post by kamakshaiah on 2010-12-16
Dear,
Can you please tell me how to upgrade bios in little detail. I downloaded bios software from Acer Official Website, and I refrained to upgrade, since it was suggested to do that with expert support. 
 
It interesting that you did it finally, will you please narrate me how to do that.
 
MKamakshaiah

---

### Post by srimanta on 2011-06-27
well if u have windows 7 also then you just have to get the bios update from the acer site and install the  .exe file present in the downloaded folder.

if you have ubuntu only then you have to go through a long  procedure

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

:guitar:

---

