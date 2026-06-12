---
title: "Dell Inspiron Fan Fix?"
date: 2010-12-03
forum: Hardware
---

### Post by fallofshadows on 2010-12-03
So I've seen how the Dell Inspiron 1545 seems to run at a slightly high temperature. I Generally average in the 50-60 degree C range, although for some reason it's behaving right now at 46 C...

A search online showed me these results, and I wanted the opinions of people who know what they're talking about. Is this a safe idea? I don't want to input anything in my computer that would screw it up.

Here is the explanation and a possible solution for your laptop. It's  the BIOS. Most laptop computers are designed specifically for Windows.  Therefore, on many models, the BIOS does not control the fan, as is  normally the case, but they depend on Windows Power Management.  Obviously, Ubuntu is not windows. Therefore, the kernel must manage the  fans. Sadly, a majority of laptops do not need this, so the default  Ubuntu setup doesn't account for the minority, and far be it for the  designers to make all easy and automatic like, detection wise. So this  is left up to the user to try and fail to find an answer in the vast  twisted jungle of hostiles and beasts known as the Linux community of da  interwebz.
 Fret not, however. You just need to modify GRUB2, which is what boots  Ubuntu, essentially, and input a kernel command that will tell it to  manage your fan. The following should work. If it doesn't, sorry. But it  really should work.
  
 In Ubuntu (version 10.04 and up)...
 Push Alt+F2.
 Type (without quotes, obviously) 'gksu nautilus'. Push Enter (or Return). 
 Enter your password, if necessary.
 In the new administrative-be-righted Nautilus File Manager window  that has just opened, navigate to 'File System' in the left side panel,  then navigate to the 'etc' folder, then navigate to the 'default'  folder, then open the 'grub' file. Good.
 In the new gedit text editor window that has just opened up, look for the line that reads: GRUB_CMDLINE_LINUX=""
 Now, precisely between the two quotes, without any spaces, copy and paste this exactly: acpi_osi=\"Linux\"
 The line should now look like this: GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
 Save the file and exit the gedit text editor.
 Now, open the Terminal (Applications>Terminal).
 Type: sudo update-grub
 Press Enter (or Return) and wait...
 Wait...
 Has the text stopped moving? If so, you're almost done.
 Exit the terminal.
 Reboot.
 Now the correct kernel/fan behavior has been activated and the fan  will work as it should and your excessive heat Ubuntu laptop problems  are solved. You're cured. Do something else. Carry on. Don't worry. Be  happy. You're welcome. Good luck. Goodbye.

---

### Post by tommcd on 2010-12-03
> **fallofshadows said:**
> 
A search online showed me these results, and I wanted the opinions of people who know what they're talking about. Is this a safe idea? I don't want to input anything in my computer that would screw it up.

 acpi_osi=\"Linux\"
 The line should now look like this: GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""

This should not cause you any problems. Go ahead and try it. If you have problems then write back for more help. 
Just out of curiosity, can you post a link to this info?
You could always remove the stuff you add to /etc/default/grub if it does not fix your problem.

---

### Post by Jimtheplanner on 2010-12-04
Hi Guys I gave it a try it originates from [http://www.maximumpc.com/article/news/ubuntu_1010_%E2%80%9Cmaverick_meerkat%E2%80%9D_officially_released]("http://www.maximumpc.com/article/news/ubuntu_1010_%E2%80%9Cmaverick_meerkat%E2%80%9D_officially_released")

It did not make any large difference for me but its worth a try. My best option is to start my laptop up on the battery wait a minuet or two then plug in the mains. This way my laptop remains cool for the remainder of the session.

Hope this helps....

Jim

---

### Post by fallofshadows on 2010-12-04
I'll post a link when I'm back on my computer.

The fix has worked fine for me :) I watched my temperature gauge while playing minecraft, it looks like my laptop warms up to 65 degrees C before the fan kicks on, which knocks the temp down to the 40s. It seems like it's acting like it does on windows, so yay!

And I've also noticed that I'm able to play minecraft on higher graphics. Weird, since windows is supposed to be more powerful in the graphics department. Oh well, I am definitely not complaining!

---

### Post by tommcd on 2010-12-05
> **fallofshadows said:**
> 
The fix has worked fine for me :) I watched my temperature gauge while playing minecraft, it looks like my laptop warms up to 65 degrees C before the fan kicks on, which knocks the temp down to the 40s. It seems like it's acting like it does on windows, so yay!

Glad it worked for you!
Just out of curiosity (*yes, I am a curious fellow!*), can you post your output of **lscpi** from the terminal so we can see exactly what hardware this fix works on. This may be beneficial to other folks who have this problem.

---

### Post by fallofshadows on 2010-12-07
Sorry I didn't get back to you sooner, I somehow forgot to check the forums!

fallofshadows@fallofshadows-Inspiron-1545:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


I hope this helps! I know it's solved my problems, so hopefully it does the same for anyone else with a dell inspiron. I've had quite a few problems getting started, but now that they're solved, I love ubuntu!

