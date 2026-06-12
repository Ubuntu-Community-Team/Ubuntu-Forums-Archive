---
title: "Brother DCP-7010 (USB): &quot;Waiting for printer to become available&quot;"
date: 2014-05-01
forum: Hardware
---

### Post by froebi on 2014-05-01
Hi all,

I'm a long time (k)ubuntu user. And I have this USB printer (Brother DCP-7010) for a long time now, too.
The printer was running without any problems in plug-and-play style in all the last releases up to (including) 13.4. The problems started with 13.10. Now I upgrade to 14.4 but the problem persists:

I have installed all the necessary drivers from the standard repos, I guess:
```

$ dpkg-query -l | grep -i brother
ii  brother-cups-wrapper-laser            2.0.1-2-0ubuntu6                      amd64        Cups Wrapper drivers for laser brother printers
ii  brother-lpr-drivers-common            1.0.0-4-0ubuntu3                      amd64        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-laser             2.0.1-3-0ubuntu5                      amd64        LPR drivers for laser brother printers
ii  brother-udev-rule-type1               1.0.0-1                               all          Brother udev rule type 1
ii  printer-driver-ptouch                 1.3-8                                 amd64        printer driver Brother P-touch label printers

```

The printer correctly shows up in "KDE printer control module" and CUPS (localhost:631). I was also able to print a test page once. But usually, when I want to print something, the status immediatly switches to "Waiting for printer to become available" (and nothing is printed).
The printer is connected to the USB port using "usb://Brother/DCP-7010?serial=000A7J661616" and configured to use "Brother DCP-7010 Foomatic/hl1250 (recommended)" as driver.

I have no idea what the cause of the problem could be. Don't even know where to look. I would really appreciate any pointers and hints.

Christian

PS: I attached 2 screenshots from CUPS

---

### Post by pdc on 2014-05-02
I guess one could suggest using the Brother drivers for your device; from the Brother site: 

[http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcp7010_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcp7010_eu_as&os=128)

Brother offer a Driver Install Tool: 

if selected and saved to your Downloads directory, it comes down as [COLOR="#008000"]linux-brprinter-installer-2.0.0-1.gz
[/COLOR]
the commands they suggest are: (each line being a separate command........)

[COLOR="#FF0000"]cd Downloads
gunzip linux-brprinter-installer-2.0.0-1.gz
sudo bash linux-brprinter-installer-2.0.0-1 DCP-7010[/COLOR]

you should then be able to identify that driver as different to your Foomatic one; and see if it works better?

---

### Post by froebi on 2014-05-03
Hi pcd,

thanks for the reply.

I did the installation using the Driver Install Tool as you suggested. Now, the following packages are installed:
```

$ dpkg-query -l | grep -i brother
ii  brdcp7010lpr                          2.0.1-1                               i386         Brother DCP-7010 LPR driver
ii  brother-cups-wrapper-laser            2.0.1-2-0ubuntu6                      amd64        Cups Wrapper drivers for laser brother printers
ii  brother-lpr-drivers-common            1.0.0-4-0ubuntu3                      amd64        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-laser             2.0.1-3-0ubuntu5                      amd64        LPR drivers for laser brother printers
ii  brother-udev-rule-type1               1.0.0-1                               all          Brother udev rule type 1
ii  brscan-skey                           0.2.4-1                               amd64        Brother Linux scanner S-KEY tool
ii  brscan2                               0.2.5-1                               amd64        Brother Scanner Driver
ii  cupswrapperdcp7010                    2.0.1-2                               i386         Brother DCP7010 CUPS wrapper driver
ii  printer-driver-ptouch                 1.3-8                                 amd64        printer driver Brother P-touch label printers
```

Indeed, there is a new driver available now and the printer is configured to use it: "Brother DCP7010 for CUPS".

But the behaviour did not change. As I clicked on "print test page" the printer's status immediately switched to "Waiting for printer to become available" (and nothing was printed).

