---
title: "3G Pcmcia  Card Not Recognized"
date: 2011-07-02
forum: Hardware
---

### Post by Dumpy Dumpster on 2011-07-02
The laptop is a Dell L400/P3/700MHz/256MB with Lubuntu 10.04 as the OS and works well with both ethernet and pcmcia wireless card for internet.
I am trying to get a 3g connection with a Novatel Merlin U530 pcmcia card. From research, I gather that the driver for these cards is already is already in the kernel, but it seems to me that the machine cannot 'see' the card although recognizes that one is present.
I attach the outputs from 'dmesg' and 'syslog'  

[HTML]...............
[   22.349935] type=1505 audit(1309530687.060:10):  operation="profile_replace" pid=541 name="/usr/lib/connman/scripts/dhclient-script"
[   22.451797] type=1505 audit(1309530687.160:11):  operation="profile_load" pid=585 name="/usr/sbin/ntpd"
[   23.630626] eth0:  setting full-duplex.
[   23.688482] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   23.688507] CS4281 0000:00:08.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   24.455578] gameport: CS4281 Gameport is pci0000:00:08.0/gameport0, speed 2386kHz
[   34.292088] eth0: no IPv6 routers present
[   64.832103] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0

michael@michael-laptop:~$ dmesg | grep "modem"

michael@michael-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.659559] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.660971] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[/HTML]

and  

[HTML]michael@michael-laptop:~$ tail -f /var/log/syslog
Jul  1 16:31:32 michael-laptop ntpd[988]: frequency initialized 22.094 PPM from /var/lib/ntp/ntp.drift
Jul  1 16:31:33 michael-laptop init: plymouth-stop pre-start process (1021) terminated with status 1
Jul  1 16:31:35 michael-laptop polkitd[1067]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jul  1 16:31:36 michael-laptop anacron[1112]: Anacron 2.3 started on 2011-07-01
Jul  1 16:31:36 michael-laptop anacron[1112]: Normal exit (0 jobs run)
Jul  1 16:31:39 michael-laptop kernel: [   34.292088] eth0: no IPv6 routers present
Jul  1 16:32:09 michael-laptop kernel: [   64.832103] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
Jul  1 16:35:50 michael-laptop ntpd[988]: synchronized to 91.189.94.4, stratum 2
Jul  1 16:35:50 michael-laptop ntpd[988]: time reset -0.190511 s
Jul  1 16:35:50 michael-laptop ntpd[988]: kernel time sync status change 2001

[/HTML]

Thanks for any help.

---

### Post by Dumpy Dumpster on 2011-07-05
I have stumbled about a bit more and found how to check if the HSO module is installed in the kernel - it seems to be:

[HTML]michael@michael-laptop:~$ find /lib/modules/`uname -r` -name 'hso.ko'
/lib/modules/2.6.32-32-generic/kernel/drivers/net/usb/hso.ko
/lib/modules/2.6.32-32-generic/updates/dkms/hso.ko
[/HTML]

I have also wondered if the card requires a CD to operate.  So I downloaded 'ozerocdoff' from [peck.org/ozerocdoff.html]("peck.org/ozerocdoff.html")

I think I have installed it correctly, blindly following the instructions but still there seems to be 'no life' in the pcmcia card.

Any ideas?

---

### Post by Dumpy Dumpster on 2011-07-18
I have borrowed a second U530 card and the results are the same - so I do not think it is a faulty card.

Both cards however also crash the computer after an interval.  By that I mean they seem to force a total shutdown - dead stop.  But on reboot with the wireless PCMCIA card back in, Network Manager re-establishes a standard wireless connection with an Orange Livebox.

Still need some help to establish a 3G connection!

---

