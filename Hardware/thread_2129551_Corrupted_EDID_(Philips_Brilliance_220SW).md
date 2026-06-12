---
title: "Corrupted EDID (Philips Brilliance 220SW)"
date: 2013-03-26
forum: Hardware
---

### Post by AnoPoli on 2013-03-26
A few days ago my monitor's EDID got corrupted.
Can somebody (with the same (but healthy) monitor) send me his/her monitor's EDID?
My monitor is: [Philips Brilliance 220SW]("http://www.p4c.philips.com/cgi-bin/cpindex.pl?ctn=220SW9FB/27&hlt=Link_Overview&scy=US&slg=AEN")
It's safe and easy to extract your monitor's EDID in a file, and you will also have a backup for yourself (recommended).
Look here for more info: [edid-rw]("https://github.com/bulletmark/edid-rw")
To download the program: [zip]("https://github.com/bulletmark/edid-rw/archive/master.zip")
To extract the EDID:
```
./edid-rw 0 > 220SW.BIN
```
Please post the 220SW.BIN somewhere to download it.
Thanks in advance

---

### Post by BubuXP on 2013-04-30
Found this while searching for technical info on this monitor, I hope I'm not too late.

I used the read-edid util present in debian.

This is the output of **/usr/sbin/get-edid > 220sw.bin**

```
/usr/sbin/get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11100 "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful
```

and the EDID output file [is here](http://www.mediafire.com/download.php?0dmv9qx5vdcfzds).

---