Any other idea? Are there maybe some logs that I can search for some diagnostics?

Thanks,
  Christian

---

### Post by gifford on 2014-05-03
I have never used the Brother driver installation tool as my installs are by the CL.
There are a few items on the Brother site that are pre-required.
Can you check to see if /var/spool/lpd exists and that your printer model is in it? 
Also, I assume that you cleared the printers memory.

---

### Post by froebi on 2014-05-03
Hi gifford,

I have all the prerequisites as documented on the Brother site.

@printer memory: I canceled all jobs and turned the printer off and on again. Hope that does the job.

I checked the spool directory and spotted a strange thing:
```

ll /var/spool/lpd/
total 96
drwxr-xr-x 24 root root 4096 Mai  3 19:03 ./
drwxr-xr-x 11 root root 4096 Apr  6  2007 ../
drwx------  2 lp   lp   4096 Apr  6  2007 DCP7010/           <<===
drwxr-xr-x  2 root root 4096 Sep 19  2012 DCP7020/
drwxr-xr-x  2 root root 4096 Sep 19  2012 DCP7025/
drwxr-xr-x  2 root root 4096 Sep 19  2012 DCP8060/
...

```
The "DCP7010" directory is from 2007 and owner:group is lp:lp. Is that supposed to be correct?

Christian

---

### Post by gifford on 2014-05-03
Yes..mine also list lp as the group owner. I am unsure about the dates though as I only have one printer listed and as it is a fairly new install of 14.04 Ubuntu, April 29 is the only date.
My assumption is it is from previous installs. Have you tried uninstalling and doing a reboot and install again? Also, are you using other printers as indicated from the number of drivers you have?

---

### Post by froebi on 2014-05-03
I only have the DCP-7010.
btw: I shortened the list already. The lpd-directory lists a total of 23 printers.

I just noticed another strange and probably serious thing: lsusb does not list my printer at all; here's what lsusb gives.
```
 lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 036: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 012: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

On my laptop though, which also runs kubuntu 14.4., I get:
```
$ lsusb
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 005: ID 04f9:0182 Brother Industries, Ltd Composite Device    <<====
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1020  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I tried turning the printer off and on, plugging the usb-cable out and in, but to no avail.
Could it be a hardware problem? As I mentioned, I was able to print at some point in time. Also all my other usb-devices seem to work without any problems.

Christian

---

### Post by pdc on 2014-05-03
I think if lsusb cannot see the printer; when the printer is powered up; that would seem to be not a good thing

if you turn on the printer and paste the following command into a terminal, what do you get?

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

---

### Post by froebi on 2014-05-04
After turning on my PC this morning I gave it another try: I turned on my printer and there is was, lsusb was listing my printer.
At that point, lpinfo gave the folloing:
```
$ lsusb                                                                                                                                                                                                                                                 
...
Bus 003 Device 004: ID 04f9:0182 Brother Industries, Ltd Composite Device
...
$ /usr/sbin/lpinfo -v
network socket
network ipps
network ipp14
network http
network lpd
network ipp
network https
direct usb://Unknown/Printer       <<====
file cups-pdf:/
direct hp
network smb
direct hpfax

```

I repeated that procedure: turned off the printer, rebooted the PC, turned on the printer again. But this time the printer did not show up in lsusb.
Then lpinfo gave this:
```

$ /usr/sbin/lpinfo -v
network socket
file cups-pdf:/
network ipps
network ipp14
direct hp
network https
network http
network ipp
network lpd
network smb
direct hpfax

```

Strange...

---

