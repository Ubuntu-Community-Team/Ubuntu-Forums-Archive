---
title: "USB Modem Installation in Ubuntu 5.10 Baddger - nnnghh"
date: 2005-11-28
forum: General Help
---

### Post by ironheart on 2005-11-28
Howdy all,

I have recently completed an unanticipated marathon in installing this Ubuntu thing.  After overcoming seemingly-incredible resistance by Ubuntu - i shan't regale the whole epic unless requested - I have finally managed to get it working.  "Working" being an operational phrase here.

I have a USB Modem.  It is a Swann Smartlink v.90 Modem. Buntu won't recognise it using the popular command

$ sudo pppconfig

since this program only examines serial ports.  Looking in /dev, there is no such thing as /dev/usb or /dev/modem.  (I don't have kppp or gppp or any other prefixed ppp command, it seems)

I have also looked in the Network bit in the Ubuntu menu.  I have set up my provider's connection details and I have enabled the Modem Connection and set it to be the default method of getting to the net.  The Modem is in fact being recognised in the Device Manager in Ubuntu so both It and I know that it exists.

At some point or other i get a "ppp0 not configured" error.

Examining my winboze device manager, it declares my modem is a Swann Communications Swann ST56 USB Modem, with this information:

Field:  Hardware ID
Value: USB\Vid_0483&Pid_7554&Rev_0200

(presumably version id, product id and revision number)

Advanced port settings state that the COM port number is actually COM3, even though i know it's in the USB hole.  At least, one of two usb holes: my keyboard is in the other (ubuntu recognises my keyboard, obviously...)

pppconfig cannot autodetect my modem (cos it's on a usb)

** I am not on a network.  i have no broadband, which is why i'm on dialup.  it is not an adsl modem.  

How do i make this modem work in Ubuntu 5.10 badger?  I have extensively scrounged the web and have found little nuggets of maybe-useful stuff.  For example, i have heard of this symlinking stuff: each are obviously separate individual commands taken from one source or another

$ ln -s /dev/ttyUSB /dev/modem
$ ln -s /dev/ttyACM0 /dev/modem
$ modprobe
$ lsmod
$ insmod acm
$ mknod something-something-something 166 0

I have read somewhere that something called Acmos1-acmos4 is used to make USB Modems work.  futher grooglage reveals nothing about Acmos-1 or anything relevant to a linux.

additionally i have heard of this scanModem thing from linmodems.org and have yet to try it: i am dual booting with Winboze and it's a tremendous hassle to move files around (no fdd).  At this stage it seems nobody has deciphered it to any meaningful extent.


And that is the extent of what i've been able to find.  Fitterman seems to experience a similar malady... if you more experienced people can suggest some kind of matrix-like workaround please help  Rebooting into windows and back into ubuntu and re-dialling up is really painful.  It is seriously uncool.


it's a long post but it's also a partial excretion of much-accumulated frustration - it is only the tip of the iceberg.  thanks muchly for time (and probably patience)

---

### Post by Original Brownster on 2005-11-28
Hi there,

Ive had a look for you and I'm afraid I can't find anyone who has had success with this modem, if I had I would have gone through it with you.

FWIW I would buy an external serial modem which just work with no messing around.

Good luck.

---