---

### Post by Unisio on 2012-05-07
I have the same problem with high temperatures on an Inspiron 1545 laptop. The fix did not work for me and there's another guide in thread [http://ubuntuforums.org/showthread.php?t=1636686](http://ubuntuforums.org/showthread.php?t=1636686) that did not work either.

Has anyone come up with a solution to this problem?

---

### Post by pierreu1 on 2012-08-19
Note I do not have a Dell. See the signature for compete specs. 5 year old laptop. I would love to try the following, but it asks me for a user that I don't have the password for. I log in, for security, with another user. I tried to use many of the potential passwords I used (from time to time) for the (main) user, but I cannot remember it since I haven't used this way to log in for more than one year. I should have written it somewhere. In any case, is there a way I can do this as sudo in the terminal window? Or is there another way?

My fan was working, but not enough to cool down the machine. I tried to follow some fixes, but they disabled my fan (it looks like). This was in Oneiric. In desperation, I upgraded to Pangolin in the hope the upgrade would fix this, but it --obviously--did not.

Thank you for your help. (I am learning Ubuntu, but I am not good .... yet! :) )


> **fallofshadows said:**
> So I've seen how the Dell Inspiron 1545 seems to run at a slightly high temperature. I Generally average in the 50-60 degree C range, although for some reason it's behaving right now at 46 C...

A search online showed me these results, and I wanted the opinions of people who know what they're talking about. Is this a safe idea? I don't want to input anything in my computer that would screw it up.

Here is the explanation and a possible solution for your laptop. It's  the BIOS. Most laptop computers are designed specifically for Windows.  Therefore, on many models, the BIOS does not control the fan, as is  normally the case, but they depend on Windows Power Management.  Obviously, Ubuntu is not windows. Therefore, the kernel must manage the  fans. Sadly, a majority of laptops do not need this, so the default  Ubuntu setup doesn't account for the minority, and far be it for the  designers to make all easy and automatic like, detection wise. So this  is left up to the user to try and fail to find an answer in the vast  twisted jungle of hostiles and beasts known as the Linux community of da  interwebz.
 Fret not, however. You just need to modify GRUB2, which is what boots  Ubuntu, essentially, and input a kernel command that will tell it to  manage your fan. The following should work. If it doesn't, sorry. But it  really should work.
  
 In Ubuntu (version 10.04 and up)...
 Push Alt+F2.
 Type (without quotes, obviously) 'gksu nautilus'. Push Enter (or Return). 
 Enter your password, if necessary.
 In the new administrative-be-righted Nautilus File Manager window  that has just opened, navigate to 'File System' in the left side panel,  then navigate to the 'etc' folder, then navigate to the 'default'  folder, then open the 'grub' file. Good.
 In the new gedit text editor window that has just opened up, look for the line that reads: GRUB_CMDLINE_LINUX=""
 Now, precisely between the two quotes, without any spaces, copy and paste this exactly: acpi_osi=\"Linux\"
 The line should now look like this: GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
 Save the file and exit the gedit text editor.
 Now, open the Terminal (Applications>Terminal).
 Type: sudo update-grub
 Press Enter (or Return) and wait...
 Wait...
 Has the text stopped moving? If so, you're almost done.
 Exit the terminal.
 Reboot.
 Now the correct kernel/fan behavior has been activated and the fan  will work as it should and your excessive heat Ubuntu laptop problems  are solved. You're cured. Do something else. Carry on. Don't worry. Be  happy. You're welcome. Good luck. Goodbye.

---

### Post by pierreu1 on 2012-08-19
**I followed [this fix]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578")#23:**

**So, did what I was told:**

sudo gedit /etc/default/grub

**(Changed the grub as specified in the fix and then updated the grub.)**

$ sudo update-grub to update /boot/grub/grub.cfg

**But, I got this:**

/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found

**Not sure what I should do!**


**[SIZE="4"]FIX[/SIZE]**

Thanks :-), i read your posts on "Linux Forums" and i will use this for my problems :

1. For CPU Fan and Fn keys :

first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer

Then System/Admin/Services and disable ACPID power management and reboot

---

### Post by pierreu1 on 2012-08-19
BIOS INFO


