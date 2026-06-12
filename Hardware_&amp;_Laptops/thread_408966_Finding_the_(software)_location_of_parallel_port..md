---
title: "Finding the (software) location of parallel port."
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by wikityler on 2007-04-14
I'm trying to use the avrdude software, and to do so I need to give it the location of my parallel port. Some people in irc suggested i try, /dev/parport0, but that didn't work. I looked around in /dev and found nothing that would logically be the parallel port. How do i find the location of my p. port?

---

### Post by amohanty on 2007-04-14
try /dev/lp0

thats L in lower case

HTH
AM

---

### Post by wikityler on 2007-04-14
No luck....
"
avrdude: can't open device "/dev/lp0": No such file or directory
avrdude: failed to open parallel port "/dev/lp0"
"

There is also no file named lp0, in /dev.

---

### Post by amohanty on 2007-04-15
IN System->Administration->Device Manager see if you can find an entry that says ECP printer port.

Also post the output of:

ls /dev/lp*

and of

lsmod | grep lp

AM

---

### Post by xeocub on 2007-04-17
lp                     16584  0 
parport                49932  3 ppdev,lp,parport_pc


I am having the same problems as described.. here is my grep info, and there is only lp0 on my pc.

I've attempted to use parport_pc, ppdev,lp etc basically anything I could find that is in connection with lp0.

Could it be that the port is somehow reserved for the printer which I usually have connected there? 

Also, this is the output I get from avrdude when I run it...

Using Port            : /dev/lp0
         Using Programmer      : sp12
avrdude: can't claim device "/dev/lp0": Invalid argument

---

### Post by amohanty on 2007-04-18
Check to see is some app is using the device via:

**lsof | grep dev | grep lp**

Then try killing that process, using System->ADministration->Sysm Monitor.
Actually post back the output before doing that. I woudnt want you to crash your session :)

Also this is an extreme solution if everything else fails, but take a look here. Try not to do it without trying what I suggested above.
[http://www.linuxforums.org/forum/peripherals-hardware/15108-trouble-getting-direct-access-parallel-port.html](http://www.linuxforums.org/forum/peripherals-hardware/15108-trouble-getting-direct-access-parallel-port.html)

HTH
AM

---

### Post by SMPS on 2007-04-18
doing
** lsof | grep dev | grep lp **

does not return anything actually.. 
It must be me doing something wrong, because it hasn't worked on 2 computers now.

AVRdude was apparently installed by only doing ./configure .. I coulnd't do make or install. Is this normal?

---

### Post by amohanty on 2007-04-18
Nope. ./configure simply configures the Makefile. You _have_ to do a make to build the app and make install or something else to install it.

AM

---

### Post by SMPS on 2007-04-18
why can I run avrdude after just ./configure then? (not in the same directory as it either)

---

### Post by amohanty on 2007-04-19
It probably means that you have previosuly installed it or something to that effect, try the following and post the output:

sudo locate -u
locate avrdude

AM

---

### Post by xeocub on 2007-04-19
Ok, well that was on another computer.. on my home PC I could install it no problem and it seems to be working. But I still can't connect to my programmer with AVRdude, it's as if it didn't find the lp0 port .. I honestly don't know why. 

I even made a second programmer to see if I messed up somehow, but it is seriously an incredibly simple circuit of resistors and capacitors.. and I'm an ECE.

Any other suggestions?

Here once more for reference.. I reconfigured and reinstalled avrdude to start with a clean slate. 
First error:
[I]         Using Port            : /dev/parport0
         Using Programmer      : sp12
avrdude: can't open device "/dev/parport0": No such file or directory
avrdude: failed to open parallel port "/dev/parport0"[/I]

Which is to be expected because my parallel port is on lp0 not parport0.. change the "/usr/local/etc/avrdude.conf" to use lp0 instead of parport0 and this is what I get:
[I]         Using Port            : /dev/lp0
         Using Programmer      : sp12
avrdude: can't open device "/dev/lp0": Permission denied
avrdude: failed to open parallel port "/dev/lp0"[/I]

do sudo instead because maybe it's just a permission problem and I get this:

[I]         Using Port            : /dev/lp0
         Using Programmer      : sp12
avrdude: can't claim device "/dev/lp0": Invalid argument[/I]


So what now?

---

### Post by amohanty on 2007-04-20
Can you make sure that /dev/lp0 is an actual file instead of a link:

ls -al /dev/lp0

Also did you try using the solution I provided in the link previously.

AM

---

