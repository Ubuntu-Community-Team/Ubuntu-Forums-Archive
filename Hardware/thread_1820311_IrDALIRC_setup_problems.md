---
title: "IrDA/LIRC setup problems"
date: 2011-08-07
forum: Hardware
---

### Post by erittaf on 2011-08-07
Hello,

I hope someone out there can assist me with the last peice of th puzzle on my HTPC setup.  I've been banging my head against this one for a couple weeks now and I've finally given up...  As much as I hate to go there... I need help!!!!

I am trying to get my IR receiver working with myth TV on a toshiba P105 laptop.  Forget the Myth TV part for now, I've been stuck trying to get ubuntu to even see the hardware.

Tech stuff:
-USB receiver does work (I can power the laptop on with my remote)
-BIOS on this system had NO information or options for IR
-Toshiba driver website (only has windows drivers) states this is a CIR (SMSC) device.
-running Mythbuntu 11.04 (natty)
-Toshiba onboard IR receivers appear to give a lot of people angst but I've "been there, done that" on every Toshiba specific setup guide that I can find.
-I have found this page which appears to tell me what interrupt and I/O addresses I need to use for this hardware so I figure this shouldn't be that hard... (see the line in the chart for Satellite P10): [http://irda.sourceforge.net/smcinit/#description](http://irda.sourceforge.net/smcinit/#description)

I have attempted just about every IrDA and LIRC setup tutorial I can find and it appears that they system can see the hardware but I can't get it working.

Here's some relevant dmesg entries:
relevant log entries...

> [   15.757803] irda_init()
[   15.757819] NET: Registered protocol family 23
[   15.790859] IrCOMM protocol (Dag Brattli)
[   16.558045]  Overriding FIR address 0x06f8
[   16.558047]  Overriding SIR address 0x03f8
[   16.558065] smsc_ircc_present(), addr 0x06f8 - no device found!

and the results of trying to stop/start the IrDA service...
> erittaf@Neversummer-FE:~$ sudo /etc/init.d/irda-utils stop
 * Stopping IrDA service irattach                                        [ OK ]
erittaf@Neversummer-FE:~$ sudo /etc/init.d/irda-utils start
 * Starting IrDA service irattach                                               Invalid module name [0x500] !
Usage: irattach <dev> [-d dongle] [-s] [-b] [-v] [-h]
       <dev> is tty name, device name or module name
Dongles supported :
        esi
        tekram
        actisys
        actisys+
        girbil
        litelink
        airport
        old_belkin
        ep7211
        mcp2120
        act200l
        ma600
        toim3232

When I have tried to set this up with LIRC instead of IrDA (not sure of the difference really) the install seems to go alright but when I go to test the low level setup and run IRW it just says "No such file or directory."  I believe this is referring to the device (something like /dev/lirc0) as it does not appear anywhere in my /dev folder.

That's about all I have that seems useful right now, if you need more info to help diagnose what's going on here let me know what commands to run and i'll reply with output.

---

### Post by erittaf on 2011-08-08
bump?!

the search continues...  no progress since my last post.

---

### Post by erittaf on 2011-08-10
scratch the bit about the p10 in the OP...  it appears this is for an actual "P10" model, not a "P10x" model...

learning more than i ever wanted to about laptop hardware,
~E

---

### Post by erittaf on 2011-08-10
I dug an older version of irda-utils up from the linux packages site that included smcinit.  I ran
> sudo scminit -v
and i got
> smcinit 0.5cvs

SIR ioport: 0x3f8
FIR ioport: 0x130
FIR interrupt: 3
FIR DMA: 3

Detected IO hub vendor id: 0x8086
smcinit IO hub device 27b9 not 82801CAM (0x248c or 0x24cc)


This makes me think that linux is able to see this hardware at least in some respect, however the smcinit utility will be of no use to me.  Using modprobe I have determined that SIR ioport 0x3f8 appears to be ttyS0 on my system.

Anyone know how to get LIRC to just talk to that port?

Still confused,
~E

---

### Post by erittaf on 2011-08-14
I've given up for now as other concerns have become more important for the time being.  I may yet return to this idea so if anyone figures out the magic to make the built in SMSC CIR port on the P105 toshiba series play nice with mythbuntu, please post it (or a link to info) here.

Thanks
~E

---

