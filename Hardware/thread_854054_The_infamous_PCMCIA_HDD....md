---
title: "The infamous PCMCIA HDD..."
date: 2008-07-09
forum: Hardware
---

### Post by isaacj87 on 2008-07-09
Yes, it's true...I have a Toshiba MK5002MPL PCMCIA HD (5gb). I cracked open an old mp3 player I had (A Bantam BA1000-5g for those interested :D) and lo and behold, it had a little PCMCIA HDD in there!

I've been searching for hours to try and find solution for this, but to no avail. I've tried adding "irqpoll" to menu.lst. I've been searching for a way to enable the ide-cs module. I just can't get the thing to appear as a mountable drive.

Ubuntu seems to recognize it, but doesn't know what to do with it. Has anyone figured out a solution to getting PCMCIA Hard Drives to work with Ubuntu? By the looks of it, no one has. :(

Any help would be much appreciated!

Thanks :)

---

### Post by isaacj87 on 2008-07-10
bump :)

I'm hoping that at least one user is using a PCMCIA HDD. :D

---

### Post by nikgare on 2008-07-10
As what does Ubuntu recognise it?

---

### Post by isaacj87 on 2008-07-10
Well, this is what lshw is giving me

```
 *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:06:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
              *-storage
                   description: TOSHIBA
                   physical id: 0
                   version: MK5002MPL
                   slot: Socket 0
                   resources: irq:3

```

---

### Post by lswb on 2008-07-10
I happen to have one in an old ipaq expansion pack in a drawer right next to me. I watched syslog messages when I plugged it in. (tail -f /var/log/syslog in a terminal.) The system is seeing it, recognizes it as a pata hard drive, loads various drivers, etc, but there are errors and no device node is created. 

I never plugged this hd into this system using hardy. On an older laptop wih dapper installed, though it always "just worked" though I don't remember for sure if I had to mount it manually. 

I know, small consolation for you, but it looks like there may be a kernel or driver issue. I'll try playing with it later. If I get any results I'll post here. Let me know if you have any success too!

---

### Post by isaacj87 on 2008-07-10
> **lswb said:**
> I happen to have one in an old ipaq expansion pack in a drawer right next to me. I watched syslog messages when I plugged it in. (tail -f /var/log/syslog in a terminal.) The system is seeing it, recognizes it as a pata hard drive, loads various drivers, etc, but there are errors and no device node is created. 

I never plugged this hd into this system using hardy. On an older laptop wih dapper installed, though it always "just worked" though I don't remember for sure if I had to mount it manually. 

I know, small consolation for you, but it looks like there may be a kernel or driver issue. I'll try playing with it later. If I get any results I'll post here. Let me know if you have any success too!

Hey,

Thanks for the response. It's nice to know I'm not alone here! I've read that these drives used to work with anything before Feisty. I'm searching for a patch, but I know it's not going to be an easy fix.

---

### Post by lswb on 2008-07-11
"I've read that these drives used to work with anything before Feisty. "

Hmm, that's about the time the older separate utilites for pcmcia cards was dropped, supposedly because their function had been incorporated into the newer pc card/cardbus drivers. I have a vague memory of deleting the older drivers since they were said to be unnecessary, but then having to reinstall them to work with some older pcmcia cards. 

I'm a little hazy on the details right now, but there used to be separate driver packages for the older pcmcia (16 bit) cards and the newer cardbus (32 bit/pci) cards. At some point, the newer driver packages were to have taken over the function of the older packages, The Toshiba pcmcia hard disks use the older 16 bit pcmcia interface so it's likely this is related.

---

### Post by isaacj87 on 2008-07-11
> **lswb said:**
> "I've read that these drives used to work with anything before Feisty. "

Hmm, that's about the time the older separate utilites for pcmcia cards was dropped, supposedly because their function had been incorporated into the newer pc card/cardbus drivers. I have a vague memory of deleting the older drivers since they were said to be unnecessary, but then having to reinstall them to work with some older pcmcia cards. 

I'm a little hazy on the details right now, but there used to be separate driver packages for the older pcmcia (16 bit) cards and the newer cardbus (32 bit/pci) cards. At some point, the newer driver packages were to have taken over the function of the older packages, The Toshiba pcmcia hard disks use the older 16 bit pcmcia interface so it's likely this is related.

Thanks for the info! Oh man, if you happen to have the driver packages that support older pcmcia (or perhaps know where I could find them), I'd be *so* appreciative :)

---

### Post by lswb on 2008-07-11
Sorry, but there aren't any for hardy. dapper had separate subsytems for the 16 bit pcmcia cards and 32 cardbus, but in current kernels the pcmcia subsystem is supposed to handle both types. If I understand things correctly ( a big "if" :) ) even if you had the source code for the older modules and compiled them for the hardy kernel, they would conflict with the current pcmcia modules. 

Watching the kernel messages when plugging in the drive does indicate that the system sees the card and knows it's a disk drive, but is not able to complete the process of activating/reading or whatever you would call it. It seems to me that this is a plain old simple BUG, unfortunately. It's a shame that a 6 year ipaq running windows CE/pocket pc 2002, with an ARM processor and 64 MB memory can work with this drive, but a P4 with 1GB mem and the latest ubuntu OS can't! I might try to file a bug report, but I doubt it would get worked on anytime soon. Probably more productive to do some googling and see if there's any workaround or patch for the pertinent driver modules.

---

