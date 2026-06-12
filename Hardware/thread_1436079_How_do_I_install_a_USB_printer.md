---
title: "How do I install a USB printer?"
date: 2010-03-22
forum: Hardware
---

### Post by colourfullegume on 2010-03-22
I have a Laserjet 4L printer and can easily install it assigned to LPT #1.

However, it is not connected to LPT #1 but via a USB port, as follows:

*  Motherboard USB Port -> KVM Switch* -> USB to Parallel Cable -> Printer*

I think the KVM Switch is irrelevant but I have noted it here for completeness.  

I think the important "device" is the USB to Parallel Cable, which came with a Windows driver.  Windows created a "Virtual USB Port" that I could assign to the printer.

I think the cable contains a Prolific PL-2305 chip.  I've thrown away the packaging, so not sure about this, but I still have the driver CD which refers to PL-2303 - a USB to Serial device - and to the company Prolific.  (Link to Prolific website: [http://www.prolific.com.tw/eng/Products.asp?ID=6](http://www.prolific.com.tw/eng/Products.asp?ID=6))

**How do I install the printer in Ubuntu 9.10?**

[SIZE=1]*[Note: A KVM Switch is a device which allows me to press a switch to alternate between allowing one of two computers to soft-connect to my keyboard, monitor (video), mouse and printer.  The four devices are connected to the KVM switch, and the KVM switch is then connected to the two computers.]*[/SIZE]

---

### Post by ellgor on 2010-03-22
Hi, 

In a terminal type in :

lsusb

and see what shows up, if the printer is there open up printers from the Admin section and carry on from there, if its not check to see if you have an app called usbutils or even usbmount.

Regards, Ellgor.

---

### Post by pricetech on 2010-03-22
I've used a couple of those USB to Parallel cables myself.  I never needed a driver for anything other than 9x since USB printing support was built in to 2k and above.  Great little devices, actually.

Back to your problem:  Try connecting the USB cable directly to the computer.  The KVM could be an issue, well worth the few minutes it takes to test it.

---

### Post by jrssystemsnet on 2010-03-22
If you're willing to spend a little bit of scratch... I don't think the LPT -> USB cable is a great choice of gear.  I would instead strongly recommend a JetDirect type printserver.

