---
title: "Parallel to USB Adapter: Just can't get the right spec for printers.conf"
date: 2014-01-28
forum: Hardware
---

### Post by LaneLester on 2014-01-28
I am so frustrated. I feel like I'm close to a solution, but I just can't make it.

Someone gave me an HP 2100 printer, and I'm trying to hook it to Ubuntu with a Belkin parallel-to-USB adapter.

The command **lsusb** gives this:
[INDENT]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 002 Device 002: ID 05af:8277 Jing-Mold Enterprise Co., Ltd 
Bus 002 Device 003: ID 041e:1052 Creative Technology, Ltd 
Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 007: ID 050d:0002 Belkin Components[/INDENT]

And the command **ls -l /dev/bus/usb/001/007** gives this:
[INDENT]crw-rw-r-- 1 root lp 189, 6 Jan 28 17:41 /dev/bus/usb/001/007[/INDENT]

But this line in printers.conf doesn't work:
[INDENT]DeviceURI parallel:/dev/bus/usb/001/007[/INDENT]

I've googled a zillion threads about this adapter problem, and some of them recommended this:
[INDENT]DeviceURI parallel:/dev/usb/lp0[/INDENT]
but there is never a /dev/usb directory on my system.

I sure hope you can help me, because I can't afford to buy a new printer.

Lane

---

### Post by LaneLester on 2014-01-29
Well, by combining stuff from various posts in other forums, I think I solved the problem. Here is my new procedure:
[INDENT]Add your printer by selecting a different connection type (since usb and parallel will not be listed)
Close CUPS in application or browser.
Edit the file /etc/cups/printers.conf
Change the DeviceID line to read: DeviceURI parallel:/dev/usb/lp0 

You probably need to execute this to get the dev to show up:
modprobe usblp[/INDENT]

I had to do that last command more than once to get /dev/usb/lp0 to stick. No idea why.

Lane

---

### Post by LaneLester on 2014-01-30
Well, I'm having this conversation with myself, but I want to keep it up to date.

Today I'm out of business again. There's no /dev/usb directory, so this in printer.conf does nothing:
[INDENT]DeviceURI parallel:/dev/usb/lp0[/INDENT]

The command lsmod shows this:
[INDENT]Module                  Size  Used by
usblp                  17885  0 [/INDENT]

I must have done something differently yesterday to get the /dev/usb.

So I don't know what's wrong. I sure wish I could get some help with this.

Lane

---

### Post by steeldriver on 2014-01-30
You may need to unplug and replug the adapter to get udev to detect something present on the port, unfortunately I have not yet found a 'soft' way to do that

Sorry I can't help - no experience with USB-parallel adapters - my experience with USB-serial adapters is that they're usually unreliable :(

---

### Post by LaneLester on 2014-01-30
> **steeldriver said:**
> You may need to unplug and replug the adapter to get udev to detect something present on the port, unfortunately I have not yet found a 'soft' way to do that

Sorry I can't help - no experience with USB-parallel adapters - my experience with USB-serial adapters is that they're usually unreliable :(

Thanks, I may end up doing that. I just finished reading an 11-page thread about this problem. One person said something about adding usblp to /etc/modules. I did that, rebooted, and now I can print again!

Who knows if it will work tomorrow? :-)

Lane

---

