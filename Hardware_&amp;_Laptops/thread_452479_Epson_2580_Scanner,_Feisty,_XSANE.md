---
title: "Epson 2580 Scanner, Feisty, XSANE"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by Riverine on 2007-05-23
XSANE support for the 2580 scanner is broken in Feisty.  You can read about the problem on Launchpad here [[COLOR="Red"]https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488") 

The scanbuttond workaround works for my system so I thought I would make note of it here in case other 2580 users had the same problem.

1. Install the scanbuttond package via Synaptic or with apt.

2. Disconnect the 2580's usb interface before you boot your system and reconnect it only after boot is complete.  This will prevent the 2580 from hanging (the red flashing light on the scan button).  If the 2580 is hung up, don't reboot your system, just cycle power to the scanner.

3. Start the scanbuttond process:   open a terminal window, enter *scanbuttond -r 1000000*

4. Start and run XSANE as usual.

You can leave the scanbuttond process running.  It uses a small amount of memory and cpu cycles.  Alternatively, you can stop the process with the command *killall scanbuttond* (just remember to start scanbuttond again before you restart XSANE).

---

### Post by JeneaseGrieco on 2007-06-15
I have followed your instructions. Yet, I still get an error message "Failed to open device ' snapscan:libusb:004:006': Invalid argument" What am I doing wrong!

Help please. most of my homework is submitted online I got to scan a lot of atuff!

Thanks
Jenease

---

### Post by noynac on 2007-06-15
--Posting deleted--

---

### Post by juniorsonny on 2007-06-18
I need help using my hp scanjet 3500c.  It gives me a Error during read: Eror during  device I/O.  Please help!!!

---

### Post by vgrisham on 2007-06-21
> **Riverine said:**
> 
4. Start and run XSANE as usual.


Riverine, how does one do that? I've not yet run XSANE.

---

### Post by vgrisham on 2007-08-02
Bump.

Has anyone had any luck with the Perfection/SnapScan 2580 and related scanners since June?

---

