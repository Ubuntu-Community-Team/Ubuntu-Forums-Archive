---
title: "hang on ``Verifying DMI Pool Data`` at boot"
date: 2012-09-14
forum: Hardware
---

### Post by Drone4four on 2012-09-14
I was running Ubuntu with an uptime for some two weeks or so.  After downloading Black Mesa Source today, I attempted to boot into Windows 7 to install the recently released mod but I got an error message before Grub2 loaded.  The message read, “BOOTMGR is missing.”  I then booted my Ubuntu Live disc and Googled the error message.   I can’t recall exactly what it was that nudged me towards the conclusion that it was my two mass storage USB sticks plugged into my PC.  I have my boot priority in my BIOS set to USB-HDD, CD Drive and then hard disk.  My BIOS was probably looking for an O/S on those two storage USB sticks and it couldn’t find any.  I removed my USB sticks which eliminated that error message. However, I then encountered different unusual behaviour.  Now it hangs after, “Verifying DMI Pool Data.....”   Google tells me that the source of problems similar to mine involve hardware and not software.  Since I don't even get to Grub2 boot loader, it can`t be a problem with Ubuntu or Windows.  As per advice I found on Google, I tried reverting to factory default settings in the BIOS.   This yielded  “Update Success” after ``Verifying DMI Pool Data,`` but it still hangs.  Also, I think my hard disk isn't the problem.  My Ubuntu Live environment detects all the hard drives.  I can see the contents of all my partitions, so I think I can safely rule out that it`s a faulty hard disk.   What else could it be?

---

### Post by Epodx64 on 2012-09-15
Try booting into a live cd and running memtest86 or run "sudo dmidecode --type memory" from a terminal I had an identical problem to that plus when I could boot to a livecd it would say "dmi-table-broken-stop" in the hostname turned out to be bad ram "1Gb of PNY DDR2 Ram"

---

### Post by Drone4four on 2012-09-15
Does the demidecode command supposed to indicate whether I have bad memory?  I also have Memtest86 running right now.

```
ubuntu@ubuntu:~$ sudo dmidecode --type memory
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 8-bit Parity
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		Other
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 4
		0x0006
		0x0007
		0x0008
		0x0009
	Enabled Error Correcting Capabilities:
		None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 1
	Current Speed: Unknown
	Type: Other
	Installed Size: 4096 MB (Single-bank Connection)
	Enabled Size: 4096 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2
	Current Speed: Unknown
	Type: Other
	Installed Size: 4096 MB (Single-bank Connection)
	Enabled Size: 4096 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A2
	Bank Connections: 3
	Current Speed: Unknown
	Type: Other
	Installed Size: 4096 MB (Single-bank Connection)
	Enabled Size: 4096 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A3
	Bank Connections: 4
	Current Speed: Unknown
	Type: Other
	Installed Size: 4096 MB (Single-bank Connection)
	Enabled Size: 4096 MB (Single-bank Connection)
	Error Status: OK

Handle 0x001C, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 32 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x001D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 2304 bits
	Data Width: 2244 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 2304 bits
	Data Width: 2244 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x001F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 2304 bits
	Data Width: 2244 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: A2
	Bank Locator: Bank4/5
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x0020, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: 2304 bits
	Data Width: 2244 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: A3
	Bank Locator: Bank6/7
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

ubuntu@ubuntu:~$ 
```

---

### Post by Drone4four on 2012-09-16
My problem  is that I can't get to my Grub2 bootloader because it hangs at DMI Pool. The work around I figured out is to use a Super Grub2 LiveCD to detect the Grub2 configuration file on my home directory which resides on /dev/sda7.  However I'm still in need of a permanent solution because I don't want to use Super Grub every time I want to boot an O/S.

---

### Post by varunendra on 2012-09-16
From your last post it seems that the BIOS does not actually hang, but is probably waiting for something (which is different of 'hang' state) or has done its job but the subsequent process (loading OS maybe?) is stuck or unresponsive.

What if you boot with the hard disk disconnected? Does it still hang on the same screen or return some "no boot device found" type error?

Some BIOS programs (even on some modern boards) are so stupid that they don't even try to boot from other available media if you have not included it in its boot sequence and in correct order. So make sure that the hard disk is listed in BIOS boot sequence and is on top in its category.

If it is already ok, then maybe there is some problem with MBR (as the error message in your original post indicated). To figure that out and possibly correct it, boot with live cd, install [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), run it and post back the pastebin link it creates (or the contents of "Result" file it created in root's home).

---

### Post by Drone4four on 2012-09-23
Thanks, varunendra.  I ended up using the 'Recommended repair' feature in the Boot Repair app you suggested.  I should have reported back here sooner, but I got carried away with other things. Thanks again. =D

---

### Post by YannBuntu on 2012-09-24
> **Drone4four said:**
> I ended up using the 'Recommended repair' feature in the Boot Repair app you suggested.

Did this fix your problem?
if yes, please use the Thread Tools to mark it [Solved].

---

