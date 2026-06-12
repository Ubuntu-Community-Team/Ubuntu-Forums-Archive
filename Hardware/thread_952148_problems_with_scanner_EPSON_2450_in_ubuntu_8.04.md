---
title: "problems with scanner EPSON 2450 in ubuntu 8.04"
date: 2008-10-18
forum: Hardware
---

### Post by xxxpse on 2008-10-18
Hi,

I'm pretty new with Ubuntu, but so far everything worked fine. 
Except my scanner EPSON2450 does not work.
I run Ubuntu 8.04 on a Intel 2Ghz, 2GB Ram plenty of HDD. The scanner is connect with USB through a USB 4port hub and works fine and fast when using Windows on same hardware.

I searched a lot during last 3 weeks (and followed about 20 hints), but none worked - or I did not follow them correctly.

When I start SANE, it takes about 5-7 minutes and then following message appears:
"Konnte Scanner nicht starten Fehler während Geräte I/O"

What's wrong. Thanks for any help.

---

### Post by cariboo on 2008-10-18
Run the following command in a termihnal:

```
sane-find-scanner
```

This should detect your scanner properly.

Jim

---

### Post by xxxpse on 2008-10-19
Hi

thanks for quick reply.

running "sane-find-scanner" shows:

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0112 [EPSON Scanner]) at libusb:005:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
  # Not checking for parallel port scanners.

So, I would say the scanner is somehow identified ?
(What I do not understand is:  yesterday the scanner was not at 005:005, but at 005:009 though I have not unplugged it or changed anything else - is that important?)

What could I check next? Any other information I should provide?

BTW: As you can see I'm really new here. How can I format the posts like you did?

---

### Post by xxxpse on 2008-10-21
Hi

nobody out there having more experience with Ubuntu and Epson scanners or having ideas, what I should try?

Thanks for any help

---

