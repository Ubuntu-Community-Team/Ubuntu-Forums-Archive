---
title: "Logic Controls pole disply"
date: 2022-04-26
forum: Hardware
---

### Post by erictherev on 2022-04-26
As part of my job, I often reuse or recycle Point of Sale hardware. One piece of equipment I have gotten my hands on more than once is a Logic Controls PD3000/PD6000 series two-line serial pole display. This has a standard 9-pin serial connector (I know, deprecated/obsolete hardware).

Since I have gotten several of these that are in working condition, I would like to be able to use them. It would seem that it would be easiest to make these work in a linux system (as opposed to M$). I am in the process of rebuilding 3 servers (an ubuntu server based file server, an ubuntu server based web server and a pfSense router) and would like to see about utilizing these displays on one or two of these systems, ideally the router and file server.

Does anyone know how I would go about setting these up to display information such as file system usage and web traffic? So far I know these would be addressed as /dev/ttyS0, /dev/ttyS1, etc. I am interested in how to output the relevant information to these ports.

Thanks in advance.

---

### Post by #&amp;thj^% on 2022-04-26
Back in the day, their customer support was outstanding, do you have the manual: [https://www.manualslib.com/manual/292675/Logic-Controls-Pd3000.html?page=8#manual](https://www.manualslib.com/manual/292675/Logic-Controls-Pd3000.html?page=8#manual)

---

### Post by erictherev on 2022-04-26
> **1fallen said:**
> Back in the day, their customer support was outstanding, do you have the manual: [https://www.manualslib.com/manual/292675/Logic-Controls-Pd3000.html?page=8#manual](https://www.manualslib.com/manual/292675/Logic-Controls-Pd3000.html?page=8#manual)

That is, in fact, the manual for the device I am working with. Unfortunately, this only has Windows information, which I already have.

Based on the Windows testing, if I enter **TYPE>COM1** then press **ENTER**, anything I enter after this point will display on the pole display. I know this to be a functional Windows test as I use it often. It stands to reason based on what I have already found,  that if I were to enter the linux equivalent of **TYPE>** followed by the port (i.e. **ttyS1**) then I should be able to do something similar. I don't know what the linux equivalent of **TYPE>** would be, but this would likely only work for testing purposes.

My question is how to automate this, in Ubuntu, to display disk usage / disk availability on one device and traffic in / out on the other. I would like all of this to update in something close to realtime (every 30 to 60 seconds should be sufficient).

To be clear, what I am hoping to achieve would be something like this:

_File server_
DISK USAGE:   X.x GB
FREE SPACE:    X.x GB

_pfSense router_   (Disclaimer: as pfSense is a FreeBSD-based distro, I understand that the answer in Ubuntu may vary from the answer for pfSense.)
TRAFFIC IN:      X.x Kbps
TRAFFIC OUT:    X.x Kbps

This would give me at-a-glance statistics for these systems, without the need for a traditional monitor. I know information like this can be displayed on screen using a package like Conky (which I am a big fan of for desktop systems). I would like to pipe this information to the pole displays, which I intend to mount to the back of my half server racks so that the poles stick up in the back.

Any information that could point me in the right direction would be greatly appreciated.

---

### Post by erictherev on 2022-05-11
I understand that my original inquiry could be a bit specific.

Does anyone have any input on outputting relevant system information to a two-line serial display?

---

### Post by #&amp;thj^% on 2022-05-11
I hope I understand you, forgive if I'm off track, but would something like this be useful?
```
sudo setserial -g /dev/ttyS[0123]
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

```
This is far to long for your request:
```
sudo dmesg | egrep -i --color 'serial|ttyS'
[    0.626973] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.629408] usbcore: registered new interface driver usbserial_generic
[    0.629411] usbserial: USB Serial support registered for generic
[    1.473321] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.473325] usb usb1: SerialNumber: 0000:04:00.3
[    1.473636] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.473639] usb usb2: SerialNumber: 0000:04:00.3
[    1.474124] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1

```
that's just a brief listing.
or again:
```
sudo setserial -g /dev/ttyS[0123]
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

```
The setserial with -g option help to find out what physical serial ports your Linux box has,
man page: [https://linux.die.net/man/8/setserial](https://linux.die.net/man/8/setserial)

---

### Post by erictherev on 2022-05-13
> **1fallen said:**
> ```
sudo setserial -g /dev/ttyS[0123]
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

```
The setserial with -g option help to find out what physical serial ports your Linux box has,
man page: [https://linux.die.net/man/8/setserial](https://linux.die.net/man/8/setserial)

This seems like a great place to start. Once I have this system fully built this will help me to determine where I am attempting to output data to. Once I have a serial port number then I can move toward scripting something that would do what I need it to do.

Forgive me, but I don't have this fully in place yet. This is a whole new server build from the ground up. The first one I am working on is my Ubuntu file server since I am familiar with this. So far I have the server built, Ubuntu installed on an SSD, my RAID array built, functioning, and recognized by the OS consistently, the array automounting consistently, and a bit of data on the array. Once I have my OS fully configured, including this project and all of my SMB configuration, I am going to clone my OS SSD to a second SSD then unhook power from the backup drive. At that point I will be ready to rackmount this beast.

---

### Post by #&amp;thj^% on 2022-05-13
Sounds fun, keep us/me posted.

---

