---
title: "Scanner does not work"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by kwgarner on 2007-04-12
Xsane is installed but my Mustek Bearpaw 2400CU Plus Scanner is not recognised, Xsane generates a message with reads:- "failed to open devise 'gt68xx.libsub'001:005" "invalid argument"

Help please! Many thanks

---

### Post by bananabob on 2007-04-13
please post the output of lsusb command

---

### Post by kwgarner on 2007-04-13
> **bananabob said:**
> please post the output of lsusb command
Sorry - as a somewhat inexperienced Linux user I dont understand the question
(many thanks for taking the trouble to reply).

Regards

---

### Post by bananabob on 2007-04-13
That's OK.

Open a terminal Applications>Accessories>Terminal 
type lsusb
and then copy and paste the result into a post here.

---

### Post by kwgarner on 2007-04-14
The details are:-

Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 055f:021d Mustek Systems, Inc. BearPaw 2400 CU Plus
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Many thanks.

---

### Post by bananabob on 2007-04-14
That tells us that the scanner is recognised.

Can you do the following
go to Applications>Graphics>GIMP>File>Acquire>Xsane

Under this there should be two options.
Device dialog
and another one.

Please select both, one at a time, and post the results for each one..

---

### Post by kwgarner on 2007-04-15
Hi

The messages are:-

failed to open device "gt68xx:libsub:001:003":Invalid argument

and

failed to open device "gt68xx:libsub:001:006":Invalid argument

Hope this helps!

---

### Post by dompie on 2007-04-15
Although I have another scanner (N670U) that is recognised, the scanner does not start and gives a black image
I tried to ad an attachment with lsusb output

---

### Post by bananabob on 2007-04-15
please type the following on a terminal  and copy and paste the result
sudo cat /etc/sane.d/gt68xx.conf

---

### Post by bourger on 2007-04-15
I have exactly the same problem with this very scanner (Mustek 2400CU Plus) under Ubuntu 6.06.
When I do ```
xsane
``` there is an error: ```
failed to open devise 'gt68xx.libsub'001:012' invalid argument
```
Output of ```
lsusb
``` is the same as **kwgarner** reported.
In gt68xx.conf the lines related to BearPaw 2400 look like this: ```
# Autodetect Mustek BearPaw 2400 CU Plus
usb 0x055f 0x021d

```

When I command ```
xsane
``` for the second time and all next times in the course of one session, the answer is "no devices available".

---

### Post by bananabob on 2007-04-15
Well I have had a look around the Internet and only come up with the one link 
[http://lists.alioth.debian.org/pipermail/sane-devel/2005-October/014952.html](http://lists.alioth.debian.org/pipermail/sane-devel/2005-October/014952.html)
Which does describe your problem.

I am afraid that it doesn't look good for getting an answer to it.

One last thing. I had a problem related to USB devices that was was solved by doing a reboot of the system.
What I did was switch on the PC, start up the OS and then just do an immediate reboot. This got rid of my problem. You maybe could try that out. It was annoying having to do that each time I switched on my computer though.

---

### Post by kwgarner on 2007-04-16
Much as I love Ubuntu occasionally there are problems which take some sorting - scanners in particular. I have tried the quick reboot but with no success. Perhaps 7.04 may be able to help!

Many thanks for trying!

---

### Post by bourger on 2007-04-16
**bananabob**
Many thanks for the link, it gave me one more way to move into.
Yet I can't resolve the problem by now... Everything is in its place, scanner doesn't work.

---

### Post by bananabob on 2007-04-16
Maybe Feisty will help. This is not a problem restricted to Ubuntu, it is across all Linux distos.

When purchasing new equipment it pays to do your research to find out if there is support for it. I realise that that is of no use to people who are converting from Windows and already have every thing they need. What is worse than scanners is dial-up modems. 

Open up your driver source people! Support Linux, the tide is changing out there.

---

### Post by ramjet_1953 on 2007-04-17
This link may shed some light:

[http://www.meier-geinitz.de/sane/misc/mustek-scanners.html](http://www.meier-geinitz.de/sane/misc/mustek-scanners.html)

Regards,
Roger :)

---

### Post by ColJep on 2007-04-18
Hi All,

I am just getting into Ubuntu and loving every moment. Bye, Bye Bill!

I have the same problem with an Agfa Snapscan 1212U. I have read that this model should work "out of the box" but it gives the same error in Dapper, Edgy and Feisty.

I've got my Epson Acculaser C900 printer going so surely there must be a way?

Colin

---

### Post by fsando on 2007-04-21
I too have this problem with agfa 1212u. It worked perfectly under edgy - it doesn't work under feisty. I guess a bug report is perhaps appropriate - just don't know how to do that.

---

### Post by glennric on 2007-04-22
I have the same problem with an Epson Perfection 1670 when running the 2.6.20-15-generic kernel.  When I run a kernel that I compiled myself the scanner works fine.  So it seems that you will need to either compile your own kernel, or wait until the Ubuntu developers find and fix the bug, and release a new kernel.

---

### Post by dompie on 2008-02-06
Since installing Ubuntu 7.10 everything works miraculously well without any further intervention of me.

---

