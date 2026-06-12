---
title: "Problem: The printer isn't printer or do anything at all"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by nadavvin on 2006-11-11
Hello

I have 720c HP printer.

I can print in windows but not in linux?


What is the problem???

---

### Post by happy-and-lost on 2006-11-11
Have you set it up properly, using the printer wizards in Ku/U?

---

### Post by nadavvin on 2006-11-11
> **happy-and-lost said:**
> Have you set it up properly, using the printer wizards in Ku/U?

I don't know.

I use the wizard but:
[[IMG]http://img182.imageshack.us/img182/8417/printerwizardmd1.th.png[/IMG]](http://img182.imageshack.us/my.php?image=printerwizardmd1.png)

I have HP no CANON nor EPSON.

I choose hp no_device_found and then chouse the specific printer from the next list.

The test page was sent successfully but the printer didn't work or sound something.

---

### Post by happy-and-lost on 2006-11-11
Go to the terminal and type "sudo hp-setup", if all goes well, it should detect and set up your printer. All you need to do is press enter many times.

---

### Post by nadavvin on 2006-11-11
> **happy-and-lost said:**
> Go to the terminal and type "sudo hp-setup", if all goes well, it should detect and set up your printer. All you need to do is press enter many times.

```

$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.6.9)
Printer/Fax Setup Utility ver. 2.2

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No devices found.
error: Error occured during interactive mode. Exiting.

```

---

### Post by happy-and-lost on 2006-11-11
How is it connected? Parallel or USB?

---

### Post by nadavvin on 2006-11-11
> **happy-and-lost said:**
> How is it connected? Parallel or USB?

Parallel

---

### Post by happy-and-lost on 2006-11-11
Try the Canon or Epson. It may have wrongly detected the printer, I haven't used KDE in about a year, but I *think* it should ask you what specific model it is from the database of CUPS drivers, which should rectify that problem. Give it a go.

---

### Post by nadavvin on 2006-11-11
> **happy-and-lost said:**
> Try the Canon or Epson. It may have wrongly detected the printer, I haven't used KDE in about a year, but I *think* it should ask you what specific model it is from the database of CUPS drivers, which should rectify that problem. Give it a go.

I choose Canon and then I get the list of the printers and choose hp 720c

When I print the test page, the printer start to work!!

but It's print very slow and stop for a while and continune again other and other.

and the print quality is very low!

What is the problem????

Can it harm my printer??

What is the problem???

---

### Post by happy-and-lost on 2006-11-11
Right. I had exactly that problem with my HP parallel printer, what you need to do is...

sudo apt-get install hpoj

and here's what happened when I did that...
```
kjz@kjz-desktop:~$ sudo apt-get install hpoj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  sane mtools hpoj-xojpanel
The following NEW packages will be installed:
  hpoj
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 455kB of archives.
After unpacking 1348kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com edgy/universe hpoj 0.91-10 [455kB]
Fetched 455kB in 2s (218kB/s)
Selecting previously deselected package hpoj.
(Reading database ... 131825 files and directories currently installed.)
Unpacking hpoj (from .../archives/hpoj_0.91-10_i386.deb) ...
Setting up hpoj (0.91-10) ...
hpoj: To enable scanning with sane you must
hpoj: manually uncomment the hpoj entry in /etc/sane.d/dll.conf.

Stopping the HP OfficeJet Linux driver.

----------------------------------------------------------------------

This program manages devices controlled by the HP OfficeJet Linux
driver (hpoj).  It attempts to probe your computer for local parallel-
and USB-connected devices, and allows you to specify network addresses
for remote JetDirect-connected devices.

If you experience any difficulties in detecting your device(s), then
refer to the hpoj documentation for troubleshooting information.

----------------------------------------------------------------------

Currently defined device names ([*]=default):
    (none)

----------------------------------------------------------------------

Probe for parallel-connected devices ([y]/n)?  y

Successfully loaded kernel module "lp" for the device probe.

Warning: Probing incorrect I/O port addresses could result in system
instability and/or data loss!  Consult your hardware documentation, BIOS
setup and/or kernel messages to verify correct base addresses in the
following prompts.   Also, take care not to probe parallel ports that
have non-printer devices (such as disk or tape drives) connected.

Probe parallel port "-base 0x378 -basehigh 0x778 -device /dev/lp0" (y/[n])?  y

    Found "OfficeJet G55"
    with serial number "SGG0CE2CM1VL".

    This device will be set up as "mlc:par:OfficeJet_G55".
    Press <Enter> alone to continue or <Ctrl-D> to skip this device, or
    enter a different desired name suffix (without the "mlc:par:" prefix)
    here ---> 

    Setting up as "mlc:par:OfficeJet_G55".
    Enabling ptal-mlcd and ptal-printd.

Press <Enter> alone to continue, or if you would like to probe an
undetected parallel port, then enter its hexadecimal base address
(such as "378", "278", or "3BC") here --->  

----------------------------------------------------------------------

Probe for USB-connected devices ([y]/n)?  n

----------------------------------------------------------------------

Press <Enter> alone to continue, or if you would like to add a
JetDirect-connected device, then enter its dotted-decimal
IP address or hostname here --->  

----------------------------------------------------------------------

Done updating device configuration files stored under /etc/ptal.
If you make manual changes to those files, then be sure to run
"/etc/init.d/hpoj start" so they will take effect.

----------------------------------------------------------------------

Starting the HP OfficeJet Linux driver.
    mlc:par:OfficeJet_G55


Stopping the HP OfficeJet Linux driver.
Starting the HP OfficeJet Linux driver.
    mlc:par:OfficeJet_G55
```

And there you have it. It works. After you've done that the wizard should detect it.

This should work much better, as it's using the correct driver!

---

### Post by nadavvin on 2006-11-11
problem:
```

Probe parallel port "-base 0x378 -basehigh 0x778 -device /dev/lp0" (y/[n])?  y

    No device found.

```

---

### Post by nadavvin on 2006-11-12
What is the problem???

---

### Post by nadavvin on 2006-11-18
The edgy ubuntu which install in my computer is upgrade from dapper.


I download now ubuntu 6.10 desktop and I'm now writing from the livecd.

I open gedit, write something and click to print.

The HP printer wasn't there but I press on the buttom of the add printer.

Ubuntu was recognize my HP printer and its model and after three clicks the printer was set.

I press to print the text but the printer didn't start to work.

What is the problem????

---

