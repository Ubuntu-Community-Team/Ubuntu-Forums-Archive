---
title: "Problem with parallel HP printer in edgy eft 64, maybe A BUG"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by TADsince1995 on 2006-12-10
Hi guys, I retry posting this strange problem, I'm starting to think it maybe a bug in edgy eft 64, so I must be sure of it before.

The problem: I have a parallel printer HP840C and I've just installer Ubuntu Edgy Eft AMD64. This printed always worked perfectly since Slackware9, linuxprinting tells it as "Work Perfectly".

After launching ubuntu, If i launch dmesg | grep parport it says:

[FONT="Comic Sans MS"][   32.253247] parport: PnPBIOS parport detected.
[   32.253292] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   32.297847] parport0: Printer, HEWLETT-PACKARD DESKJET 840C
[   34.308270] lp0: using parport0 (interrupt-driven).[/FONT]

So the kernel recognizes that there is a HP840C on parport0.

First of all, I don't see any /dev/parport0 node on /dev... I don't know if it must be, but I think it's strange.

Then, if I try to install my printer through System -> Administration -> Printers of even directly with cups at localhost:631, inserting LPT#1 as device and URI: parallel/dev/lp0 (the same values that have always worked on Slackware) I can add my printer.

But when I launch even the simplest print, it starts to print dozens of white pages only with a few random characters and I only have to turn off brutally the printer.

Then dmesg says this:

[FONT="Comic Sans MS"][  688.469278] lp0: ECP mode
[  697.034379] lp0: ECP mode
[  697.238350] lp0: ECP mode
[  697.818317] lp0: ECP mode
[  753.817061] lp0: ECP mode
[  761.563984] DMA write timed out
[  799.761625] DMA write timed out
[  831.589901] parport0: FIFO is stuck
[  831.611730] parport0: PE,1 timeout (1) in ecp_write_block_pio[/FONT]

and the LPT#1 device option on cups administration disappears...

I tried even with printconf:

[FONT="Comic Sans MS"]sudo printconf 
Password:
Configuring HP DeskJet 842C on parallel:/dev/lp0 with hpijs driver as queue
"deskjet_842c".[/FONT]

 * Restarting Common Unix Printing System: cupsd                         [ ok ] 

but the result is the same.

Some one can tell me if I'm doing something wrong, or it's a real bug of ubuntu edgy eft?

Thank you.

TAD

---

### Post by gborzi on 2006-12-10
I have edgy i386 installed on my desktop PC, so I can't help you much. I can only say that there is not (and I think shouldn't be) a /dev/parport0 node in my system which is connected to a very old NEC P20 that works without problems.

---

### Post by TADsince1995 on 2006-12-10
> **gborzi said:**
> I have edgy i386 installed on my desktop PC, so I can't help you much. I can only say that there is not (and I think shouldn't be) a /dev/parport0 node in my system which is connected to a very old NEC P20 that works without problems.

Ok, this is really useful for me! I can exclude that the problem is the node. Thank you! ;) 

TAD

---

### Post by TADsince1995 on 2006-12-10
> **TADsince1995 said:**
> Ok, this is really useful for me! I can exclude that the problem is the node. Thank you! ;) 

TAD

WROOOOOOONG!!!!!

The /dev/parport0 node MUST BE PRESENT!!!

I added it writing 

mknod -m 666 /dev/parport0 c 99 0

and then hp-setup -a worked properly!!!


I really think it's a bug of ubuntu edgy eft!

How can I have this device node automatically set on ubuntu launch?

How can I signal it on the ubuntu creators?

TAD

---

### Post by gborzi on 2006-12-10
Sorry for giving you the wrong suggestion, but good to know that node is needed, at least on amd64. One way (perhaps _the_ way) to have this device node automatically created is to load ppdev module at boot, i.e. add it to /etc/modules. After loading this module with modprobe, it creates the node as > crw-rw---- 1 root lp 99, 0 2006-12-11 01:21 /dev/parport0
To report this problem to ubuntu developers you have to register yourself here [https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu) and file a bug.

---

### Post by TADsince1995 on 2006-12-10
> **gborzi said:**
> Sorry for giving you the wrong suggestion, but good to know it is needed, at least on amd64. One way (perhaps _the_ way) to have this device node automatically created is to load ppdev module at boot, i.e. add it to /etc/modules. After loading this module with modprobe, it created the node as 
To report this problem to ubuntu developers you have to register yourself here [https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu) and file a bug.

No problem if it was a wrong suggestion! Thank you for the way of adding with ppdev. By now I added a simple script on /etc/rc.local.

MMm... Reading your name it seems you are italian! Isn't it?

TAD from Italy

---

### Post by gborzi on 2006-12-10
> **TADsince1995 said:**
> 
MMm... Reading your name it seems you are italian! Isn't it?


Look at the Location: :)

---

### Post by brazzmonkey on 2006-12-19
> **TADsince1995 said:**
> WROOOOOOONG!!!!!

The /dev/parport0 node MUST BE PRESENT!!!

I added it writing 

mknod -m 666 /dev/parport0 c 99 0

and then hp-setup -a worked properly!!!


I really think it's a bug of ubuntu edgy eft!

How can I have this device node automatically set on ubuntu launch?

How can I signal it on the ubuntu creators?

TAD

man i must buy you a beer for this one ! i'm running edgy, my printer-fax used to work till today. somehow the dev node must have disappeared. i wasted my entire evening trying to fix it until i read your post.

i don't know if this is a bug, but i didn't do any major changes until this happened.

thanks a bunch !!

---

### Post by brazzmonkey on 2006-12-20
bug filed

---

### Post by KaiO on 2006-12-29
Thanks a lot, *TADsince1995* !
I have a parallel port HP OfficeJet g85 and I managed to get it printing, but scanning wouldn't work until I added the node as you suggested.
That node did the trick.

---

### Post by steefjeqv on 2007-01-20
Great solution !

Our HP 550C is finally working again.

Greetings,
Steven

---

