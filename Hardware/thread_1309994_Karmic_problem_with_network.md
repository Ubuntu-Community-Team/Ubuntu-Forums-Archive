---
title: "Karmic problem with network"
date: 2009-11-01
forum: Hardware
---

### Post by andrewkoff on 2009-11-01
Dear gurus!

I have clean install of Karmic on laptop Acer Aspire 5739g. I also have Win7 installed.

Problem: network cards (wired and wireless) work fine in Win7, but then I boot Ubuntu 9.10 - no network!
I have googled, that Win disables network interfaces during shutting down so Ubuntu can't use it at all. It looked right - there were no green/orange LEDs lighting/flashing on ethernet port. I've changed WOL properties of network interfaces in Win7 to stay enabled after shut down and green LED light up. All that didn't fix a problem - Ubuntu network doesn't start up.

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a74 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
```lshw -C network:
```
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:be000000-be001fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd cap_list
       configuration: latency=0
       resources: memory:be100000-be13ffff ioport:3000(size=128)

```And there's no network interfaces in /etc/X11/interfaces except lo

I dont like those UNCLAIMED :(

Any help is appreciated...

---

### Post by gecko1337 on 2009-11-01
Ive been looking for a solution for days now, and nothing:(
If you really want to use the network you'll have to turn off ACPI :/
which isnt really an option for me, so please if anyone out there has an answer:o

---

### Post by andrewkoff on 2009-11-02
Thanx a lot, gecko1337!
Turning off ACPI really helps.
At least now I can install some software.
I hope next kernel release will cure ACPI :p.

---

### Post by gecko1337 on 2009-11-03
UP!
is there anything I can do to fix this or do I have to wait for a new version?:mad:

---

### Post by andrewkoff on 2009-11-03
I don't know what to do indeed...
Let's keep this thread alive - any problem can be solved. In time.:D
I have network working in Fedora 11 installed on this laptop. Maybe changing distro can help. :mad:

---

### Post by gecko1337 on 2009-11-03
Yeah too bad, I really liked Ubuntu QQ
Ah awell you cant have it all in life :p
going to install Fedora/SuSe when I have time...

---

### Post by necromonger on 2009-11-03
I have a wusb54g and 9.10 picked it up at start up.please do a bug report it may help a lot of other people to.

---

### Post by OstergrenDan on 2009-11-03
I'm  having this same issue with an Acer Aspire 5520-5377, which was previously running Windows Vista. I have no idea what to do to fix this problem, nor do i know how to disable an ACPI, much less even know what ACPI really functions as, and the disadvantages of allowing it to run. Any help would be greatly appreciated.

---

### Post by andrewkoff on 2009-11-03
**2 OstergrenDan:**

To turn off ACPI you should edit (sudo required)  your grub configuration file. It might be /boot/grub/menu.lst or /boot/grub/grub.cfg.

1. Search content of the file for (e.g.) line:
"linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=6f2e6ee8-6477-4fd4-885f-f7a4d838938f ro   quiet splash"

2. Add "acpi=off" to the end of line.

3. Save, reboot, hope and pray... Of course backup is needed.

4. Then ACPI is off, you won't have a correct power management of your laptop. Read wiki for details.

**2 necromonger**
Report a bug... How could we do it? I am ready, but don't know how-to.
[B]
2 gecko1337[/B]
What is the beast - Ubuntu QQ?:lolflag:

---

### Post by OstergrenDan on 2009-11-05
I'm very sorry to be the newbie here, but thats all a bunch of jibberish to me. =_=

---

### Post by sergio jose dias on 2009-11-06
Try that solution of link:
[http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html](http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html)

---

### Post by agustin.g on 2009-11-08
> **OstergrenDan said:**
> I'm very sorry to be the newbie here, but thats all a bunch of jibberish to me. =_=
Could you post the output of ```
lspci -v 
``` if you can cut out the two paragraphs concerning your network devices (they should be rather easy to detect) that would be good, as it limits the amount of data we have to look through.

As for myself, i also have an Intel WiFI 5100 card, and disabling ACPI doesn't change much. The link  provided doesn't help either because i have no wlan0 interface to speak of, all i have is the extremely useful loopback interface. Anyways, I think i'll be going back to 9.04 for the next few months.

---

### Post by Manyette on 2009-11-08
Just as a cautionary note to all who newly install Ubuntu.  You MUST have a cable to your router/modem plugged in during the install.  If you do not, Ubuntu will not autolocate your ethernet connection and set it up for you.

---

### Post by GreenEU on 2009-11-08
Unfortunately, even being hooked up at install isn't infallible. I can see the networks (including my own) but just can't access them *unless* I go onto the ethernet.

---

### Post by gecko1337 on 2009-11-08
[LEFT]read this :)
[http://ubuntuforums.org/showthread.php?p=8201349](http://ubuntuforums.org/showthread.php?p=8201349)

about ACPI: [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
[/LEFT]

---

### Post by agustin.g on 2009-11-09
> **Manyette said:**
> Just as a cautionary note to all who newly install Ubuntu.  You MUST have a cable to your router/modem plugged in during the install.  If you do not, Ubuntu will not autolocate your ethernet connection and set it up for you.
Did that and Ubuntu was unable to even locate the network interface. Idem with ACPI, added the ```
acpi = off
``` via GRUB just before booting and no luck whatsoever. Let's just hope it gets fixed.

---

### Post by agustin.g on 2009-11-10
You could try reading up on this:

[http://ubuntuforums.org/showthread.php?t=1307396]("http://ubuntuforums.org/showthread.php?t=1307396")

---

