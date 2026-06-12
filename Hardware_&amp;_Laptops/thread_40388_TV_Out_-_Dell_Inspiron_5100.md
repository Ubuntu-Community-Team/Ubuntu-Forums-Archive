---
title: "TV Out - Dell Inspiron 5100"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by vinayn on 2005-06-08
Hello:

I know this topic has been asked before, but it's never been explained in a "howto" manner. I've tried all suggestions, but none gave any results.

I run Ubuntu Hoary H 5.04 on a Dell Inspiron 5100, which has a ATI Radeon Mobility 7500. I've been trying to get the TV out to work via the S Video port. I installed atitvout, rebooted with the S Video connected and on running atitvout, I get this:
"VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!"

Also in my xorg.conf in the device section it shows this:
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection
I know I have a Radeon Mobility 7500. The Device manager shows the display card as  Radeon Mobility M7 LW (Radeon Mobility 7500).

Please can anybody tell me a step by step method on how to get this working.
Thanks in advance.

V

---

### Post by Mudbream on 2006-01-25
Hi,
I have the same problem - well I just want to figure out how to turn on the s-video on my Dell Inspiron 5100.
I use KDE if that makes any difference?

Anyone?
Thanks,
Mudbream

---

