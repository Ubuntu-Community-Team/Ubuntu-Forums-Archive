---
title: "Microtek v300 parallel port scanner - how to install?"
date: 2009-02-26
forum: Hardware
---

### Post by leoh on 2009-02-26
Hi everyone.
I need to install a parallel port Microtek V300 scanner on an Ubuntu 8.10.
I have already checked and the parallel port is enabled on the BIOS.

The XSane does not detect it, and under console, if I run "xsane-find-scanner" I get, among other lines, this:

"#Not checking for parallel por scanners"

Here ([http://www.sane-project.org/sane-backends.html#S-MICROTEK](http://www.sane-project.org/sane-backends.html#S-MICROTEK)) it says that the V300 has "good" support under parallel port.

So, what should I do so it actually does scan for it?
What would be the procedure?

---

### Post by geraldm on 2009-02-26
Look at the manpage for it. 
man sane-microtek2

I would also try a link to the parallel port, and name the link /dev/scanner0

The manpage does not cover this, so it might not be necessary:
I would also change the group permission of the scanner's parallel port to
group "scanner" with permissions of 0660.
Add the scanner user to the group scanner.
If the port was lp0, try
sudo ln -s /dev/lp0 /dev/scanner0
sudo chmod 0660 /dev/lp0

regards,
Gerald

---

### Post by davidsrsb on 2009-02-27
Does the PC work with the scanner under Windows? Parallel port scanners are very sensitive to PC speed and the port circuit. The parallel port is not very good at bidirectional data transfer.

---

### Post by leoh on 2009-03-02
> **geraldm said:**
> Look at the manpage for it. 
man sane-microtek2

I would also try a link to the parallel port, and name the link /dev/scanner0
How do I do this?

> **geraldm said:**
> I would also change the group permission of the scanner's parallel port to
group "scanner" with permissions of 0660.
How do I do that?

> **geraldm said:**
> Add the scanner user to the group scanner.
And that?

> **geraldm said:**
> If the port was lp0, try
sudo ln -s /dev/lp0 /dev/scanner0
sudo chmod 0660 /dev/lp0
I did that, but nothing happened.

---

### Post by leoh on 2009-03-02
> **davidsrsb said:**
> Does the PC work with the scanner under Windows? Parallel port scanners are very sensitive to PC speed and the port circuit. The parallel port is not very good at bidirectional data transfer.

The scanner is not officially supported under Windows XP because it is an old model (1999?). However, with the Windows 2000 driver it is recognized and the speed test comes out OK. I could not scan an image, but that's a driver (TWAIN?) issue, not a hardware issue.

I was expecting that, I have other old Microtek scanners at work and none of them work under Windows XP.

---

### Post by leoh on 2009-03-05
Anyone? Please?

---

### Post by leoh on 2009-03-17
Bump.
Please...?

---

