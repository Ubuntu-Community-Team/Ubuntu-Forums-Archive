---
title: "smaclmgr/mosmig on port 4660: anyone?"
date: 2009-08-22
forum: Hardware
---

### Post by tbj61898 on 2009-08-22
Hello Everybody,
it has been a while I'm using various Ubuntu flav by now, to complete my transition to Windows I'd like to make a little piece of hardware work.

This piece of. .. hardware ... is a 50$ Digicom Usb Server model 8e4440, long story short: it's a tiny box which connect to network and to usb devices. By a small piece of software it lets a windows box to act as remote usb devices were connected directly to the winbox (when, in fact, they are connected to this tiny box). More than over, it lets remote usb devices to be shared between various PCs.

What's really curious about this digicom 8e4440 unit is the fact it (seems to) share the usb port directly, not the device or the printer queues, neither samba. On the Windows box I got a Network Usb Server virtual device (with drivers apparently from Microsoft), which contains a network usb hub with all connected usb devices. That means devices access can't be concurrent, but still usefull to me.

Here are my tests result.

I NMAPed it (nmap -sS -O -p 1-65535), which results in:
- port 80 (tiny emb web server for minimal configuration)
- port 515
- port 4660

OS scan gives 88% accuracy on a Minix v3.x, but I don't know what's really in there.

I did some tests on port 515 for printer sharing but I didn't came up with good results: configuring an lpd printer on such port didn't get any luck with various printer drivers available to my system (hpjis, pcl3 and foomatics), with the printer being an old deskjet 845c. On most cases it took a sheet and then stop, once some garbage came out shortly.

I rebooted to Windows, pinned an usb key to that tiny box (unit 8e4440, to be clear), started digicom software and sniffed traffic. All communications seems to flow by port 4660.

I did some search, this port seems to be called smaclmgr by IANA, or "mosmig" by nmap.

I tried again to search for more but I was unable to find information about mosmig or smaclmgr.

That bring me to why I'm writing a post here: do anyone knows more about this port 4660? Do you think mosmig/smaclmgr have anything to do with the purpose of this tiny box (or they just picked up a random port for their custom services)?

If anyone else knows a way to get this box working with linux, any hint will be more than welcome.

Other things I tried:
- various packages from [www.incentivespro.com](www.incentivespro.com), not working with that box
- user manual say it is only compatible with Windows, obviously

Thank you, any case! :confused:

---

### Post by tbj61898 on 2009-08-24
tiny steps here.

I was able to do some small print out, simple pages, mostly text.

Ubuntu Print test page hang the printer, but simple text seems to come out,,, a bit slowly!

Any suggestions?

Thank you

---

### Post by dabubu on 2009-09-29
That's interesting. I have a Conceptronic CHDDLANU with exactly the same ports open. They must be very similar devices.  

PORT     STATE SERVICE
80/tcp   open  http
515/tcp  open  printer
4660/tcp open  mosmig

And my CHDDLANU, by the look of the box, is identical to the Addonics NASU2. 

My CHDDLANU however is not Linux compatible. So I tried to download the firmware from Addonics, which, apparently, is Linux compatible, but I needed an Addonics serial number. 

I would be quite happy to sacrifice my CHDDLANU by trying to install the Addonics firmware, but I can't find it anywhere. Anyone?

Daniel

---

### Post by tbj61898 on 2009-10-11
Hello,
I did a side step (unfortunately any forward step). Following similitudes I tried other firmwares I found on the net but none worked nor bricked my little piece of hardware.

I took a screw driver and opened the can, here's what I found inside:
- chip EST e1868m4

Which apparently take US to [http://www.display-solution.com/en/products/chips/elite_silicon_E1868M4.html](http://www.display-solution.com/en/products/chips/elite_silicon_E1868M4.html)

Quoting from "features" section:
- Supports LPD/LPR printing on Windows, LINUX and Mac OS

That confirm it's a firmware problem.. I'm trying, right now, an update with some other firmware online, such as 
[http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1101&SUBMIT=Go](http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1101&SUBMIT=Go)

... I'll post news here, if any! ;-)

Cheers,
Andrè :guitar:

---

### Post by tbj61898 on 2009-10-11
There,
just a follow up with a list of product which (should) use/implement chip e1868m4. 

For the record: this DOESN'T MEAN firmware is interchangeable. Use only official firmware from your hardware supplier.

Grand iUSB Hub
EXSYS EX-6000
TE100-MP2U
GUIP201
GMFPSU22W6  (?????)

I tried to upload every firmware I found... but none of them seems to even BRICK that little device. This is what I did:
- opened device homepage
- Firmware updates
- upload firmware (which post to ul.cgi)
- digicom LAN led started to blink furiously
- after a while I turned it off and on
- the new firmware has no effect on it

I don't know why this isn't working but here are some thinkinh about it:
- actual firmware version is like 100.065 (which is very high... ), if it compares to other firmwares I tried (which are like 2.80, 3.5) it may deny a downgrade.... 

- serial checking? (unlikely..)

- jsut wrong firmware?

Bye,
Andrè :(

---

### Post by David Mulligan on 2009-12-16
Did you ever get anywhere with this?  I have a unit with the same chip in it from MonoPrice which is made by WS-Tech and private labeled.

I can print to my printer from my Mac using LPR and Gutenprint but not from my Linux box.  I wouldn't mind using the networked USB feature too.

Thanks,
David

---

