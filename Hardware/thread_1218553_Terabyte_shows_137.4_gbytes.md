---
title: "Terabyte shows 137.4 gbytes"
date: 2009-07-20
forum: Hardware
---

### Post by rylFlush on 2009-07-20
Only 137 gigs of my seagate terrabyte drive is recognize by Ubuntu 9.04. The BIOS and Windows XP see the whole drive. I have the lastest firmware on the drive. Seatools reveals:
[INDENT] paul@ubuntu:~$ sudo ./st -i /dev/sg1
    /dev/sg1
    Vendor = ATA      
    Product = ST31000340NS     
    Version = SN01
    Serial Number = 
    Copyright = 
    SCSI Firmware = [
    Servo RAM Release =     ST31
    Servo ROM Release = 000340NS
    Servo RAM Date =     
    Servo ROM Date = SN01

    Blocksize = 512, Highblock = 268435454, Capacity = 134218 MB
    -this is a Seagate drive
    -this drive does not support DST
    -Mode Page Settings [current value (default)]:
        -WCE bit = 1 (0)
        -RCD bit = 0 (0)
        -AWRE bit = 1 (0)
        -ARRE bit = 0 (0)
        -DExcpt bit = 0 (0)
        -Number of cache segments = 0 (0)
        -JIT bit 0 = 0 (1)
        -JIT bit 1 = 0 (1)
        -JIT bit 2 = 0 (1)
        -JIT bit 3 = 0 (1)
[/INDENT]Any suggestions?

---

### Post by rylFlush on 2009-07-21
I think this is solved. I'll need to test for awhile. I got this from another post on another forum post.[http://ubuntuforums.org/archive/index.php/t-1009343.html]("http://ubuntuforums.org/archive/index.php/t-1009343.html"). It said the Max number addresses wasn't set for this drive. I downloaded Seatools for Dos and burned a bootable CD with it. To do this I needed to use Windows XP as downloaded ISO was not readable in Ubuntu.

I booted into SeaTools for DOS. I checked the drive and it ***WAS*** set for Max number addresses. But I went into the menu and selected Max Addresses from the Advanced Menu. On reboot into Ubuntu I opened gparted and saw the whole disk drive. 

I believe there may be a problem with how Linux accesses this drive. Above is my old ./st listing. Below is the new:

paul@ubuntu:~$ sudo ./st -i /dev/sg1
	/dev/sg1
	Vendor = ATA      
	Product = ST31000340NS     
	Version = SN01
	Serial Number = 
	Copyright = 
	SCSI Firmware = 
	Servo RAM Release = 0)0C0Z0
	Servo ROM Release = q0&#65533;0&#65533;0&#65533;0
	Servo RAM Date = &#65533;01
	Servo ROM Date = $181

	Blocksize = 512, Highblock = 1953525167, Capacity = 976763 MB
	-this is a Seagate drive
	-this drive does not support DST
	-Mode Page Settings [current value (default)]:
		-WCE bit = 1 (0)
		-RCD bit = 0 (0)
		-AWRE bit = 1 (0)
		-ARRE bit = 0 (0)
		-DExcpt bit = 0 (0)
		-Number of cache segments = 0 (0)
		-JIT bit 0 = 0 (1)
		-JIT bit 1 = 0 (1)
		-JIT bit 2 = 0 (1)
		-JIT bit 3 = 0 (1)

Note the upper ascii characters for the Servo RAM data. Anyways this looks like the solution so marking Solved.

---

### Post by rylFlush on 2009-07-21
Nope this isn't working. I turn off and turn on and the value qets reset to 137 again. Also I think now the partition is corrupt so I may need to back up everything.

All the tests I've run on the disk say everything is fine. XP says it's fine. Gparted shows this partition is "unallocated" which is weird since this is the OS I'm using now and everything is working fine.

---

