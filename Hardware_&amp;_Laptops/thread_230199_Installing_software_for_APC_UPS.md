---
title: "Installing software for APC UPS"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by wpshooter on 2006-08-05
I have marked and installed the **APCUPSD** software in Synaptic software package manager.

But now, I do NOT see any APCUPS software shown on any of the menus.

Where is this software installed and how do I call it ?

Thanks.

---

### Post by fubadubrub on 2006-08-06
> **wpshooter said:**
> I have marked and installed the **APCUPSD** software in Synaptic software package manager.

But now, I do NOT see any APCUPS software shown on any of the menus.

Where is this software installed and how do I call it ?

Thanks.

The apcupsd software has no menu entry.  Assuming your using the Gnome desktop, Open your terminal.  **Applications>Accessories>Terminal**.
Now type: **sudo gedit /etc/apcupsd/apcupsd.conf**
A text editor opens up.  Please note that the examples shown below are from my computer and **you need to adapt them to your computer**.  Scroll down very slightly untill you reach this section:

> # UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
UPSCABLE usbChange the **UPSCABLE** to the one that **matches your paticular battery backup**


Scroll down to the next section:
> # To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB.
#                            A blank DEVICE setting enables
#                            autodetection, which is th best choice
#                            for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's 
#                            rfc1628 UPS-MIB. Port is usually 161. 
#                            Community is "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
UPSTYPE usb
DEVICEAgain select the right options for **your ups unit**
Also note that "# usb       <BLANK>" is not literal, so don't type <BLANK> just leave a blank space.


Now click the save button in the text editor and then close it.


Now keeping your terminal open type:
**sudo gedit /etc/default/apcupsd**

> # Apcupsd-devel internal configuration

APCACCESS=/sbin/apcaccess
ISCONFIGURED=yesSee the **"ISCONFIGURED=no"**.  Change the **no** to **yes** just like in my example.


Now click the save button in the text editor and then close the editor.


Keeping your terminal open type:
**sudo /sbin/apcupsd**

Look for any errors, if you don't see any thing great.


Keeping your terminal open type:
**gedit /var/log/apcupsd.events**

Don't do any thing in here, just look.  It is a log file.  Look for an entry like this:
[B]Sun Aug 06 11:15:00 PDT 2006  apcupsd 3.12.1 (06 January 2006) debian startup succeeded

[/B]

Congratulations.  Hope this helps.

---

### Post by gmc on 2006-08-23
Thanks! 

Even thought there's not much to edit in the configuration, this helped me get my APC 650 up and running in a few minutes.

Bring on those nasty power failures :-)

G.

---

### Post by cdeel77 on 2007-03-11
Thanks a lot for that ISCONFIGURED=yes tip. It appeared that the daemon wouldn't start up until I added that.  Thanks for the help!

---

### Post by sanitycheck on 2007-03-13
I am surprised that anyone with a USB signal cable got apcupsd to run without first having to create the hiddev devices.  I use Edgy 64-bit with an APC Back-UPS ES 500.  I had to run a script to create the hiddev devices before the UPS could be seen on the USB bus.  I remember having to do this on my old Debian Sarge server as well.

I used this information:

"Apcupsd accesses USB UPSes via the hiddev device nodes. Typically these are located in /dev/hiddevN, /dev/usb/hiddevN or /dev/usb/hiddev/hiddevN (where N is a digit 0 thru 9). Some distributions (some Debian releases, possibly others) do not provides these device nodes for you, so you will have to make them yourself. Check /dev, /dev/usb, and /dev/usb/hiddev and if you cannot find the hiddevN nodes, run (as root) the examples/make-hiddev script from the apcupsd source distribution."

From here:

[http://www.apcupsd.com/manual/USB_Configuration.html](http://www.apcupsd.com/manual/USB_Configuration.html)

The make-hiddev script to run is located here:

/usr/share/doc/apcupsd/examples/make-hiddev

The make-hiddev script has to be run as root (sudo) of course.  Only after that did the log file give me "debian startup succeeded."

I have not checked yet to see if this will survive a reboot, but I am reasonably sure it will.

---

### Post by majoridiot on 2007-03-31
> **fubadubrub said:**
> The apcupsd software has no menu entry...   Hope this helps.

yes, it was VERY helpful.  i got two apc units up and running in less than 30 minutes following these
instructions... and the bulk of that time was spent unpacking the apc unit and plugging things in!

you just GOTTA LOVE our ubuntu forums!

and thank you very much, fubadubrub!

---

### Post by huck416 on 2007-06-11
Hi, 

Ran everything fubadubrub said and it worked, although, when tested by pulling the plug, I did not get a warning to log off as I thought I would after 60 seconds. Any idea why or what I may be missing? Thanks.

---

### Post by coolbrook on 2007-12-27
This is the output of my log```

Thu Dec 27 14:50:36 EST 2007  Valid lock file for pid=5810, but not ours pid=5817
Thu Dec 27 14:50:36 EST 2007  apcupsd FATAL ERROR in device.c at line 70
Unable to create UPS lock file.
  If apcupsd or apctest is already running,
  please stop it and run this program again.
```I'll have a look at the apcupsd site as soon as I get a chance.

---

### Post by sudhashen on 2008-01-11
running ubuntu server 7.10 with apc cs 650 ups on usb connection.

Followed fubadubrub's clear instructions, rebooted and it worked!  did not have to create hiddevN devices.

Thank you fubadubrub!:guitar:

viva ubuntuforums! :KS

---

