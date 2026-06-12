---
title: "Modem problem- But it said it's linux compatible!"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by kate on 2005-08-06
I think this is my first post here... Anyway...
I'm a linux newbie and since about Feb I've been complaining about not being about to use the internet with linux ( having a winmodem). For my b'day about a week ago, I got a linux-compatible modem. Its a PCI 56k modem, and it is in and everything. I got the disk and it has the linux driver on it. However, it is for kernel 2.4.something. I followed the installation instructions, but it comes up with a message saying that some file isnt found. Can anyone point me in the right direction?

~Kate

---

### Post by Juergen on 2005-08-06
> I think this is my first post here... Anyway...I see posts: 3 ;-)

> Its a PCI 56k modem, and it is in and everything.Your best bet would have been an external modem (are there serial lines in modern computers? But probably USB-modems communicate the same way)

The exact name/model would help. 
Maybe you can find somthing here: [http://www.linmodems.org](http://www.linmodems.org)

---

### Post by kate on 2005-08-06
its a Dick Smith one... umm Intel 536ep if that helps anything....

I must have forgotten about the other posts....

---

### Post by az on 2005-08-06
Try the smartlink drivers.  They are known to work with the intel 536 chipset.  If not, install the build-essential and linux-headers package and go to the intel site and find the 2.6 kernel driver for the 536 modem.



[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=6497&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=6497&strOSs=39&OSFullName=Linux*&lang=eng)

[http://downloadfinder.intel.com/scripts-df-external/T8Clearance.aspx?url=/7300/eng/intel536-4.68-fc1-up.tgz&agr=Y&ProductID=977&DwnldID=7300&lang=eng](http://downloadfinder.intel.com/scripts-df-external/T8Clearance.aspx?url=/7300/eng/intel536-4.68-fc1-up.tgz&agr=Y&ProductID=977&DwnldID=7300&lang=eng)

---

### Post by blastus on 2005-08-06
OK I'm a Linux newbie also. But I've read a lot about modems under Linux. I'm sorry I don't have answers to get your modem working but this is what I've read about modems under Linux...

Basically from what I've read is that ALL PCI modems and ALL external USB modems are "soft modems" and you will have great difficulty getting them to work under Linux if it is even possible. ONLY "hard modems" are really supported under Linux. ALL ISA modems and ALL external serial (RS-232) modems are hard modems and should work with Linux. I have an old ISA Rockwell modem that works fine under Fedora Core (on an old machine that has ISA slots) but none of the PCI modems I have work under Fedora Core.

A soft modem is a FAKE modem that does not have the basic circuitry and ROM software to maintain a network connection. Soft modems use the CPU to perform this kind of stuff and so they need specialized drivers and they can drain your CPU performance especially on older machines (< 400 Mhz.) The problem is is that these drivers are usually very proprietary and you'll basically only find drivers for Windows. 

A hard modem is a REAL modem that contains the necessary circuitry to maintain network connections. Hard modems are identified by their price--they are usually much more expensive than soft modems because they have the necessary hardware to work without specialized software drivers.

ISA MODEMS: Unfortunately modern computers do not have an ISA slots so you can't use an ISA modem on these. ALL these modems are hard modems because the idea of striping the basic hardware out of the modem (to reduce manufacturing costs) and making it a soft modem didn't become popular until PCI slots were introduced and CPU speeds increased to be able to handle the load soft modems put on CPUs. By that time ISA was being phased out and replaced with PCI.

PCI MODEMS: ALL these modems are "soft modems" and manufacturers don't care to share the specs with anyone so there's little to no support for these under Linux. The PCI bus enables the modem to communicate with the computer fast enough so that the modem can be controlled by software (not hardware.) Some people have said that a "Linux compatible" message on a PCI modem box is an oxymoron -- because they're ALL WinModems. A WinModem is another name for a "soft modem."

EXTERNAL USB MODEMS: ALL these modems are "soft modems" because the USB interface allows the computer to communicate with the computer fast enough that the modem can be controlled by software (not hardware.) You would connect this modem to a USB port on your computer.

EXTERNAL SERIAL MODEMS: ALL these modems are "hard modems" and should work with any Linux distribution. These modems communicate through the RS-232 serial port (a COM port.) They don't/shouldn't require any drivers because all Linux has to do is communicate with the serial port using standard ATA (modem) commands. ALL serial modems are hardware modems because the RS-232 port is not fast enough for the modem to be completely controlled by software (and not hardware.) Therefore you don't need specialized drivers for them.

From what I've read is that the U.S. Robotics 56K external serial (RS-232) modem is your best bet for dialup under Linux. They're expensive but you can use them on any machine and in theory you shouldn't have to mess with drivers and stuff under Linux. This is the modem I want to eventually get.

---

### Post by kate on 2005-08-06
Thanks, Azz, i'll try those.

Blastus, thanks for the info. I've  been trying to get this one and the one we had before to work for the better part of the year. Needless to say, I was wasting my time. 

I have a serial modem,  but is it definatly a 'hard' modem? It's made by AOpen. I dont have any more info on that coz i must have lost the packaging... Anyway, if I can't get my internal one to work in the next couple of weeks, i'll buy a new one... If I can find it.

---

### Post by blastus on 2005-08-06
[QUOTE=kate]I have a serial modem,  but is it definatly a 'hard' modem? It's made by AOpen. I dont have any more info on that coz i must have lost the packaging... Anyway, if I can't get my internal one to work in the next couple of weeks, i'll buy a new one... If I can find it.[/QUOTE]

Is it an external modem and do you connect it to the RS-232 port on the back of your computer? An RS-232 port is a COM port and it has 9 pins on it. If not then there are no guarantees and I'd say it is a soft modem (assuming it's not an ISA modem.) If it's PCI then it's a soft modem. A PCI modem may use the word "serial" but it is not referring to a real RS-232 port on the back of your computer. Serial just means "one byte after the other." Parallel means "multiple bytes at a time" like an LPT printer port. The COM "port" that a PCI modem is associated with is a virtual port. For example, my PCI Lucent WinModem is connected to COM port 3 but this isn't a real RS-232 port. I think it is just a frame of reference.

---

### Post by kate on 2005-08-06
Yeah it has a RS-232 port. I didn't buy it. We've had it lying around for about 4 years or so. I also have a Lucent Winmodem. But the AOpen one, i dont know anything about except that it's external and has an RS 232 port.

---

### Post by az on 2005-08-06
No.  You are wrong.  Not all pci modems are softmodems.  There are many PCI hardware modems. 

And most software modems are supported by linux.  They mostly have binary-only drivers, but they can work.

Intel, Smartlink, Lucent, Pctel, all have linux drivers.  I think that represents the greater part of the current software modem market.  

wiki.ubuntu.com/forum/hardware

Use scanmodem to identify the modem chipset:
[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)

---

### Post by blastus on 2005-08-07
> And most software modems are supported by linux.

Yes IF AND ONLY IF you are an expert in Linux. You know how to compile kernels, you know the intricate details of the OS inside and out, you understand and can diagnose cryptic error messages and output, etc... etc... etc... in fact, I'd say you should be a Linux developer to really understand these things. It seems like the common definition of a Linux NOVICE is anyone who is NOT an expert in Linux. That pretty much eliminates 99% of the population from getting Linux stuff that DOESN'T WORK OUT-OF-THE-BOX to actually work.

I know if I had a high speed connection I could get Internet access in Ubuntu because I had no problem getting Internet access to work in Fedora Core 1 on high speed on another computer. It was nice because it worked right out of the box. But I'm stuck with dialup here so Linux is pretty much useless to me at this point--no Internet access means I can do squat.

I used scanModem and now what? I've tried several different instruction pages, bah NOBODY explains anything that puts the whole picture together. Well use apt-get to install the kernel headers, do this and do that, download this then download that and follow the instruction in each...dant work. The scattered instructions in the form of email snippets on [http://linmodems.technion.ac.il/packages/ltmodem](http://linmodems.technion.ac.il/packages/ltmodem)...well all I can say is BLAH! Dozens of driver files, which one do you need, apt-get kernel-kbuild-3.6 DOESN'T WORK, the Ubuntu 5.04 instruction-email-snippet thing well the ltmodem-2.6-7-alt-7.tar.bz2 DOESN'T EVEN EXIST on the web server and so and so on and so on. This is just hopeless, it's like trying to find a certain needle in a haystack except that you don't even know what the needle is supposed to look like and there are also thousands of bogus needles in the haystack.

There's just too much of a chasm between those who KNOW Linux and those who don't. I'm an Apache/Java developer and have a B.Sc. in Computer Science and I'm damn good at what I do but I'm no expert in Linux. I took some Linux courses and I know some commands and stuff and while I have some basic knowledge of hardware, I mean really, who expects ANYBODY to understand the output from scanModem?  :roll:  I know what a freakin header is and what source code is because I used to program in C/C++ but should I be expected to be able to diagnose some cryptic error message from recompiling a kernel or something like that? I wouldn't even know where to start.

With Linux and Windows you are pretty much at the mercy of the OS designers/creators and hardware manufacturers. This will never change. I like Linux and stuff but I think it's still at least 15 years away from making inroads on the desktop. I'm talking about the average user here, one who is NOT an EXPERT in EVERYTHING related to hardware configuration in Linux. If you're a Linux expert then great, if not then you might as well forget about switching to Linux and just play around with it for a couple of years, then maybe, you might know enough to configure it and get stuff to work that doesn't work out-of-the-box. For now, as far as basic hardware support (like modems, sound cards etc...), EASE OF INSTALLATION AND USE, multimedia, and the desktop, Windows is light years ahead of Linux. 

I don't mind having to spend time trying to configure stuff here and there, following detailed instructions on how to setup this or that in LInux. The problem is is that everyone assumes I know how to compile kernels, read, understand and diagnose cryptic driver messages, etc... etc... etc... Until the Linux experts realize that they have these assumptions they will never be able to explain things in a clear and concise manner such that someone who is not an expert can understand what they need to do, how they need to do it, and most importantly WHY they need to do this or that step.

---

### Post by mingus on 2005-08-12
kate -

Don't know if this might help . . .

First of all, while generally modems are lumped into the two categories of "hardware" vs "soft" (or "winmodem"), that can occasionally be misleading.  

A true hardware modem has 2 devices, a controller and a datapump.  The form factor can be external, a PCI card, or a pcmcia card.  Typical cost avg $75US.

A true software modem just has circuitry to communicate with the CPU; it's drive with the CPU actually do all the work.  And again, the form factor can be any of the above.  PCI versions avg cost $10.

So, it is inaccurate to assume that a given form factor determines the modem type, it is what is on the board that matters.

A twist on this are the hybrids.  There aren't many of these, but they can be worth finding.  For example, the Amigo AME-CA95 is an external, RS-232 "controllerless" modem, which usually means that the controller function is off-loaded to the CPU via a driver (like the winmodems) but that the datapump is on-board.  However, this particular modem has an eprom on-board with controller firmware.  It therefore does not need a driver under Linux, and many think that because of this plus it being external and RS-232 that it is a "full hardware" modem - it is not *but* it *does* eliminate the need for a driver and hence is very easy to use.  This modem costs about $25US, which while more than the avg winmodem, is still far less than  a full hardware modem.

---

### Post by az on 2005-08-12
[QUOTE=blastus]Yes IF AND ONLY IF you are an expert in Linux. You know how to compile kernels, you know the intricate details of the OS inside and out, you understand and can diagnose cryptic error messages and output, etc... etc... etc... in fact, I'd say you should be a Linux developer to really understand these things. It seems like the common definition of a Linux NOVICE is anyone who is NOT an expert in Linux. That pretty much eliminates 99% of the population from getting Linux stuff that DOESN'T WORK OUT-OF-THE-BOX to actually work.

I know if I had a high speed connection I could get Internet access in Ubuntu because I had no problem getting Internet access to work in Fedora Core 1 on high speed on another computer. It was nice because it worked right out of the box. But I'm stuck with dialup here so Linux is pretty much useless to me at this point--no Internet access means I can do squat.

I used scanModem and now what? I've tried several different instruction pages, bah NOBODY explains anything that puts the whole picture together. Well use apt-get to install the kernel headers, do this and do that, download this then download that and follow the instruction in each...dant work. The scattered instructions in the form of email snippets on [http://linmodems.technion.ac.il/packages/ltmodem](http://linmodems.technion.ac.il/packages/ltmodem)...well all I can say is BLAH! Dozens of driver files, which one do you need, apt-get kernel-kbuild-3.6 DOESN'T WORK, the Ubuntu 5.04 instruction-email-snippet thing well the ltmodem-2.6-7-alt-7.tar.bz2 DOESN'T EVEN EXIST on the web server and so and so on and so on. This is just hopeless, it's like trying to find a certain needle in a haystack except that you don't even know what the needle is supposed to look like and there are also thousands of bogus needles in the haystack.

There's just too much of a chasm between those who KNOW Linux and those who don't. I'm an Apache/Java developer and have a B.Sc. in Computer Science and I'm damn good at what I do but I'm no expert in Linux. I took some Linux courses and I know some commands and stuff and while I have some basic knowledge of hardware, I mean really, who expects ANYBODY to understand the output from scanModem?  :roll:  I know what a freakin header is and what source code is because I used to program in C/C++ but should I be expected to be able to diagnose some cryptic error message from recompiling a kernel or something like that? I wouldn't even know where to start.

With Linux and Windows you are pretty much at the mercy of the OS designers/creators and hardware manufacturers. This will never change. I like Linux and stuff but I think it's still at least 15 years away from making inroads on the desktop. I'm talking about the average user here, one who is NOT an EXPERT in EVERYTHING related to hardware configuration in Linux. If you're a Linux expert then great, if not then you might as well forget about switching to Linux and just play around with it for a couple of years, then maybe, you might know enough to configure it and get stuff to work that doesn't work out-of-the-box. For now, as far as basic hardware support (like modems, sound cards etc...), EASE OF INSTALLATION AND USE, multimedia, and the desktop, Windows is light years ahead of Linux. 

I don't mind having to spend time trying to configure stuff here and there, following detailed instructions on how to setup this or that in LInux. The problem is is that everyone assumes I know how to compile kernels, read, understand and diagnose cryptic driver messages, etc... etc... etc... Until the Linux experts realize that they have these assumptions they will never be able to explain things in a clear and concise manner such that someone who is not an expert can understand what they need to do, how they need to do it, and most importantly WHY they need to do this or that step.[/QUOTE]

File a bug report and ask that there be a software modem configuration tool developed for ubuntu.  Some other distributions have hit-and-miss modem driver support.  Warty did not have any precompiled modem support.  Hoary shippes with the lucent drivers in the kernel. 

Ask for the sl-modem drivers to be shipped with Breezy and that should cover about two-thirds of software modems.

Go on the wiki and update the modem page.  Tell them that no dial up modem users stick with linux because of what you just posted.  Keep it to about fifty words and make it compelling and maybe something will happen.

There are not enough people asking for this and so that is why it is not being done.

---

### Post by az on 2005-08-13
[http://ubuntuforums.org/showthread.php?t=56578](http://ubuntuforums.org/showthread.php?t=56578)

*clap* *clap* *clap*

Somehow, every time I have asked, it was on a firday, or on the eve of the big Ubuntu conference...

---

### Post by blastus on 2005-08-13
[QUOTE=azz]File a bug report and ask that there be a software modem configuration tool developed for ubuntu.  Some other distributions have hit-and-miss modem driver support.  Warty did not have any precompiled modem support.  Hoary shippes with the lucent drivers in the kernel. 

Ask for the sl-modem drivers to be shipped with Breezy and that should cover about two-thirds of software modems.

Go on the wiki and update the modem page.  Tell them that no dial up modem users stick with linux because of what you just posted.  Keep it to about fifty words and make it compelling and maybe something will happen.

There are not enough people asking for this and so that is why it is not being done.[/QUOTE]

I will look into that. About two days after I posted that I got the modem to work and it's still working as of today. See here [http://www.ubuntuforums.org/showthread.php?p=300445](http://www.ubuntuforums.org/showthread.php?p=300445). ;-)

---

### Post by az on 2005-08-13
[QUOTE=blastus]I will look into that. About two days after I posted that I got the modem to work and it's still working as of today. See here [http://www.ubuntuforums.org/showthread.php?p=300445](http://www.ubuntuforums.org/showthread.php?p=300445). ;-)[/QUOTE]


I thought this was you:

[http://ubuntuforums.org/showthread.php?t=56578](http://ubuntuforums.org/showthread.php?t=56578)


Oh well!  Go figure!

---

