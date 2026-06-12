---
title: "Intel 2100 wireless problem"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by jesibl on 2005-03-09
I've done all the installations required, but my wireless card is still not being detected.  i think this might be because my ethernet card interface is using eth1, which is what the wireless card is supposed to use (and i think the drivers tell it to use this interface).  is there a way of changing the interface the wireless card uses?  or maybe finding out which one it is trying to use?  or am i asking the wrong questions completely?

---

### Post by Johan on 2005-03-09
I have an Intel 2100 card too and for me it just works. Have you loaded the ipw2100 module? It should be made automatically but you can make sure by typing sudo modprobe ipw2100. Does it say anything in dmesg about the card? What does ifconfig say? And iwconfig?

---

### Post by jerome bettis on 2005-03-09
it's probably mapped to eth0 ... did you check that out?

---

### Post by alastair on 2005-03-09
Check the logs :

dmesg

or

/var/log/syslog

Look for mention of "ipw".

Or : lsmod | grep ipw

Check network devices (all of them) :

ifconfig -a

---

### Post by jesibl on 2005-03-09
firstly how do i check whether it's mapped to eth0?

secondly, after i type ifconfig -a, i get info about my ethernet card (eth1) and two other devices "lo" and "sit0".  no idea what they mean but they don't mention anything about being wireless.

if i look in the syslog, i find:

Mar 10 10:24:48 localhost kernel: ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 0.53
Mar 10 10:24:48 localhost kernel: ipw2100: Copyright(c) 2003-2004 Intel Corporation
Mar 10 10:24:48 localhost kernel: ACPI: PCI interrupt 0000:01:03.0[A] -> GSI 7 (level, low) -> IRQ 7
Mar 10 10:24:48 localhost kernel: ipw2100: Error allocating IRQ 7.
Mar 10 10:24:48 localhost kernel: ipw2100: probe of 0000:01:03.0 failed with error -16

which, by looking at it seems to show that something didn't work along the way.

typing iwconfig says:

lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

so....help?  :)

---

### Post by alastair on 2005-03-09
No, the driver isn't getting loaded properly.

This looks like an IRQ (interrupt request) problem, so ..... I would try something like the following.

After each - see if the module loads and "ifconfig -a" shows a device.

1) Boot with kernel arg. :

pci=noacpi

2) If that doesn't help, boot with :

pci=routeirq

3) If that doesn't help, boot with :

acpi=off

To boot with a kernel arg. - stop at grub (ESC), "e" to edit the kernel line (stick extra arg at end) and "b" to boot.

---

### Post by jesibl on 2005-03-09
ok, when i typed in "pci=noacpi", the boot hung when it was checking for PCMCIA services.

when i typed "pci=routeirq", it said "unknown option" during boot and nothing changed when i typed in ifconfig -a

when i typed in "acpi=off", my sound card suddenly worked and my battery power indicator stopped working, but ifconfig -a still showed the same thing as before.

what i did notice was, during boot up, there was the error:

address space collision on region 7 of bridge 0000:00:1f.0 [800:87f] whatever that means

and later on during the hotplug stuff:

modprobe:FATAL:Error inserting hw_random (blah blah): Input/Output

I don't know if these mean anything.

I'm using kernel 2.6.8.1-5-386 if that helps at all.

update: I tried sudo modprobe ipw2100 again and this time when i type in ifconfig -a, i get an additional interface:

eth0      Link encap:Ethernet  HWaddr 00:04:23:4D:FF:EE
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x3000 Memory:fcfff000-fcffffff

Is this right?

---

### Post by alastair on 2005-03-10
Well - an "additional" interface is good.

See if it's wireless via :

iwconfig eth0

There is something odd going on with your system though. Might be worth taking a look in the BIOS and seeing what the IRQ options are (if there are any). Perhaps (BIOS) disable any things you do not use (e.g. IrDA etc.).

---

### Post by danielk on 2005-03-13
[QUOTE=jesibl]firstly how do i check whether it's mapped to eth0?

secondly, after i type ifconfig -a, i get info about my ethernet card (eth1) and two other devices "lo" and "sit0".  no idea what they mean but they don't mention anything about being wireless.

if i look in the syslog, i find:

Mar 10 10:24:48 localhost kernel: ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 0.53
Mar 10 10:24:48 localhost kernel: ipw2100: Copyright(c) 2003-2004 Intel Corporation
Mar 10 10:24:48 localhost kernel: ACPI: PCI interrupt 0000:01:03.0[A] -> GSI 7 (level, low) -> IRQ 7
Mar 10 10:24:48 localhost kernel: ipw2100: Error allocating IRQ 7.
Mar 10 10:24:48 localhost kernel: ipw2100: probe of 0000:01:03.0 failed with error -16

which, by looking at it seems to show that something didn't work along the way.

typing iwconfig says:

lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

so....help?  :)[/QUOTE]

I have a Dell Inspiron 600m and I'm running into the exact same problem (I use a Intel 2200bg not 2100).

When I type:  dmesg, I too get the following message:
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.11
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Error allocating IRQ 7
ipw2200: probe of 0000:02:03.0 failed with error -16


Any thoughts?

**EDIT**
I'm not sure if this is any help (I'm new to Linux) but when i type: lspci -vv
I get the following stuff pertaining to IRQ 7:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB (ICH4) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Computer Corporation: Unknown device 011e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 7
        Region 0: I/O ports at b800
        Region 1: I/O ports at bc40 [size=64]
        Region 2: Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>


0000:00:1f.6 Modem: Intel Corp. 82801DB (ICH4) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Conexant: Unknown device 5422
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 7
        Region 0: I/O ports at b400
        Region 1: I/O ports at b080 [size=128]
        Capabilities:

 <available only to root>


0000:02:03.0 Network controller: Intel Corp. Intel(R) PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corp.: Unknown device 2721
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 7
        Region 0: Memory at fafef000 (32-bit, non-prefetchable)
        Capabilities: <available only to root>


As I said, I'm not sure if this help but I found it interesting because my sound doesn't work either.

---

### Post by pete on 2005-03-14
I spent the better part of this past weekend fighting with this exact problem on a Latitutde D500 with an Intel 2100--  finally found the explanation in [this Bugzilla entry](https://bugzilla.ubuntu.com/show_bug.cgi?id=1254) .

According to the entry, it's fixed in later versions of the kernel, so I gave the Hoary beta a shot, and wireless is now working like a champ.

---

### Post by danielk on 2005-03-14
[QUOTE=pete]I spent the better part of this past weekend fighting with this exact problem on a Latitutde D500 with an Intel 2100--  finally found the explanation in [this Bugzilla entry](https://bugzilla.ubuntu.com/show_bug.cgi?id=1254) .

According to the entry, it's fixed in later versions of the kernel, so I gave the Hoary beta a shot, and wireless is now working like a champ.[/QUOTE]


Thanks a lot. I'll try it when I get home later.

---

### Post by danielk on 2005-03-17
[QUOTE=danielk]Thanks a lot. I'll try it when I get home later.[/QUOTE]

Didn't work. I'm running Hoary preview and I still seem to be having the same problem.

---

