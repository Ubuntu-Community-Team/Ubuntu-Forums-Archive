---
title: "After suspend-resume cycle: USB mouse very &quot;jumpy&quot;"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by A.Skwar on 2006-06-25
Hi!

I'm using the [FONT="Fixedsys"]**2.6.15-25-686**[/FONT] kernel on Dapper (naturally...). I installed the hibernate package and modified [FONT="Courier New"]**/etc/hibernate/hibernate.conf**[/FONT] to include:

```
UseSysfsPowerState disk
PowerdownMethod shutdown
Verbosity 0
LogFile /var/log/hibernate.log
LogVerbosity 1
Distribution debian
SaveClock restore-only
UnloadBlacklistedModules yes
LoadModules auto
SwitchToTextMode yes
```

In [FONT="Lucida Sans Unicode"]**/boot/grub/menu.lst**[/FONT], I added "[FONT="System"]**resume=/dev/hda6**[/FONT]" to the kernel line.

After having done this, I ran "[FONT="Courier New"]**hibernate -v 3**[/font]" and the system hibernated just fine. At next boot, I didn't get a normal boot, but a resume - all very well.

But now my USB mouse (a Dell branded Logitech mouse) is very "*jumpy*". Don't know how to explain this, but best I can say is, that it reacts very slowly and seems to get only every third information or something like this.

What can I do about this?

```
alexander@knospe:~$ lsusb
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000
```

```
alexander@knospe:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
```

Thanks,

Alexander

---