### Post by teaker1s on 2008-10-21
[http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)[http://avasys.jp/hp/menu000000500/hpg000000442.htm]("http://avasys.jp/hp/menu000000500/hpg000000442.htm")

if you can't find a deb file then a "rpm" can be converted to "deb" with use of "alien"

[HTML]sudo apt-get install alien[/HTML]

[http://ubuntuforums.org/showpost.php?p=570250&postcount=7]("http://ubuntuforums.org/showpost.php?p=570250&postcount=7") gives a brief descripton.

If you can't get sane to work then
```
lsusb
``` you should see the scanner listed and the info required to configure sane.

---

### Post by redwing81 on 2008-10-22
I'm hoping this thread will lead to an answer to a similar problem I am having.

Epson 3490 scanner that will only work in Ubuntu 8.04 from the command line as sudo.

the command 'xsane' results in "segmentation fault" while 'sudo xsane' starts the scanner normally (after a dire warning).

I can only assume that I have the driver correctly installed and configured, but have a permission problem of some kind.

Can anyone shed some more light on this?  I have been struggling with it ever since I upgraded to 8.04 - it worked fine in 7.04 and 7.10.

thanks,

---

### Post by teaker1s on 2008-10-24
[http://ubuntuforums.org/archive/index.php/t-166944.html]("http://ubuntuforums.org/archive/index.php/t-166944.html")

user@somelinuxbox:~$ lsusb
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


as you can see the scanner resides on Bus 002 as the second (002) device in my case. The syntax for changing permissions of the scanner device is


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE


remember to change the $BUS and $DEVICE variables according to the lsusb output as described above. to change permissions to my scanner device i would enter:


user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002

---

### Post by xxxpse on 2008-10-24
the lsusb shows for me:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 04b8:0112 Seiko Epson Corp. Perfection 2450
Bus 001 Device 004: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USBTetraHub"
Bus 001 Device 001: ID 0000:0000

and the ls lisa on /dev/bus/usb/001 shows:

 5853 0 drwxr-xr-x  2 root root       100 2008-10-24 22:12 .
 5852 0 drwxr-xr-x  8 root root       180 2008-10-24 21:25 ..
 5854 0 crw-rw-r--  1 root root    189, 0 2008-10-24 23:25 001
 6151 0 crw-rw-r--  1 root root    189, 3 2008-10-24 23:25 004
22211 0 crw-rw-r--+ 1 root scanner 189, 5 2008-10-24 21:34 006

now I ran "sudo chmod a+w /dev/bus/usb/001/006"  and this results in:

 5853 0 drwxr-xr-x  2 root root       100 2008-10-24 22:12 .
 5852 0 drwxr-xr-x  8 root root       180 2008-10-24 21:25 ..
 5854 0 crw-rw-r--  1 root root    189, 0 2008-10-24 23:25 001
 6151 0 crw-rw-r--  1 root root    189, 3 2008-10-24 23:25 004
22211 0 crw-rw-rw-+ 1 root scanner 189, 5 2008-10-24 21:34 006

I installed the driver from this site [http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm) already earlier, but still the scanner does not work.


the result of the lsusb if above

sane-find-scanner shows:
  ...
  # you have loaded a kernel SCSI driver for your SCSI adapter.
found USB scanner (vendor=0x04b8 [EPSON], product=0x0112 [EPSON Scanner]) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
  ...

but when entering the command "scanimage -L" it takes again some 5 minutes for a system response:
and the answer is:
device `epkowa:libusb:001:006' is a Epson Perfection 2450 flatbed scanner

which seems to be o.k. for me

But why does it last some 5 minutes to get this system response and sane takes also 5 minutes and then it doesn't work.

Anything I could analyse?
Should I uninstall sane and install again?
Should I remove more packages or.. from system to be able to "restart" somehow again?

---

### Post by teaker1s on 2008-10-24
have you tried 
```
iscan
```

---

### Post by xxxpse on 2008-10-24
I started 
iscan 
from konsole. It took about 2-3 minutes to open it, then I pressed the button scan and it took again 1-2 minutes and then it throws "Es konnte kein Befehlt an den Scanner gesendet werden. Überprüfen Sie den Scanner-Status." Translation: "It was not possible to send a command to the scanner. Check the scanner status."
So, it looks like with SANE (long, long waiting and then some strange error)

---

### Post by teaker1s on 2008-10-24
try```
 gksudo
``` not```
 sudo
``` as it's a graphical interface app, then this will rule out permission error

---

### Post by xxxpse on 2008-10-25
I used gksudo and started
gksudo iscan
from konsole. It took about 2-3 minutes to open it, then I pressed the button scan and it took again 1-2 minutes and then it throws "Es konnte kein Befehlt an den Scanner gesendet werden. Überprüfen Sie den Scanner-Status." Translation: "It was not possible to send a command to the scanner. Check the scanner status."

Then I tried
gksudo sane, but this did not work at all (to be more correct: nothing happend)

Was this what you meant, when saying I should use gksudo ?

---

### Post by teaker1s on 2008-10-25
yes, I'm out of idea's on this one and google doesn't seem to come up with anything. 
Would suggest very politely contacting developers outline steps so far:-avasys [contact]("https://www.avasys.jp/secure/english/linux_e/support_form.html")

---

### Post by michiedo on 2008-11-07
I join the list of sad users.
:-(
I'm experiencing the same problems ... it's (almost) impossible for me to use the 2450 with ubuntu ...
I've found this link ... it dates back to 2007
[https://lists.ubuntu.com/archives/ubuntu-users/2007-April/110987.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-April/110987.html)

i'm trying to contact avasys (as suggested by teaker1s), but it looks like they're having troubles with SMTP .

---

### Post by xxxpse on 2008-11-09
Meanwhile I updated the system to release 8.10 - but the scanner still doesn' work.

@michiedo: if you find any solution: please post it here. I'm more than interested (in fact, I'm considering to move either to any other distribution or even back to windows - because month with scanner is no fun :(  )

---

### Post by michiedo on 2008-11-10
@xxxpse:
may i suggest that you too post a request to avasys (address in teaker1s post).
honestly, i'm not too optimistic, but the more people complains/asks , the more hope that they develop a driver for ubuntu.

---

### Post by xxxpse on 2008-11-28
Hi Michiedo,

I'm sorry, but I guess I'll not contact avasys anymore.
I have now spent many many hours and beside the scanner I have also problems with connecting to my network drive and the printer allows printing also only in best mode (but not in draft mode) ....
For testing I installed a new machine, this time using OpenSuse and - surprise, surprise - everything (scanner, printer, network drive, etc) works immediately.
So, my final solution here is: I'll use OpenSuse in future

---

### Post by michiedo on 2008-11-29
> 
For testing I installed a new machine, this time using OpenSuse and - surprise, surprise - everything (scanner, printer, network drive, etc) works immediately.

Worth to give it a try, at least to the "live" cd.
Thank you
:)

---

