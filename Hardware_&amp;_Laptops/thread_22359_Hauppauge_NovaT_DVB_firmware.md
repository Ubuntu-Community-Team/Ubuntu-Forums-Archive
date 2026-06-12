---
title: "Hauppauge NovaT DVB firmware"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by robj on 2005-03-27
I have a Nova T with the tda1004x/saa7146 chipset (i.e. not the new conexant chipset ones that require kenel patching etc)

The hardware appears to be recognised by Hoary (see various system messages at the end of this post) but when testing with tzap, dmesg reports:

[COLOR=Navy]tda1004x: waiting for firmware upload...
tda1004x: no firmware upload (timeout or file not found?)
tda1004x: firmware upload failed[/COLOR]

I have copied the library from the 2.15a version of the (technotrend) windows driver:
[COLOR=Navy]$ ls -la /usr/lib/hotplug/firmware/
-rw-rw-rw-  1 robj robj 286720 2003-04-10 10:31 tda1004x.bin
-rw-r--r--  1 root root 286720 2005-03-27 18:43 tda1004x.mc[/COLOR]

 ](*,) 
Anyone have any suggestions?
 :confused: 


dmesg reports:
[COLOR=Navy]saa7146: register extension 'budget_ci dvb'.
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
saa7146: found saa7146 @ mem d0ab4000 (revision 1, irq 19) (0x13c2,0x1011).
DVB: registering new adapter (TT-Budget/WinTV-NOVA-T  PCI).
adapter has MAC addr = 00:d0:5c:23:b1:a3
DVB: registering frontend 0 (Philips TDA10045H DVB-T)...[/COLOR]

lspci:
[COLOR=Navy]0000:00:0b.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)[/COLOR]

lsmod says:
[COLOR=Navy]Module                  Size  Used by
v4l2_common             5888  0
v4l1_compat            13572  0
video                  16260  0
budget_ci              12160  0
tda1004x               11908  1 budget_ci
firmware_class          9728  1 budget_ci
budget_core             9092  1 budget_ci
dvb_core               74408  2 budget_ci,budget_core
saa7146                17700  2 budget_ci,budget_core
ttpci_eeprom            2688  1 budget_core
stv0299                 9348  1 budget_ci
i2c_core               21264  5 budget_ci,tda1004x,budget_core,ttpci_eeprom,stv0299
crc32                   4352  3 dvb_core,sis900,fbcon[/COLOR]

---

### Post by robj on 2005-03-27
Apparently as of kernel 2.6.10 the method for obtaining and naming firmware for tda1004x Nova-T's has changed. 
this script was needed to obtain and extract firmware:

[http://www.ibiblio.org/peanut/Kernel-2.6.10/dvb/get_dvb_firmware](http://www.ibiblio.org/peanut/Kernel-2.6.10/dvb/get_dvb_firmware)

joy, and onto the next problem :)

Rob

---

### Post by mterring on 2005-04-26
This doesn't work for me, it just says:

Apr 27 08:09:09 bangor kernel: tda1004x: waiting for firmware upload...
Apr 27 08:09:12 bangor kernel: tda1004x: firmware upload failed

So I enabled DEBUG in hotplug:

Apr 27 08:09:09 bangor default.hotplug[8552]: arguments (firmware) env (PHYSDEVPATH=/devices/pci0000:00/0000:00:14.0 SUBSYSTEM=firmware OLDPWD=/ DEVPATH=/class/firmware/0000:00:14.0 FIRMWARE=dvb-fe-tda10045.fw PATH=/bin:/sbin:/usr/sbin:/usr/bin ACTION=add PWD=/etc/hotplug UDEV_LOG=1 MANAGED_EVENT=1 SHLVL=1 HOME=/ PHYSDEVDRIVER=budget_ci dvb PHYSDEVBUS=pci SEQNUM=1312 _=/usr/bin/env)
Apr 27 08:09:09 bangor default.hotplug[8552]: invoke /etc/hotplug/firmware.agent ()
Apr 27 08:09:09 bangor default.hotplug[8569]: arguments (firmware) env (PHYSDEVPATH=/devices/pci0000:00/0000:00:14.0 SUBSYSTEM=firmware OLDPWD=/ DEVPATH=/class/firmware/0000:00:14.0 FIRMWARE=dvb-fe-tda10045.fw PATH=/bin:/sbin:/usr/sbin:/usr/bin ACTION=remove PWD=/etc/hotplug UDEV_LOG=1 MANAGED_EVENT=1 SHLVL=1 HOME=/ PHYSDEVDRIVER=budget_ci dvb PHYSDEVBUS=pci SEQNUM=1313 _=/usr/bin/env)
Apr 27 08:09:09 bangor default.hotplug[8569]: invoke /etc/hotplug/firmware.agent ()

In /usr/lib/hotplug/firmware I have:

-rw-r--r--  1 root root  30555 2005-04-26 19:58 dvb-fe-tda10045.fw
-rw-r--r--  1 root root  24479 2005-04-26 20:35 dvb-fe-tda10046.fw
-rw-r--r--  1 root root 286720 2005-04-26 21:04 tda1004x.bin

This is on a VIA M-10000 if that matters.

Any clues?

---