# dmidecode 2.11
SMBIOS 2.4 present.
38 structures occupying 1295 bytes.
Table at 0x000DF010.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: 6.00   
	Release Date: 07/12/2007
	Address: 0xE4480
	Runtime Size: 113536 bytes
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		ACPI is supported
		USB legacy is supported
		AGP is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: TOSHIBA
	Product Name: Satellite A100
	Version: PSAA8C-SK400E
	Serial Number: 76050474Q                       
	UUID: 0414D160-0A56-11DB-A70E-00A0D146D8CE
	Wake-up Type: Power Switch
	SKU Number: Not Specified
	Family: Not Specified

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: CAPELL VALLEY(NAPA) CRB
	Version: Not Applicable
	Serial Number: Not Applicable

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: No Enclosure
	Type: Other
	Lock: Not Present
	Version: N/A
	Serial Number: None
	Asset Tag: No Asset Tag                    
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00001234

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: U2E1
	Type: Central Processor
	Family: Other
	Manufacturer: Intel
	ID: E8 06 00 00 FF FB E9 AF
	Version: Genuine Intel(R) CPU           T1
	Voltage: 3.3 V
	External Clock: Unknown
	Max Speed: 2048 MHz
	Current Speed: 1860 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 kB
	Maximum Size: 64 kB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Socketed, Level 2
	Operational Mode: Write Back
	Location: External
	Installed Size: 2048 kB
	Maximum Size: 4096 kB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J19
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator: COM 1
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: Circular DIN-8 male
	Port Type: Keyboard Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS/2 Mouse
	External Connector Type: Circular DIN-8 male
	Port Type: Mouse Port

Handle 0x000A, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Slot J8B1
	Type: 32-bit PCI
	Current Usage: Unknown
	Length: Long
	ID: 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000B, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Slot J9B1
	Type: 32-bit PCI
	Current Usage: Unknown
	Length: Long
	ID: 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000C, DMI type 9, 13 bytes
System Slot Information
	Designation: PEG Slot J6C1
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Long
	ID: 6
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000D, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot J7C1
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Long
	ID: 8
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000E, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot J8C1
	Type: 32-bit PCI Express
	Current Usage: Unknown
	Length: Long
	ID: 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x000F, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Disabled
	Description: HD-Audio

Handle 0x0010, DMI type 11, 5 bytes
OEM Strings
	String 1: This is the Intel Calistoga
	String 2: PSAA8C-SK400E,S3A2422D004       

Handle 0x0011, DMI type 12, 5 bytes
System Configuration Options
	Option 1: Jumper settings can be described here.

Handle 0x0012, DMI type 15, 29 bytes
System Event Log
	Area Length: 16 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x00000001
	Header Format: Type 1
	Supported Log Type Descriptors: 3
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: Single-bit ECC memory error
	Data Format 2: Multiple-event
	Descriptor 3: Multi-bit ECC memory error
	Data Format 3: Multiple-event

Handle 0x0013, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 2 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0014, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0013
	Error Information Handle: No Error
	Total Width: 32 bits
	Data Width: 32 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M1
	Bank Locator: Bank 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0015, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0013
	Error Information Handle: No Error
	Total Width: 32 bits
	Data Width: 32 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M2
	Bank Locator: Bank 1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0016, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x0013
	Partition Width: 2

Handle 0x0017, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x0014
	Memory Array Mapped Address Handle: 0x0016
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x0018, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x0015
	Memory Array Mapped Address Handle: 0x0016
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x0019, DMI type 23, 13 bytes
System Reset
	Status: Enabled
	Watchdog Timer: Present
	Boot Option: Do Not Reboot
	Boot Option On Limit: Do Not Reboot
	Reset Count: Unknown
	Reset Limit: Unknown
	Timer Interval: Unknown
	Timeout: Unknown

Handle 0x001A, DMI type 24, 5 bytes
Hardware Security
	Power-On Password Status: Enabled
	Keyboard Password Status: Unknown
	Administrator Password Status: Enabled
	Front Panel Reset Status: Unknown

Handle 0x001B, DMI type 25, 9 bytes
	System Power Controls
	Next Scheduled Power-on: 12-31 23:59:59

Handle 0x001C, DMI type 26, 20 bytes
Voltage Probe
	Description: Voltage Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x001D, DMI type 27, 12 bytes
Cooling Device
	Temperature Probe Handle: 0x001E
	Type: Fan
	Status: OK
	OEM-specific Information: 0x00000000

Handle 0x001E, DMI type 28, 20 bytes
Temperature Probe
	Description: Temperature Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x001F, DMI type 29, 20 bytes
Electrical Current Probe
	Description: Electrical Current Probe
	Location: Processor
	Status: OK
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0020, DMI type 30, 6 bytes
Out-of-band Remote Access
	Manufacturer Name: Intel
	Inbound Connection: Enabled
	Outbound Connection: Disabled

Handle 0x0021, DMI type 32, 20 bytes
System Boot Information
	Status: <OUT OF SPEC>

Handle 0x0022, DMI type 129, 16 bytes
OEM-specific Type
	Header and Data:
		81 10 22 00 01 01 02 01 00 00 00 01 00 00 08 01
	Strings:
		Intel_ASF_001
		Intel_ASF_001

Handle 0x0023, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 23 00 FF FF

Handle 0x0024, DMI type 150, 14 bytes
OEM-specific Type
	Header and Data:
		96 0E 24 00 01 01 00 00 00 00 00 00 00 00
	Strings:
		ABSOLUTE(PHOENIX) CLM

Handle 0x0025, DMI type 127, 4 bytes
End Of Table

---

### Post by overdrank on 2012-08-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

