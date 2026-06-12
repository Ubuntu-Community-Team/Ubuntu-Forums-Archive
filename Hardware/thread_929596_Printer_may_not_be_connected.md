---
title: "Printer may not be connected"
date: 2008-09-25
forum: Hardware
---

### Post by Sashin on 2008-09-25
Okay, I have a Canon MP210 series printer. I've installed all the correct drivers and everything.

I had the printer working before fine, but the scanner wasn't so in an attempt to have it working I unplugged the printer and replugged it. 
Now my scanner is working but my printer isn't, ever since I unplugged the printer and replugged it, whenever I plug it in it says that the printer is ready for use but whenever I actually print something it says "MP210 series may not be connected".

What can I do?

---

### Post by Sashin on 2008-09-25
Anyone able to help?

Oh and from [http://localhost:631/printers/](http://localhost:631/printers/)

it says

```
"Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4a9_1721_F37BA3_if1_printer_noserial": Permission denied"
```

Just in case that helps.

---

### Post by Sashin on 2008-09-25
Bump

I've also received this error message:

"CUPS server error

There was an error during the CUPS operation: 'server-error-service-unavailable"

---

### Post by phidia on 2008-09-25
I think it's worth opening the print manager from System > Admin >Printing  delete that printer and re-install it. See if that gets it going for you.

---

### Post by Sashin on 2008-09-25
Oh, I've already tried that. It doesn't work.

---

### Post by phidia on 2008-09-25
What does > lpstat -p && lsusb entered in the terminal output?

---

### Post by Sashin on 2008-09-25
lpstat: No destinations added.

---

### Post by Sashin on 2008-09-26
Still looking for help...

---

### Post by phidia on 2008-09-26
And "lsusb"?

---

### Post by Sashin on 2008-09-26
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0572:cb01 Conexant Systems (Rockwell), Inc. GeekADSL Promax Q31 ADSL Modem
Bus 001 Device 004: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by Sef on 2008-09-26
> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0572:cb01 Conexant Systems (Rockwell), Inc. GeekADSL Promax Q31 ADSL Modem
Bus 001 Device 004: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

It don't seem to be detected.  Have you tried plugging it into another usb port to make sure that the problem does not lie with the current usb port?

---

### Post by Sashin on 2008-09-26
I'm sorry but when I posted both of those my printer wasn't on...

Now it's on I'll post them again. I still have that error though.

lpstat -p && lsusb:
```
printer MP210_series now printing MP210_series-281.  enabled since Sat 27 Sep 2008 10:32:50 EST
Bus 002 Device 015: ID 04a9:1721 Canon, Inc. 
Bus 002 Device 010: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0572:cb01 Conexant Systems (Rockwell), Inc. GeekADSL Promax Q31 ADSL Modem
Bus 001 Device 004: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

lsusb
```
Bus 002 Device 015: ID 04a9:1721 Canon, Inc. 
Bus 002 Device 010: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0572:cb01 Conexant Systems (Rockwell), Inc. GeekADSL Promax Q31 ADSL Modem
Bus 001 Device 004: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

That's how it is now that my printer is on, I hope someone can help...

---

### Post by Sashin on 2008-09-27
Bump

---

### Post by Sashin on 2008-09-27
Bump

---

### Post by Sashin on 2008-09-28
Bump

---

### Post by Frantic_Earthling on 2008-09-28
I am afraid that I bring no solution to your problem, but I have exactly the same with a Brother wireless printer :(. 

I have access to this printer from three different computers, running Ubuntu 8.04, OpenSUSE 11.0 and Fedora 9. I get the "printer may not be connected error" on a random basis from any of these OS. My printer is perfecty well installed and I have never been able to find a solution to this:confused:.

The way I get out of this error is to boot from Windows:(, from which I always have access to the printer, and then I reboot in Ubuntu. The "printer may not be connected" error never happens then:(:confused:

---

### Post by Sashin on 2008-09-28
Hmm. I dual boot with Windows as well. Maybe that has something to do with it...

---

### Post by Sashin on 2008-09-28
Yet another bump. There's bound to be more people familiar with the phrase:

"Not Connected? Printer MP210_series may not be connected"

---

### Post by Sashin on 2008-09-30
Bump

---

### Post by dodtsair on 2008-10-04
I have the same problem with my Brother 1440:

mpower@dodtsair:~$ lpstat -p && lsusb
printer HL-1440_series now printing HL-1440_series-8.  enabled since Sat 04 Oct 2008 12:26:31 PM PDT
	No %%BoundingBox: comment in header!
printer PDF is idle.  enabled since Sat 04 Oct 2008 12:21:51 PM PDT
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer
Bus 002 Device 005: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
mpower@dodtsair:~$ echo "file" > printme
mpower@dodtsair:~$ lp printme
mpower@dodtsair:~$ sleep 300
mpower@dodtsair:~$ lpstat
HL-1440_series-8        mpower          153600   Sat 04 Oct 2008 12:26:31 PM PDT
HL-1440_series-9        mpower            1024   Sat 04 Oct 2008 12:43:13 PM PDT

Printer is connected, has been reinstalled, computer has been rebooted.  /etc/hosts file has been fixed "127.0.1.1" changed to "127.0.0.1".

Bug, but due to another bug I can not register to launchpad so I can not file it.

---

### Post by dodtsair on 2008-10-05
I was able to print with this printer trying two things.  I am not sure if all were needed.

echo hello >> /dev/usb/lp0

After sending some job to the printer, unplug the power, unplug the usb, plugin the power, plugin the usb.

It is printing for now.

---

### Post by stormtrooprdave on 2009-01-20
> **Sashin said:**
> Anyone able to help?

Oh and from [http://localhost:631/printers/](http://localhost:631/printers/)

it says

```
"Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4a9_1721_F37BA3_if1_printer_noserial": Permission denied"
```

Just in case that helps.

All of a sudden I find myself unable to print. I am getting a message saying Printer 'Stylus-SX2002' may not be connected.

When I look on the cups page on [http://localhost:631/printers/](http://localhost:631/printers/) it says the following:

Stylus-SX2002 "Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4b8_849_4B4C4E4B3032393760_if1_printer_ noserial": Permission denied"

---

### Post by rMatey on 2009-01-26
I don't know about your setup, but I dual-boot.  I also upgraded the kernel.  Using 2.6.27-11-generic.  My Brother HL-2040 is used in both systems.
  Just today when I went to print, it kept giving me a bunch of errors.  All I got was " /use/lib/ filter/ foomatic-rip failed"  The trouble shooter gave a bunch of print-out that I never really saw before.  But it also didn't fix anything.
  Got mine running by disconnecting power and usb to printer; removing printer from System> Administration> Printing.  Reboot.  Plugged in printer and reinstalled driver.

  I just hope it keeps on working.  :-k

---

### Post by jsa13 on 2009-04-19
I have this same issue w/ both my USB attached HP DJ3930 and networked HP CLJ CP1518ni. If I wait both eventually print (when I remember to add paper).  I did a firmware upgrade on the CP1815 and the error happens less.

I am only guessing, bit I think it is a timing issue between spooling the job and a response back from CUPS.  The error is cosmetic (but annoying) in my case.

From [http://www.nylug.org/pipermail/nylug-talk/2008-January/036541.html](http://www.nylug.org/pipermail/nylug-talk/2008-January/036541.html) ...
Maybe disable the AppArmor CUPS profile by running "sudo aa-complain cupsd". AppArmor support may be re-enabled by running "sudo aa-enforce cupsd".

Apparently this is a known cups bug addressed in Jaunty Jackalope (9.04)...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348316)

---

### Post by odin1965 on 2009-09-13
I, too get this message on Jaunty with HP Colorjet 2550, but if I wait it will print. Occurs mainly with large photos. I think it is a timing issue too.

---

### Post by zeper2012 on 2009-09-13
I'll add my two cents. I have this problem as well. My HP P1100 used to work on Ubuntu 9.04 but somewhere along the line something changed and now will not print. I also get the 'printer may not be connected' but I get this:
lpstat -p && lsusb
printer PHOTOSMART-P1100 now printing PHOTOSMART-P1100-0.  enabled since Sun 13 Sep 2009 07:45:36 PM CDT
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:3102 Hewlett-Packard PhotoSmart P1100 Printer w/ Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It seems to think it's printing, but it isn't.

---

### Post by zeper2012 on 2009-09-13
Just to add a little more info - using [http://localhost:631](http://localhost:631) - I get the following:
**Description:** HEWLETT-PACKARD PHOTOSMART P1100
**Location:** john-desktop-quad
**Printer Driver:** HP Photosmart p1100 hpijs, 3.9.2
**Printer State:** processing, accepting jobs,  published. 
**Device URI:** hp:/usb/PhotoSmart_P1100?serial=MX98P1D0VCID  

and I printed a job with the following results after 20 minutes:

   [CENTER][URL="http://localhost:631/jobs/?ORDER=asc"]
[/URL][/CENTER]
   


[SIZE=2]ID [/SIZE] [SIZE=2]Name [/SIZE] [SIZE=2]User [/SIZE] [SIZE=2]Size [/SIZE] [SIZE=2]Pages [/SIZE] [SIZE=2]State [/SIZE] Control      [SIZE=2][PHOTOSMART-P1100]("http://localhost:631/printers/PHOTOSMART-P1100")-10 [/SIZE] [SIZE=2]Yahoo! [/SIZE] [SIZE=2]john [/SIZE] [SIZE=2]2237k [/SIZE] [SIZE=2]Unknown [/SIZE] [SIZE=2] processing since
Sun 13 Sep 2009 07:45:36 PM CDT [/SIZE]

---

### Post by zeper2012 on 2009-09-17
I began to wonder if all the messing around with samba was the problem. I uninstalled all the samba apps and rebooted.
  I then deleted the printer and rebooted. I then reinstalled the printer.
  It works again! I'm happy!  Was it samba - I'm not sure?
:)

---

### Post by tpederse on 2009-10-09
I seem to be having the same problem with an HP LaserJet 2420 - gives message printer may not be connected but automatically recognizes it and shows the following...

ted@ted-desktop:~$ lpstat
hp-LaserJet-2420-254    ted             153600   Fri 09 Oct 2009 09:23:06 AM CDT

ted@ted-desktop:~$ lsusb
Bus 001 Device 006: ID 03f0:2917 Hewlett-Packard LaserJet 2420
Bus 001 Device 002: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Have deleted and reinstalled (several times :) and still no luck. Any thoughts?

---

### Post by davidgutu on 2010-11-18
> **Sashin said:**
> Bump

what do you mean by bump? (noobie qn)

---

