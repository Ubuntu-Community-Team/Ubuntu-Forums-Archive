---
title: "Bitpim Help on LG Phone"
date: 2008-11-23
forum: Hardware
---

### Post by zstraub1 on 2008-11-23
I have an LG Dare phone and downloaded the most recent version of Bitpim. I want to be able to transfer music on my computer to the phone via usb. The system is recognizing my phone and model but it's still not connected. I think i've narrowed it down to two things: either the port needs to be opened, or the linux usb needs to be set up to recognize the phone. I think it's the latter option.

Here's some information that Bitpim says:
Property	Value	Description
PID	0x6000	Product ID
VID	0x1004	Vendor ID
active	True	Your operating system shows this driver and port is correctly configured and a device attached
[COLOR="Red"]available	False	It was not possible to open this port[/COLOR]
description	USB Device - Vendor LG Electroncs, Product VX Series Phone (Direct USB connection), (Interface Modem Interface)	 
driver-required	True	This indicates if you must use a device driver, not direct USB access
libusb	True	This indicates if the usb library is in use to access this device. Operating system device drivers (if any) are bypassed when BitPim talks to the device
name	usb::001::003::1	This is the name the port is known to your operating system as
protocol	Data / Generic

In this tutorial at   [http://www.bitpim.org/help/](http://www.bitpim.org/help/)  it gives me instructions but I'm still a complete amateur (ex: i don't know how to create a ******* cellusers group- I don't even know what that is), so I'm having difficulties. I use undev (and it is on), not hotplug (so it would be option 2 on the tutorial).
I would greatly appreciate it if someone could walk me through this and explain it to me so I understand it.

---

### Post by Ehtetur on 2008-12-21
> **zstraub1 said:**
> In this tutorial at   [http://www.bitpim.org/help/](http://www.bitpim.org/help/)  it gives me instructions..
My phone has the same PID/VID as yours and I was having the same problem: I could only access my phone as root... I went to the help page in your post and was able to access my phone as normal user..

Note - I'm running Hardy:

System --> Administration --> Users and Groups

Click the button marked 'Unlock' and when prompted, type in your password for root access.

Click the button marked 'Manage Groups'.

Click the buttom marked 'Add Group'.
Type the word cellusers in the Group Name field.
In the Group Members section, click on the radial button next to your name.

Click the OK button and voilà you're a member of cellusers. :twisted:

---