[http://www.google.com/products/catalog?q=jetdirect+300x&cid=5244186072316720172#](http://www.google.com/products/catalog?q=jetdirect+300x&cid=5244186072316720172#)

Or try [http://www.newegg.com/Product/Product.aspx?Item=N82E16833162203](http://www.newegg.com/Product/Product.aspx?Item=N82E16833162203); this should work just as well, though I've never used one of these specifically.  (It's just less common to *need* one anymore, since almost anything decent comes with Ethernet service built-in to the printer these days.)

AVOID Netgear, D-Link, etc "printservers"; they usually require a special driver installed on the host computer which is 1. windows specific and 2. doesn't work worth a snowball in Miami.

---

### Post by colourfullegume on 2010-03-23
Thanks everyone for your replies.  Unfortunately, I have not had any luck so far, but here are some results:

**First suggestion: ellgor - lsusb**

$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 020: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 019: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 018: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 009: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Lines 1 & 2, I believe are the USB ports built into the motherboard.
Lines 3, 4 & 5 relate to the KVM switch (line 5 = the switch itself).
Lines 6 & 7 are:
  * a PCI card with two USB ports on it
  * a 4-port hub that is plugged into the motherboard.
I'm not sure which is which although I suspect that line 7 is the PCI card.

The USB-Parallel cable is plugged into the 2nd motherboard USB port but does not show up in the list.

**Second suggestion: ellgor - usbutils / usbmount**

None of these commands works in the terminal - is there a way to install them?

[B]Third suggestion: pricetech - remove KVM Switch
[/B]
Done this - no difference

[B]Fourth suggestion: jrssystemsnet - use a print server
[/B]
This is an expensive option (although the HP JetDirect 300X is $42 on google.com, it is £153 on google.co.uk and I live in England).  In addition, it will have to be wireless (which I think is more expensive) because I do not have *any* network cabling whatsoever near the printer - the computer is wireless too.   Running cabling would mean messing up my house.  The Buffalo device (second link) doesn't make sense as it it LAN to USB and my printer has a parallel port.

**Further attempts**

I have also googled a bit and found that the USB-Parallel cable should work via the device /dev/usb/lp0 - I tried using the Add Printer wizard in GNOME adding an "LPD/LPR Host or Printer" with Host=localhost and Queue=/dev/usb/lp0 (so the device URI is lpd://localhost/dev/usb/lp0).  It then adds the printer but nothing prints.  There are two error messages in floating popup windows when I print a test page:

  * **Not connected?** Printer 'HP-Laserjet-4L' may not be connected
  * **Printer warning:** Printer 'HP-Laserjet-4L': 'com.apple.print.recoverable'

I think this just means that /dev/usb/lp0 is not connected to anything.

I looked in /etc/modules and there is only one line (ignoring the comments at the start):
lp

*Any other suggestions would be most welcome*.

---

### Post by ellgor on 2010-03-23
Hi again,

The usbmount/usbutils are apps that can be got in synaptic.

I've just noticed that its a HP model, there are a number of apps in synaptic specifically for HP's you might want to check them out.

Regards, Ellgor.

---

### Post by pricetech on 2010-03-23
> **jrssystemsnet said:**
> If you're willing to spend a little bit of scratch... I don't think the LPT -> USB cable is a great choice of gear.  I would instead strongly recommend a JetDirect type printserver.

Agreed.

> **jrssystemsnet said:**
> AVOID Netgear, D-Link, etc "printservers"; they usually require a special driver installed on the host computer which is 1. windows specific and 2. doesn't work worth a snowball in Miami.

Agreed, accept for Netgear.  While I have come to loathe Netgear from a customer service standpoint, I have never had a problem with a Netgear Print Server under any Linux distro I've ever used.

> **colourfullegume said:**
> [B]Third suggestion: pricetech - remove KVM Switch
[/B]
Done this - no difference


Oh well, it was worth a try.

It doesn't appear that your USB / Parallel cable is being seen.  Maybe just not compatible with Linux.

---

### Post by colourfullegume on 2010-03-23
Here's an exciting new development!  I read the man page on lsusb and discovered the -t option - note that the device numbers have changed because I have rebooted and have been removing and reinserting USB jacks:

**~$ lsusb**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100
Bus 001 Device 008: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 007: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 006: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 003: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**~$ lsusb -t**
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 3, If 0, Class=stor., Driver=usb-storage, 480M
        |__ Port 2: Dev 10, If 0, Class=vend., Driver=pac207, 12M
[SIZE=2]**        |__ Port 3: Dev 9, If 0, Class=print, Driver=usblp, 12M**[/SIZE]
        |__ Port 4: Dev 6, If 0, Class=hub, Driver=hub/4p, 12M
            |__ Port 4: Dev 8, If 0, Class=HID, Driver=usbhid, 1.5M


I have highlighted the one that shows the USB-Parallel cable.  Now I just need to figure out how to access it.

Also, thanks for the info on usbutils/usbmount.  I'd never used Synaptic before but have now installed usbmount.  Also discovered that usbutils is simply the package for lsusb.

I only tried lsusb -t after installing usbmount, so not yet sure whether that has made the difference.  However, notice that lsusb (without -t) still does not show the lp.

---

### Post by colourfullegume on 2010-03-23
Another bit of a clue ... 
[http://www.qbik.ch/usb/devices/showdev.php?id=2955](http://www.qbik.ch/usb/devices/showdev.php?id=2955)

It shows that a device based on the PL-2305 is supported ... which matches that we can see the usblp device when using lsusb -t.

I've removed usbmount via Synaptic as it is not supported by Canonical and  it seems an equivalent package is already included in Ubuntu:

**~$ ps -ef | grep udev**
root       467     1  0 20:38 ?        00:00:00 upstart-udev-bridge --daemon
**root       470     1  0 20:38 ?        00:00:00 udevd --daemon**
bean      3055  2068  0 21:45 pts/0    00:00:00 grep --color=auto udev

---

### Post by Muzer on 2010-03-23
Just a random guess - maybe the device node has already been created but just in an odd place. Try:

ls /dev/*lp*

ls /dev/*/*lp*

if anything comes back other than the standard /dev/lp0, etc., this could well be it.

---

### Post by colourfullegume on 2010-03-23
The other things that come up are

/dev/usblp0 (a symbolic link)
/dev/usb/lp0 (to which the above link refers)

Maybe this isn't sensible but I've tried

echo . > /dev/usb/lp0 and get 'Permission denied'.

Also, I may not be setting the URI correctly when setting up the printer (lpd://localhost/dev/usb/lp0)

Another perhaps disappointing find: [http://www.qbik.ch/usb/devices/showdev.php?id=3510](http://www.qbik.ch/usb/devices/showdev.php?id=3510)
I think this refers directly to the Prolific PL-2305 (although it doesn't say so) and it states

[INDENT]*[FONT=Arial]BEWARE! The prolific driver appearently fails when connecting to some printers, among them are Minolta 6e/6ex and HP DeskJet 500. The printer is identified but no print data ever gets through, usblp_write ends up in a timeout. usb-devel wasn't helpful either. If you plan to connect older printers (assuming that is the cause), make sure you've a return agreement with your dealer. [/FONT]*
[/INDENT]

---

### Post by colourfullegume on 2010-03-23
I've managed to print !!!!  This thread helped a lot: [http://ubuntuforums.org/showthread.php?t=126135](http://ubuntuforums.org/showthread.php?t=126135)

UNFORTUNATELY, the only way to print so far is something like

**echo Printing > /dev/usb/lp0**

and not through applications.  I'm getting there ...

The problem is that the ownership of /dev/usb/lp0 does not match the CUPS configuration.

**~$ ls -l /dev/usb/lp0**
crw-rw---- 1 root **lp** 180, 0 2010-03-23 21:39 /dev/usb/lp0

Notice the **lp** group?  When I checked group properties, this group did not have any members - not even root!!!  *[SIZE=2]Not sure if this is an Ubuntu installation issue or not (I have a fairly clean installation of 9.10 Karmic Koala[/SIZE].*

The default for CUPS (from the CUPS doc) is **lpadmin**, in any case, so not sure what **lp** is all about.  In fact, the lp group has ID=0, the same as the group root.  I think I will write a separate thread for this so that other new users won't be adversely affected.

I fixed it by doing this:

[B]~$ sudo chown root:lpadmin /dev/usb/lp0
[/B]
(In fact, I went further and did this for lp0, lp1, parport0 and parpart1 as well - I have two parallel ports in my setup.)

I think the printer URI is wrong.  I've changed it to** usb:/dev/usb/lp0** but it's still not working.  I must be close, surely!

---

### Post by unregistered-user on 2010-03-23
Download a driver online and use wine to run it, that's what I did for my HP laserjet 4000.

---

### Post by colourfullegume on 2010-03-24
Thanks for the suggestion unregistered-user, but that sounds like defeat to me.  Here's something new - sudo lsusb produces a different result:

~$ sudo lsusb
**Bus 001 Device 009: ID 1a86:7584 Unknown **
Bus 001 Device 008: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 007: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 006: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 004: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100
Bus 001 Device 003: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

That first line - "Unknown" is not there when I don't use 'sudo'.  It is the printer (it disappears when I unplug the printer's USB cable).  So this is sounding more and more like a problem with permissions - why can root see the device but not my user?

Incidentally, when I rebooted, all the lp devices (/dev/lp0, /dev/parport0, /dev/usb/lp0) had their group changed back to **lp** again after I changed them to **lpadmin** (see earlier post).  Why is this?

---

### Post by colourfullegume on 2010-03-24
I don't have to reboot - just unplug the USB cable and plug it back in and it is reset to be in the group **lp**.

---

### Post by colourfullegume on 2010-03-24
It's SOLVED.

The only problem was the URI.  Nothing else matters - permissions, nothing.

This thread held the solution but it took me ages to find it: [http://ubuntuforums.org/showthread.php?t=894223&page=2](http://ubuntuforums.org/showthread.php?t=894223&page=2)

The solution is that the URI is  [B]parallel:/dev/usblp0
[/B]
*Now I just have to figure out how to mark this thread as solved ....*

---

