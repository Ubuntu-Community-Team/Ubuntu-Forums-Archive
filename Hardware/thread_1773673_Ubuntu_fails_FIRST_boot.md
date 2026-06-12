---
title: "Ubuntu fails FIRST boot"
date: 2011-06-02
forum: Hardware
---

### Post by Diskdoc on 2011-06-02
I have an Acer Aspire TimelineX 3820TG laptop with Intel + Radeon switchable graphics. If "switchable" is enabled in BIOS, Natty will halt at boot the FIRST time. After a warm reboot, the system boots normally (making use of Intel graphics).

Symptoms:

- Black screen, no activity.
- After changing console windows (ctrl+alt+arrows) I can see a bunch of (kernel?) errors on one of the consoles.

Workaround:

- Switch to "discrete" in BIOS to force use of Radeon graphics instead. 

I´m not sure I'm content with the solution..the Intel graphics support is supposed to be more battery efficient. At present however, this may not be the case since the (Intel) brightness control is also broken in Natty.

Anyone else with the same problem?

---

### Post by Yellow Pasque on 2011-06-02
What version BIOS do you have?
```
sudo dmidecode -t bios
```

---

### Post by Diskdoc on 2011-06-02
Here it is:

> # dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: V1.19
	Release Date: 10/27/2010
	Address: 0xE3F10
	Runtime Size: 114928 bytes
	ROM Size: 4096 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		ACPI is supported
		USB legacy is supported
		AGP is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

---

### Post by Yellow Pasque on 2011-06-02
Your BIOS is up to date, so I guess we need to find a way for you to post the error messages.

---

### Post by Diskdoc on 2011-06-02
I had a look at the error messages. The problem occurs pretty early in the boot process, the timer was on 14.4something. It's before or just as the "ubuntu" text is supposed to be displayed on the framebuffer.

The errors contain stuff about "modprobe" and "radeon" and something that starts with green.. I had a look at what there was in dmesg.x and syslog.x but it seems nothing is written there when the boot fails.

I could perhaps take a photo of the errors and post if you like?

---

### Post by Diskdoc on 2011-06-05
Hmm. Seems this bug only occurs sometimes! I tried rebooting warm and could a couple of times but couldn't reproduce. Will post a picture when I see this next time but am fine using Radeon right now.

---

### Post by Diskdoc on 2011-06-07
"I'm not crazy!" :)

Attaching photo of problem.

---

### Post by rccp on 2011-06-07
hello everyone, i did have the same problem with ubuntu 10.10 64 bits have you tried to do a sudo apt-get full-upgrade? maybe those drivers wasn't in the installation, try this in recovery mode and tell us if it worked good luck.

---

### Post by Yellow Pasque on 2011-06-08
[http://askubuntu.com/questions/39562/radeon-module-boot-problems?amp](http://askubuntu.com/questions/39562/radeon-module-boot-problems?amp)

---

