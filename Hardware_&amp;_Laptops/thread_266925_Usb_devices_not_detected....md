---
title: "Usb devices not detected..."
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by zoradude5 on 2006-09-27
Hey, I am new to linux, but think it is great! I have looked around for some solution, but get stuck at dmesg. I copy the output into mousepad (I am using Xubuntu) and search for usb, but find no reference whether a usb device is plugged in or not. I do have usb ports in the back of the computer, and the light of device is lit, but I meet no success. What do I do now?

---

### Post by jISh on 2006-09-27
First of all, all you need to do to see what USB devices are plugged in is to type:
```
lsusb
```
in the terminal.
If you can't find it there, then check your dmesg like this:
```
dmesg |grep usb
```

Next, what exactly are you trying to make work?

---

### Post by zoradude5 on 2006-09-28
I get nothing from the lsusb,
and get this message for the dmesg lgrep usb:
dmesg [-c] [-n level] [-s bufsize]

I am trying to get a flash drive to work

---

### Post by zoradude5 on 2006-09-28
bump

---

### Post by zoradude5 on 2006-09-30
bump

---

### Post by zoradude5 on 2006-10-01
bump? I would like to know what is up with my usb port and why it is not being detected...

---

### Post by devils_casper on 2006-10-01
Hi !

plug-in usb device and execute this command in terminal.

tail -s 3 -f /var/log/messages

This command will poll the kernel's message log every three seconds, and displays the latest messages the kernel has spat out. check the assigned device name.



casper

---

### Post by christhemonkey on 2006-10-01
That should be a | not an l (on my keyboard it second function on the backslash)

```
dmesg | grep usb 
```
Note the space between the | and the grep




Also, i dont think it refers to usb in the dmesg, on my computer, it mostly refers to scsi and sda, so try:
```
dmesg | tail 
```
a few seconds after you have inserted your usbstick and look for references to "scsi emulation" or "sda".

Post its output here.

---

### Post by zoradude5 on 2006-10-01
This is what I got with the device plugged in:

carlos@ubuntu:~$ dmesg | grep usb
carlos@ubuntu:~$ dmesg | tail
[   73.086052] CSLIP: code copyright 1989 Regents of the University of California
[   73.121010] PPP generic driver version 2.4.2
[   73.347781] NET: Registered protocol family 10
[   73.348473] lo: Disabled Privacy Extensions
[   73.348914] IPv6 over IPv4 tunneling driver
[   96.068820] ppdev: user-space parallel port driver
[   98.767162] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  102.839805] hdc: drive_cmd: status=0x11 { SeekComplete Error }
[  102.839848] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  102.839866] ide: failed opcode was: 0xec
carlos@ubuntu:~$ tail -s 3 -f /var/log/messages
Oct  1 15:30:41 localhost kernel: [   96.068820] ppdev: user-space parallel port driver
Oct  1 15:30:44 localhost kernel: [   98.767162] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct  1 15:30:48 localhost kernel: [  102.839805] hdc: drive_cmd: status=0x11 { SeekComplete Error }
Oct  1 15:30:48 localhost kernel: [  102.839848] hdc: drive_cmd: error=0x04 { AbortedCommand }
Oct  1 15:30:48 localhost kernel: [  102.839866] ide: failed opcode was: 0xec
Oct  1 15:31:14 localhost chat[3267]: ATDT361W6932000^M^M
Oct  1 15:31:14 localhost chat[3267]: NO CARRIER
Oct  1 15:31:14 localhost chat[3267]:  -- failed
Oct  1 15:31:14 localhost chat[3267]: Failed (NO CARRIER)
Oct  1 15:31:16 localhost pppd[3230]: Exit.

---

### Post by zoradude5 on 2006-10-02
bump

---

### Post by zoradude5 on 2006-10-03
After my bump last night, I read another post that recommended looking in the bios to see if the USB controller was enabled.
In the Chipset setup menu, I found that it was disabled. Shortly After enabling it, I booted up, and found that my USB Device Was functioning. Thanks all!

---

