---
title: "Oki B4100 printing @PJL stuff via samba"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by sevcsik on 2007-02-26
Hi!

I have an Ubuntu Edgy with an Oki B4100 printer. I'd like to share the printer with XP machines (using own driver).
The problem is that when an XP machine tries to print, the printer prints stuff like:
```
-12345X@PJL
@PJL JOB NAME = "WindowsNT"
@PJL OKIAUXJOBINFO DATA="ComputerName=andris"
[...]
@PJL ENTER LANGUAGE=PCL
b1Mr0Fu600Dt [...]

```

Here's my smb.conf:
```
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	printcap name = cups
	dns proxy = No
	wins support = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	printing = cups
	print command = lpr -P b4100 %s
	lpq command = %p
	lprm command = 
	use client driver = Yes

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[shares coming here...]

```

Any ideas why this is happening? With the same config, it worked on SuSE 10.2.
I have cups-1.2.4-2ubuntu3 and samba-3.0.22-1ubuntu4.1.
In other topics people said that it's solved in Edgy, but I still have this problem.
Thanks for any help.

---

### Post by sevcsik on 2007-02-27
Any ideas?

---

### Post by mintar on 2007-03-12
I have had the same problem (with the same printer) and finally got it working after 6 hours of work.


**The problem**

I am using the driver I found here: [http://ubuntuforums.org/showthread.php?t=256031]("http://ubuntuforums.org/showthread.php?t=256031")

My setup is: OKI B4100 on computer A, running CUPS 1.1.x on Ubuntu 6.04.
Computer B, running Windows XP, connected to the OKI printer on computer A via IPP, using the original OKI Windows driver.
Printing from Linux on computer A works fine, printing from Windows gives the result described by sevcsik. He is using Samba instead of IPP, but that shouldn't matter.


**The solution**

Finally, I stumbled upon this thread:

[http://ubuntuforums.org/showthread.php?t=232996]("http://ubuntuforums.org/showthread.php?t=232996") 

The problem seems to be that the Windows driver encodes the data to PJL, and then the Linux driver does the same again. So we have data wrapped in PJL wrapped in PJL, the printer removes *one* layer of PJL, and what gets printed is data wrapped in PJL, instead of just data. So:


1. Uninstall your printer from both computers.

2. Install the printer on computer A as **RAW** (using KDE, install the printer normally, then when asked for a driver, check "raw (does not need driver)" instead).

3. Call this printer "oki_b4100_raw".

4. On Windows, install the printer driver as you would normally (using IPP or SMB should both work), and use "oki_b4100_raw".

5. To be able to print on Linux, install *another* printer, but this time a network printer over IPP, using the following URI:

[http://localhost:631/printers/oki_b4100_raw](http://localhost:631/printers/oki_b4100_raw)

6. Call this printer "oki_b4100" and use it for your Linux printing needs.

Voila, it's done!

I hope this solves your problem, sevcsik. If not, I'll be happy to help!

mintar



BTW: Does anybody know if this is connected to [bug 55828]("https://launchpad.net/ubuntu/+source/cupsys/+bug/55828")?

---

### Post by sevcsik on 2007-03-13
Thanks a lot! That solved my problem. I'd never think about this myself :)

---

### Post by Pof34 on 2007-04-02
THANK YOU !!!
This works for me...

---

### Post by mintar on 2007-04-02
Glad to hear! :-)

---

