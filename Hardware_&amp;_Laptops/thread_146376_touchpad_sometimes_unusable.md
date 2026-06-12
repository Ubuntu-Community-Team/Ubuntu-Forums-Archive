---
title: "touchpad sometimes unusable"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by melquiades on 2006-03-18
guys,
      I have a compal fl31 laptop running on ubuntu 5.10. On most occasions, usually 4 out of 5, my touchpad works perfectly upon bootup. And when it doesn't there's no moving the cursor except with the aid of a mouse. I've saved the /proc/interrupts file at times when the touchpad works and won't work. 

/proc/interrupts when Touchpad is usable:
           CPU0       
  0:    5371284    IO-APIC-edge  timer
  1:       9512    IO-APIC-edge  i8042
  8:          1    IO-APIC-edge  rtc
  9:      17081   IO-APIC-level  acpi
 12:     107839    IO-APIC-edge  i8042
 14:      63537    IO-APIC-edge  ide0
 16:          0   IO-APIC-level  uhci_hcd:usb4, yenta, i915@pci:0000:00:02.0
 17:         23   IO-APIC-level  Intel ICH6
 18:          0   IO-APIC-level  uhci_hcd:usb3
 19:          0   IO-APIC-level  uhci_hcd:usb2
 20:    2005056   IO-APIC-level  ohci1394, Intel ICH Modem
 23:         12   IO-APIC-level  uhci_hcd:usb1, ehci_hcd:usb5
NMI:         0 
LOC:    4071318 
ERR:          0
MIS:          0

/proc/interrupts when touchable is unusable
           CPU0       
  0:     909199    IO-APIC-edge  timer
  1:       2647    IO-APIC-edge  i8042
  8:          1    IO-APIC-edge  rtc
  9:       1127   IO-APIC-level  acpi
 14:      16970    IO-APIC-edge  ide0
 16:          0   IO-APIC-level  uhci_hcd:usb4, yenta
 17:         23   IO-APIC-level  Intel ICH6
 18:          0   IO-APIC-level  uhci_hcd:usb3
 19:          0   IO-APIC-level  uhci_hcd:usb2
 20:          2   IO-APIC-level  ohci1394, Intel ICH Modem
 23:         12   IO-APIC-level  uhci_hcd:usb1, ehci_hcd:usb5
NMI:          0 
LOC:     360397 
ERR:          0
MIS:          0

I'm not quite sure what this file tells but for a newbie like me, one thing I noticed between the two is that i8042 has 2 irq numbers (1 & 12) when the touchpad is working, as compared to only one irq ( 1 ) when it's not. I recognized i8042 as a one of the drivers used by winxp for the touchpad (i8042prt.sys). So a newbie like me would suppose that there's some connection to the touchpad's usability under ubuntu and that missing irq for i8410; but as to what connection I have no idea.

Here's an extract of my /etc/X11/xorg.conf file by the way, just in case it's needed

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Can anyone please help me figure this out? Thanks for reading my post.

cheers,
melquiades

---

