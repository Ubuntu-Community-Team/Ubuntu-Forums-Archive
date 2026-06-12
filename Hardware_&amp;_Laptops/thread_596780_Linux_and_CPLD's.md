---
title: "Linux and CPLD's"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by darthsabbath on 2007-10-29
Hi, I'm taking a class in Digital Logic and Design, and we're working with a Xilinx XCR3064 CPLD.  We use Xilinx ISE Webpack 9.2 for schematic capture, and Digilent's Adept suite to program the chip via a USB to JTAG cable.  I know that ISE is available for Linux, but I've been having trouble finding an application that I can use to program my device. 

I'm a longtime Linux user, but since school started, I've had to use Vista thanks to some of the choices my school has made.  I just installed Gutsy though and it's like night and day, so I'm having a hard time going back to Vista. :D Granted, call me a traitor, but Office 2007 and Visual Studio 2005 make it a little bit easier to bear. ;-) 

Any help you can provide regarding the JTAG programming software would be great though!

Thanks!

---

### Post by quigz on 2007-12-01
Well i kinda got ise webpack to work. i could wirte the verilog just fine but it wouldnt load the ise program to assign package pins. so i had to switch to windows to assign package pins and load it to the board. i have been trying to find the adept suite software for linux. its made by the same people (xilinx) that made the webpack so i assume they have the suite for linux too. were you able to assign package pins with ise in linux? if so let me know. i couldnt get it to work.

---

### Post by xzased on 2007-12-06
hiya guys. any words on this -question sign, my shift button doesnt work- 

im planning on buying a xilinx cpld, but i dont know if ubuntu has the software to run it. any help is appreciated.

--nevermind. i just went to xilinx.com

---

### Post by flaggh on 2008-02-18
Don't know if you solved this issue, but I use Xilinx ISE 9.2i Webpack on my Ubuntu machine and it works great for compiling and loading the code onto FPGAs through a USB JTAG cable.  Why have you been unable to program using ISE?  Is it the software or the usb cable that is giving you trouble?

---

### Post by hvymtlsteve on 2008-02-19
What USB cable are you using that actually works?
Is it the Xilinx Platform cable? Because that thing is a whopping 200 bucks!

Digilent's Parallel-JTAG is much cheaper, 13 bucks, and it works on Linux pretty easily.. there are some instructions out there for running on Ubuntu, too:
[http://groups.google.com/group/comp.arch.fpga/msg/2dfa36541174a4f2](http://groups.google.com/group/comp.arch.fpga/msg/2dfa36541174a4f2)

I tried Digilent's $40 USB-JTAG, which is supposed to work under xilprg (on sourceforge) but I had no luck with that.

I did have a bit of an issue, that some circumstances led to me getting rid of my desktop computer, leaving me without a parallel port. 
I sucked it up and paid 60 bucks or so plus shipping for an expresscard parallel port on ebay, and I'm back in business programming my FPGA boards and CPLDs!

---

### Post by hvymtlsteve on 2008-02-19
> **quigz said:**
> Well i kinda got ise webpack to work. i could wirte the verilog just fine but it wouldnt load the ise program to assign package pins. so i had to switch to windows to assign package pins and load it to the board. i have been trying to find the adept suite software for linux. its made by the same people (xilinx) that made the webpack so i assume they have the suite for linux too. were you able to assign package pins with ise in linux? if so let me know. i couldnt get it to work.

Yup, the assign package pins GUI does not seem to work, for some reason. 
The way to assign package pins is to text edit the user constraints file and make a netlist by hand, unfortunately. 
I would make a generic one for whatever chips you use, that you can recycle for different designs.

---

### Post by flaggh on 2008-02-19
I never used the PACE program before to assign package pins so I'm not really familiar with how it works or the functionality and therefore never realized it wasn't working.  Creating a UCF file is simple enough that I don't see any reason to learn how to use the GUI or boot into XP to generate one.  I use ISE only for editing and compiling verilog, simulating modules, and then loading them onto the FPGA.  It took a little work to get everything going, especially the USB JTAG, but google is a good resource for getting all that stuff working.  If you have any trouble figuring out how to do any of that, I can see if I can dig up the sites myself and post the links.

---

### Post by cszikszoy on 2008-03-05
I would _extremely_ appreciate it if you could link me to some of the resources you used to get Digilent's USB cable to work.  I tried to load their software in virtualbox, but for some reason, it keeps having an error on initialize chain.  I found this a bit strange because Virtualbox has played very nicely with all of my other usb perifs, but I don't have any idea why the Digilent usb cable isn't working.

---

### Post by flaggh on 2008-03-05
I do not use Digilent's USB cable, I use the Xilinx cable which does not work out of the box in Ubuntu.  Following the instructions here
[http://svenand.blogdrive.com/archive/55.html]("http://svenand.blogdrive.com/archive/55.html")
I was able to get everything working fine.  It loads an alternate firmware into the FPGA, everytime it is plugged in.  This firmware does not require a proprietary kernel module that the cable normally requires.

---

