---
title: "System freeze after adding RAM to PC."
date: 2012-06-15
forum: Hardware
---

### Post by przemnet on 2012-06-15
Hello Experts,

I had 2GB of RAM in my PC, I added another 2GB and after that system don't want to start up, it is freezed (screen is black or purple). When I remove 2GB than everything is OK, system starts normally. Memory is OK, Windows 7 starts normally when 4GB is installed and it is visible in the system.

I'm using 32 bit version of Ubuntu 12.04 LTS.

What should I check, what logs should I provide?

Looking forward,
Przemek.

**### SOLUTION ###**
Problem is partially solved- I disabled ATI drivers (I have AMD (ATI) Radeon HD 5670 graphic card) and now system boots, but I don't have graphics drivers...
I moved discussion to thread related to graphic drivers: _[http://ubuntuforums.org/showthread.php?p=12041414#post12041414](http://ubuntuforums.org/showthread.php?p=12041414#post12041414)_

---

### Post by sanderj on 2012-06-15
First things first:

With the 4GB installed, run memtest86 from the grub boot menu, and let it run for one night (or at least a few hours). See if it reports any errors.

---

### Post by przemnet on 2012-06-15
Hi,

yes, I'll run memtest tonight, but I don't think it will show something, because I have Windows 7 installed as well and it starts normally, 4GB of memory is visible in the system.

Besides I borrowed 1GB and system starts when there is 3GB installed, but it does not when 4GB is installed. Is there any limitation/setting in kernel to verify this?

Looking forward,
Przemek.

---

### Post by sanderj on 2012-06-15
Nope, no limit in the Linux kernel.

You can run my script from [http://www.appelboor.com/dump/check-my-hardware.py](http://www.appelboor.com/dump/check-my-hardware.py) to get info on your system.

Method:


```
wget http://www.appelboor.com/dump/check-my-hardware.py
sudo python check-my-hardware.py 
```

It will give you memory info about your BIOS, CPU, OS, etc.

---

### Post by Redblade20XX on 2012-06-15
Can you post the output of: 

```
sudo dmidecode -t 6
```

-Red

---

### Post by przemnet on 2012-06-15
Hello,

problem is partially solved- I disabled ATI drivers (I have ATI HD5670 graphic card) and now system boots, but I don't have graphics drivers:confused:

I can not use drivers proposed by system, I tried to download and install drivers from ati webside by following these instructions [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)
Packages were generated succesfully, but during *deb files installation there were some errors...

Here is the output of fglrxinfo:
```
root@ubuntuLTS:/home/przemek# fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
root@ubuntuLTS:/home/przemek#
```

free -m shows 4GB of RAM:
```
root@ubuntuLTS:/home/przemek# free -m
             total       used       free     shared    buffers     cached
Mem:          4027       1003       3023          0         39        348
-/+ buffers/cache:        615       3411
Swap:            0          0          0
root@ubuntuLTS:/home/przemek# 

```

And the output of dmidecode is below:
```
root@ubuntuLTS:/home/przemek# dmidecode -t 6
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 1
	Current Speed: 77 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2
	Current Speed: 77 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A2
	Bank Connections: 3
	Current Speed: 77 ns
	Type: Other Unknown EDO
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A3
	Bank Connections: 4
	Current Speed: 77 ns
	Type: Other Unknown EDO
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

root@ubuntuLTS:/home/przemek# 

```

Do you have any idea what may be wrong??? What should I check regarding ATI drivers installation failure???

Looking forward,
Przemek.

---

### Post by przemnet on 2012-06-20
I moved discussion to thread related to graphic drivers: [http://ubuntuforums.org/showthread.php?p=12041414#post12041414](http://ubuntuforums.org/showthread.php?p=12041414#post12041414)

Looking forward,
Przemek.

---

### Post by przemnet on 2012-07-20
Hello Everyone!

Problem is SOLVED!

As per recommendation from fglrx bugtracker- BIOS upgrade on my motherboard (Gigabyte GA-MA69G-S3H) was the solution! I upgraded to the newest version which is F8E. I was able to install latest Catalyst 12.6 drivers succesfully.

I had problems with upgradeing BIOS from Windows XP and Windows 7, but upgrade directly from BIOS with Q FLASH worked perfectly! To do it, just download BIOS from Gigabyte site, extract the archive, copy BIOS file to USB stick, plug USB stick into computer, reboot system, hit "End" button during startup and select BIOS upgrade from HDD- you can find lots of videos on YouTube about that.

Many thanks for your help and support!

Looking forward,
Przemek.

---

