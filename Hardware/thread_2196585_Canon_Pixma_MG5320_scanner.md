---
title: "Canon Pixma MG5320 scanner"
date: 2013-12-30
forum: Hardware
---

### Post by jamesb1957 on 2013-12-30
I have been trying to install my scanner in xubuntu 12.04 and have gone through a number of solutions found in ubuntu forms with no luck. I am very new to ubuntu so go easy on me with your replies please.

Below is the terminal screen shot of what I have tried so far.


```

james@hp-desktop:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer 
Bus 001 Device 004: ID 045e:0766 Microsoft Corp.  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical 
Bus 001 Device 005: ID 04a9:1754 Canon, Inc.  
james@hp-desktop:~$ sane-find-scanner 
 
  # sane-find-scanner will now attempt to detect your scanner. If the 
  # result is different from what you expected, first make sure your 
  # scanner is powered up and properly connected to your computer. 
 
  # No SCSI scanners found. If you expected something different, make sure that 
  # you have loaded a kernel SCSI driver for your SCSI adapter. 
 
found USB scanner (vendor=0x04a9, product=0x1754) at libusb:001:005 
  # Your USB scanner was (probably) detected. It may or may not be supported by 
  # SANE. Try scanimage -L and read the backend's manpage. 
 
  # Not checking for parallel port scanners. 
 
  # Most Scanners connected to the parallel port or other proprietary ports 
  # can't be detected by this program. 
 
  # You may want to run this program as root to find all devices. Once you 
  # found the scanner devices, be sure to adjust access permissions as 
  # necessary. 
james@hp-desktop:~$ scanimage -L 
 
No scanners were identified. If you were expecting something different, 
check that the scanner is plugged in, turned on and detected by the 
sane-find-scanner tool (if appropriate). Please read the documentation 
which came with this software (README, FAQ, manpages). 
james@hp-desktop:~$  
```

I am currently using xsane as my scanner program and the version  is .998
This is what shows when check for latest version of sane
james@hp-desktop:~$ scanimage -V
scanimage (sane-backends) 1.0.22; backend version 1.0.22
When I checked to see if my printer is supported under the sane project, it is 

[TABLE]
[TR]
[TD="align: center"]PIXMA MG5300 Series[/TD]
[TD="align: center"]USB[/TD]
[TD="align: center"]0x04a9/0x1754[/TD]
[TD="align: center"][COLOR=#007000]Complete[/COLOR][/TD]
[TD]All resolutions supported (up to 2400DPI).[/TD]
[TD="align: center"] [pixma]("http://home.arcor.de/wittawat/pixma/") 
(0.17.4)[/TD]
[TD="align: center"][sane-pixma]("http://www.sane-project.org/man/sane-pixma.5.html")[/TD]
[/TR]
[/TABLE]


When I try to enable the backend by using the 
james@hp-desktop:~$ sudo gedit /etc/sane.d/dll.conf
[sudo] password for james: 

 this is what I get
sudo: gedit: command not found

This is the site that I am using as a reference to install my scanner because it is not auto-detected

[https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected)
But as you see above when I run the find scanner command my scanner shows up,although it does not show that it is a canon scanner, only the vendor #

Not sure if this info will help but my computer is a HP desktop with a 2.8 Ghz Pentium 4 processor.
Also the printer is hooked up directly with a USB cable and not running wireless.

Thanks Jim

---

### Post by adam-saunders on 2014-01-04
Hi JIm, is the "sane-pixma" package installed?  If not, try installing it and try to scan again. If so, could you set up the printer wirelessly and try again?

---

### Post by deadflowr on 2014-01-04
> [COLOR=#000000]When I try to enable the backend by using the [/COLOR]
[COLOR=#000000]james@hp-desktop:~$ sudo gedit /etc/sane.d/dll.conf[/COLOR]
[COLOR=#000000][sudo] password for james: [/COLOR]

[COLOR=#000000]this is what I get[/COLOR]
[COLOR=#000000]sudo: gedit: command not found[/COLOR]

I don't think xubuntu has gedit.
Find out the name of the text editor you have and change gedit to that.
I think it's either mousepad or leafpad.

---

### Post by jamesb1957 on 2014-01-04
deadflwr:

your right xubuntu does not have gedit but does have leafpad so that problem is solved.

adam-saunders:

did some more searching on the net and found "http://ubuntuhandbook.org/index.php/2013/07/canon-drivers-for-ubuntu-and-linux-mint/" followed the instructions and now have my scanner up and running.

Thank You both for taking the time to reply.

Jim C.:)

---

### Post by deadflowr on 2014-01-04
It's an unfortunate state that a good chunk of advice, which is universal among the buntus has Ubuntu specific commands, which then cause users who are running other systems, like Xubuntu or Kubuntu, fits because those programs mentioned aren't in the system used.
Well, at least now you know to change it/ignore mentions of gedit and replace it with your own.
I, myself try to point out that any graphically program I suggest is for Ubuntu and a user of another system, like Xubuntu, should change the Ubuntu program, like gedit, to whatever they have.
I'm not always successful at pointing that out, though.:confused:

Good to see the setup is working.

---

### Post by jamesb1957 on 2014-01-05
If I would have gone in a check to see if gedit was installed or checked what the default editor was for xubuntu I probably would have saved myself a least a few headaches.

---

