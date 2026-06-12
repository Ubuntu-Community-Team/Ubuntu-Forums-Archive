---
title: "USB Port Assignments Are Not Consistent From Boot to Boot"
date: 2020-04-14
forum: Hardware
---

### Post by mark bower on 2020-04-14
My question is, is there a way via BIOS or something I am not aware of which will always cause USB ports to be captured/assigned in the same order when a PC is booted?                                                                                                                                                                                                                                                                                                                                                                                                                                                               

I am using two HP34401A multimeters which have RS-232 output and each is connected to a PC USB port.  In the connection process, the RS-232 signals are converted and delivered to the USB ports via cabling with built in converters (RS-232 to USB).  There is a problem in that for each boot of the computer, it is a toss-up as to whether the FTDI converter will be assigned to ttyUSB0 or ttyUSB1 and vise versa for the pl2303 device.  

The inputs from the meters are plotted and displayed on a monitor like an oscilloscope screen.  The switching of assignment from one boot to another obviously wreaks havoc with the meaning of the display.

Case 1 boot:
```
mark@mark:~$ dmesg | grep tty
[    0.214063] printk: console [tty0] enabled
[    1.656751] 00:04: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[   21.149448] usb 1-5.4: FTDI USB Serial Device converter now attached to ttyUSB0
[   21.181525] usb 1-5.2: pl2303 converter now attached to ttyUSB1

```
Case 2 Boot (FTDI and pl2303 have switched assignments):
```
mark@mark:~$ dmesg | grep tty
[    0.212725] printk: console [tty0] enabled
[    1.659891] 00:04: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[   15.811967] usb 1-5.2: pl2303 converter now attached to ttyUSB0
[   15.846315] usb 1-5.4: FTDI USB Serial Device converter now attached to ttyUSB1
```

The following code is how the devices are captured in the program:
```
scom1 = "/dev/ttyUSB0:9600,e,7,2,rs,cd0,cs0,ds0"
scom2 = "/dev/ttyUSB1:9600,e,7,2,rs,cd0,cs0,ds0"

open com scom1 for input as #1
open com scom2 for input as #2
```

---

### Post by odd135 on 2020-04-15
Would it be possible to latch the meters each to a different value when starting up, test for that value, and assign inputs accordingly? I'm no expert with Ubuntu serial port drivers, but that's probably what I'd do if I hit a similar input problem with my arduino.

---

### Post by TheFu on 2020-04-15
Perhaps some udev rules can control it?

Do serial devices have a "by-path" or "by-id" like video and disks do?  Those shouldn't change at boot.  Sorta like /dev/sd[a-z] have /dev/disks/by-path/.... works.

But I haven't any clue.

---

### Post by mark bower on 2020-04-15
Admittedly, this is a bit over my head.  

@ TheFu  Actually, the meters do have HP-IB addresses, but from the sources I have (and looked online) I cannot determine a way to determine what they are remotely, that is, from withing the program (I can get to them from the front panel). The point here is that their HP-IB addresses does differentiate the meters, I just don't have the knowledge how to access that information via the software and equipment involved.

@odd135  I see it all the time "udev" rules, but do not know how to work with them.  But your post triggered some further thinking.  I do get the input strings you see in my first post, and it would be possible to "pluck out" both the ttyusb# assignment and the connecting cable device ID (ie FTDI or pl2303) and see if they match the tty address as needed, else do some sort of swap.  I will investigate that, but probably as a downstream effort since I currently have a work around.

I really was hoping for something very simple.  So thanks both for your responses

---

### Post by sisco311 on 2020-04-15
> **TheFu said:**
> Perhaps some udev rules can control it?

Do serial devices have a "by-path" or "by-id" like video and disks do?  Those shouldn't change at boot.  Sorta like /dev/sd[a-z] have /dev/disks/by-path/.... works.

But I haven't any clue.

Can't test it but according to the udev rule on my system (/lib/udev/rules.d/60-serial.rules), they should be /dev/serial/by-path/ and /dev/serial/by-id/

---

### Post by TheFu on 2020-04-15
Probably worth starting by checking the usb device ids to see they are unique. Then udev can force a specific device name for each.
i have a USB-to-Serial cable around here somewhere but haven't seen it in a few years.  Don't have 2, so really cannot test it.

---

### Post by sisco311 on 2020-04-15
> **TheFu said:**
> Probably worth starting by checking the usb device ids to see they are unique. Then udev can force a specific device name for each.
i have a USB-to-Serial cable around here somewhere but haven't seen it in a few years.  Don't have 2, so really cannot test it.

I was trying to say that there is an existing udev rule which does all the magic and creates the necessary symlinks in /dev/serial .

So the OP only needs to change the path to the devices in the config file(s) from /dev/tttyUSB* to /dev/serial/by-id/*whatever*

---

### Post by mark bower on 2020-04-16
I generally get the udev concept, but again a bit over my head as have never done it or worked with symlinks.  And on further reflection, making such changes would require doing the same on another PC should I use it, and,  each upgrade(I do fresh installs), would have to make the udev changes again.

So, I believe my best option is to work the problem with programs coding using string functions, something like(very generally to give the idea):

1) Capture the 4 strings involving "tty" (this is done by shelling in the program to dmesg)

2) Test for the presence of FTDI in the 3rd string, ie, Does the string "[   21.149448] usb 1-5.4: FTDI USB Serial Device converter now attached to ttyUSB0" have FTDI in it?
    
3) If yes, then
         pair the FTDI device to scom1
4) Else
         pair the FTDI device to scom2

And I now realize  that I can do this only because I have devices from two different manufacturers, which provides differentiation.  Bottom line, all the support inputs to this thread have elucidated a mostly approach that will work for me.

---

