---
title: "Ubuntu shuts down randomly"
date: 2012-02-24
forum: Hardware
---

### Post by Mercury1964 on 2012-02-24
I am relatively new to Ubuntu, and this is my first time trying to install Wubi. The laptop I am using had Wubi on it, running 9.04. This time, however, Ubuntu will boot from GRUB, remain working for a few minutes, and then shutdown, displaying the: 

ubuntu
......

screen, as if I had initiated a shutdown. The only two things I can think of are that the graphics card drivers were buggy and that it likes to overheat. It is a HP Pavilion zd8000 with a Pentium 4 and 2GB of RAM. It also runs Unity fine, at least for the few minutes where it works.
](*,)!!!

---

### Post by ahallubuntu on 2012-02-24
Try cleaning out the CPU heat sink and fan area to get rid of the dust and dirt.  I have cleaned a number of them on old laptops, and it can make a world of difference in heat.  You may have to do it every so often.

The difficulty of cleaning it varies by make and model of laptop.  Some are really easy; some require you to take off the keyboard, etc. and that can be a pain.

Some people recommend even removing the CPU heat sink, cleaning it off, and applying new thermal paste, but I've had better luck simply removing the fan(s) and cleaning without removing the heat sink at all, when possible.  You'll need a little jeweler's screwdriver most likely to remove the screws on the fan(s).

I googled yours: apparently it's notorious for heat issues.  Here's a link to the service manual that will help you figure out how to get to the fan to clean it:

[http://h10032.www1.hp.com/ctg/Manual/c01383095.pdf](http://h10032.www1.hp.com/ctg/Manual/c01383095.pdf)

---

### Post by roelforg on 2012-02-24
Give us the output of:
```

sudo tail -n 40 /var/log/dmesg

```

---

### Post by ahallubuntu on 2012-02-24
Even if you are using Windows, it's still a wise idea to clean out the fan/heat sink on an old P4 laptop.   Those are desktop CPUs that should never have been used in laptops - they get HOT!

---

### Post by kulimanga on 2012-07-21
> **roelforg said:**
> Give us the output of:
```

sudo tail -n 40 /var/log/dmesg

```

hi, I have the same problem. my output of that command shows me this:

hipotent@hipotent-desktop:~$ sudo tail -n 40 /var/log/dmesg
[   19.540757] Adding 915664k swap on /dev/sda7.  Priority:-1 extents:1 across:915664k 
[   19.625640] udev: starting version 151
[   19.717560] lp: driver loaded but no devices found
[   20.167165] parport_pc 00:0c: reported by Plug and Play ACPI
[   20.167218] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   20.267672] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.268319] lp0: using parport0 (interrupt-driven).
[   20.271764] Linux agpgart interface v0.103
[   20.318235] udev: renamed network interface eth0 to eth1
[   20.373358] agpgart: Detected VIA P4M900 chipset
[   20.394604] vga16fb: initializing
[   20.394612] vga16fb: mapped to 0xc00a0000
[   20.394729] fb0: VGA16 VGA frame buffer device
[   20.577316] Linux video capture interface: v2.00
[   20.676225] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[   20.826399] ppdev: user-space parallel port driver
[   20.826871] gspca: main v2.7.0 registered
[   20.885007] gspca: probing 17a1:0128
[   20.888152] t613: sensor om6802
[   21.279005] gspca: probe ok
[   21.279041] usbcore: registered new interface driver t613
[   21.279046] t613: registered
[   21.417335] Console: switching to colour frame buffer device 80x30
[   21.479387] type=1505 audit(1342869617.552:2):  operation="profile_load" pid=687 name="/sbin/dhclient3"
[   21.485944] type=1505 audit(1342869617.560:3):  operation="profile_load" pid=687 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.486411] type=1505 audit(1342869617.560:4):  operation="profile_load" pid=687 name="/usr/lib/connman/scripts/dhclient-script"
[   21.529625]   alloc irq_desc for 17 on node -1
[   21.529630]   alloc kstat_irqs on node -1
[   21.529642] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.529714] HDA Intel 0000:80:01.0: setting latency timer to 64
[   21.529721] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[   21.714001] input: HDA Digital PCBeep as /devices/pci0000:80/0000:80:01.0/input/input6
[   22.023862] type=1505 audit(1342869618.096:5):  operation="profile_load" pid=807 name="/usr/share/gdm/guest-session/Xsession"
[   22.063175] type=1505 audit(1342869618.136:6):  operation="profile_replace" pid=808 name="/sbin/dhclient3"
[   22.100099] type=1505 audit(1342869618.176:7):  operation="profile_replace" pid=808 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   22.100594] type=1505 audit(1342869618.176:8):  operation="profile_replace" pid=808 name="/usr/lib/connman/scripts/dhclient-script"
[   22.176046] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   22.183432] type=1505 audit(1342869618.256:9):  operation="profile_load" pid=809 name="/usr/bin/evince"
[   22.271388] type=1505 audit(1342869618.344:10):  operation="profile_load" pid=809 name="/usr/bin/evince-previewer"
[   22.306062] type=1505 audit(1342869618.380:11):  operation="profile_load" pid=809 name="/usr/bin/evince-thumbnailer"
hipotent@hipotent-desktop:~$

---

