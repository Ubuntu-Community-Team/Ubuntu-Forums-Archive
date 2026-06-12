---
title: "Samsung SCX-4521F"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by xbaez on 2006-06-19
Hello
I'm trying to install the Samsung SCX-4521F printer. I installed the ./install.sh script from the Samsung Driver CD, and when I try to print (in /dev/usblp0) I receive the following error.

```
# lsusb
Bus 001 Device 003: ID 04e8:3419 Samsung Electronics Co., Ltd
```


```

Jun 19 11:14:48 caronte kernel: lp0: using parport0 (interrupt-driven).
Jun 19 11:14:56 caronte rmmod: ERROR: Module mfpportprobe does not exist in /proc/modules
Jun 19 11:14:56 caronte rmmod: ERROR: Removing 'mfpport': Device or resource busy
Jun 19 11:14:56 caronte rmmod: ERROR: Module ppdev does not exist in /proc/modules
Jun 19 11:14:57 caronte rmmod: ERROR: Module parport is in use by mfpport
Jun 19 11:14:57 caronte kernel: parport 0x378 (WARNING): CTR: wrote 0x0c, read 0xff
Jun 19 11:14:57 caronte kernel: parport 0x378 (WARNING): DATA: wrote 0xaa, read 0xff
Jun 19 11:14:57 caronte kernel: parport 0x378: You gave this address, but there is probably no parallel port there!
Jun 19 11:14:57 caronte kernel: parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 19 11:14:57 caronte kernel: lp0: using parport0 (interrupt-driven).
Jun 19 11:14:57 caronte kernel: mfpport: no version magic, tainting kernel.
Jun 19 11:14:57 caronte kernel: mfpport: module not supported by Novell, setting U taint flag.
Jun 19 11:14:57 caronte hp: unable to open /var/run/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 84
Jun 19 11:14:57 caronte hp: unable to connect hpiod socket 50000: Connection refused: prnt/hpijs/hplip_api.c 703
Jun 19 11:14:57 caronte hp: unable to send ProbeDevices: Broken pipe

```

If I use the Samsung MFP Configurator, all I get is success messages, but the printer doesn't prints

---

### Post by xbaez on 2006-06-19
Ok I was able to install this printer and I can print locally
However, when I try to print from a Windows computer, I am unable to do that, since this is the Samba browser and I need to share this printer

I'll appreciate any help

These are the errors that I get at samba

[2006/06/19 14:04:54, 0] lib/username.c:map_username(179)
  Unable to build user list
[2006/06/19 14:04:54, 0] smbd/service.c:make_connection(853)
  station-03 (192.168.0.113) couldn't find service y2test
[2006/06/19 14:04:54, 0] lib/username.c:map_username(179)
  Unable to build user list
[2006/06/19 14:04:54, 0] smbd/service.c:make_connection(853)
  station-03 (192.168.0.113) couldn't find service y2test

---

### Post by em3raldxiii on 2006-09-04
You say you successfully got the printer installed (the precise one I am having difficulty with) - how did you do it?  I have installed other printers before, and never had any troubles.

So, I have the printer plugged in via USB.  I have tried the install script on the disc (install.sh) -- this gave me a number of small errors, such as CUPS not being installed and SANE not being installed, both of which ARE actually installed.

I also tried using the first drivers suggested by the Linux add-printer process, again to no avail.

So, what do I need to do to make this printer work?????

Thanks for your input!

---

### Post by em3raldxiii on 2006-09-06
I recently found a tutorial regarding how to install the Samsung SCX-4521F printer.  Here is the website link where I found it:

[http://www.elijahlofgren.com/linux/ubuntu/](http://www.elijahlofgren.com/linux/ubuntu/)

I tried this method today.  It works.  There are some notable differences, however, between the updated driver and the driver mentioned in that article.  Specifically, it now uses a GUI for the installation, very reminiscent of a WindowsCrazything(tm).  You still have to follow all of the instructions in the article, though ... 

:D

*EDIT:  I was unsuccessful with the scanner using this method*

---

### Post by samurai1200 on 2007-06-05
Just a little update for those of you who are searching to find instructions for these printers (like you should): 

I'm running Ubuntu 6.10, and downloaded the latest drivers from Samsung (20070425140106937_UnifiedLinuxDriver), and went through the first 5 steps on the site em3raldxiii suggested. Then a windows-like install prompt shows up and runs you through the process.

Thus far, i only have a basic local printer function, no scanner, and no network. That'll come next.

[edit] Scanner works through XSane!

---

### Post by roxy99 on 2007-10-10
I'd hardly call that a success : (
 what use is a multifuntion printer if scanning doesn't work??

I don't get it.  The samsumg litterature says Linux is supported.  The manual list a bunch of distributions including Fedora and Red Hat (albeit not Ubuntu).   How difficult should it be Linux is still Linux.

Has anyone contacting Samsung about this?

---

### Post by em3raldxiii on 2007-10-10
Hi Roxy,

Just a note - this is a rather old thread, so depending on which version of Ubuntu you have operating, things may be vastly different.

Also, Samurai added an edit to the end of his post saying that XSane does allow him to scan with this process.

When I had installed this printer for my dad's computer, it was a year ago - and I think he was using Dapper.  Possibly even Breezy ... it's been that long ;)

I have contacted Samsung about it, and they were rather unhelpful.  The essence of the phonecall was 1) I couldn't barely understand the helpdesk person (rediculously strong accent), 2) "Did you read the manual?" was one of the common responses, 3) The helpdesk person was extremely linux-illiterate.  So I sent an email ... long since deleted ... but the gist of the message was that Samsung has no apparent policy regarding supporting "fringe" operating systems.  I should point out, though, that since this was a year ago, their policy has most likely changed.  I encourage you to contact them and let us know if you are successful.

As far as my father's printer goes, I haven't asked him in awhile, but I do know he uses it for printing & faxing.  I'll ask him if he ever got scanning to work.

Good luck!  I hope you have some success.

---

### Post by roxy99 on 2007-10-12
Thanks for the reply.  I'm hoping for the best and I assume Ubuntu is no longer considered fringe by Samsung so hopefully the latest unified driver will work.

---