### Post by froebi on 2014-05-04
Here's what I found in /var/log/syslog when turning the printer on:
```
May  4 11:44:47 froebi-desktop kernel: [  232.640239] usb 3-1: new full-speed USB device number 16 using xhci_hcd
May  4 11:44:47 froebi-desktop kernel: [  232.640419] usb 3-1: Device not responding to set address.
May  4 11:44:47 froebi-desktop kernel: [  232.844552] usb 3-1: Device not responding to set address.
May  4 11:44:48 froebi-desktop kernel: [  233.048498] usb 3-1: device not accepting address 16, error -71
May  4 11:44:48 froebi-desktop kernel: [  233.160678] usb 3-1: new full-speed USB device number 17 using xhci_hcd
May  4 11:44:48 froebi-desktop kernel: [  233.160875] usb 3-1: Device not responding to set address.
May  4 11:44:48 froebi-desktop kernel: [  233.365004] usb 3-1: Device not responding to set address.
May  4 11:44:48 froebi-desktop kernel: [  233.569015] usb 3-1: device not accepting address 17, error -71
May  4 11:44:48 froebi-desktop kernel: [  233.681089] usb 3-1: new full-speed USB device number 18 using xhci_hcd
May  4 11:44:48 froebi-desktop kernel: [  233.681290] usb 3-1: Device not responding to set address.
May  4 11:44:48 froebi-desktop kernel: [  233.885451] usb 3-1: Device not responding to set address.
May  4 11:44:49 froebi-desktop kernel: [  234.089375] usb 3-1: device not accepting address 18, error -71
May  4 11:44:49 froebi-desktop kernel: [  234.201570] usb 3-1: new full-speed USB device number 19 using xhci_hcd
May  4 11:44:49 froebi-desktop kernel: [  234.201749] usb 3-1: Device not responding to set address.
May  4 11:44:49 froebi-desktop kernel: [  234.422130] usb 3-1: device descriptor read/8, error -71
May  4 11:44:49 froebi-desktop kernel: [  234.542200] usb 3-1: device descriptor read/8, error -71
May  4 11:44:49 froebi-desktop kernel: [  234.646028] hub 3-0:1.0: unable to enumerate USB device on port 1

```

That doesn't look promising...

---

### Post by gifford on 2014-05-04
Maybe time for a clean install of 14.04?

---

### Post by froebi on 2014-05-04
Here is the syslog-excerpt from my laptop (where lsusb listed the printer correctly) when turning the printer on:
```
May  4 19:21:02 froebi-laptop2 kernel: [  557.800236] usb 2-1.2: new full-speed USB device number 5 using ehci-pci
May  4 19:21:02 froebi-laptop2 kernel: [  557.897724] usb 2-1.2: New USB device found, idVendor=04f9, idProduct=0182
May  4 19:21:02 froebi-laptop2 kernel: [  557.897736] usb 2-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=3
May  4 19:21:02 froebi-laptop2 kernel: [  557.897743] usb 2-1.2: SerialNumber: 000A7J661616
May  4 19:21:02 froebi-laptop2 mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
May  4 19:21:02 froebi-laptop2 mtp-probe: bus: 2, device: 5 was not an MTP device
May  4 19:21:02 froebi-laptop2 kernel: [  558.280943] usblp 2-1.2:1.0: usblp1: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0182
May  4 19:21:02 froebi-laptop2 kernel: [  558.280975] usbcore: registered new interface driver usblp

```

Also I was able to print the test page several times. All with standard packages.
Can anyone make something of that?
The one thing I notice is that on my desktop it says "using xhci_hcd" where on my laptop it says "using ehci-pci". But I guess this is ok and due to the difference in hardware?

---

### Post by pdc on 2014-05-04
when I see 

> The one thing I notice is that on my desktop it says "[COLOR="#EE82EE"]using xhci_hcd[/COLOR]" where on my laptop it says "[COLOR="#EE82EE"]using ehci-pci[/COLOR]"

it reminds me of another scanning thread that is running

[http://ubuntuforums.org/showthread.php?t=2220043&p=13010402#post13010402](http://ubuntuforums.org/showthread.php?t=2220043&p=13010402#post13010402)

this is yet another thing I don't know about: (I was thinking a day ago about suggesting what gifford suggested; a clean install of 14.04 as it will be a LTS that will be supported for five years; however maybe that isn't the issue; it is all very unclear what is happening on your systems...............)

---

