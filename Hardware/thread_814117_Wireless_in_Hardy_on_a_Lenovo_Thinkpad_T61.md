---
title: "Wireless in Hardy on a Lenovo Thinkpad T61"
date: 2008-05-31
forum: Hardware
---

### Post by variableenigma on 2008-05-31
I just got a new Lenovo Thinkpad T61, and I installed Hardy Heron from an installation disk.

The wireless internet is buggy. It is often slow, and stops and starts and stops and starts over and over again. It won't STAY connected!

The following text is in lspci, if that helps (let me know any more information you might need- and how to find it, please!!)

"00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
...
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)"


Thanks in advance :)

---

### Post by fitzman49 on 2008-05-31
> **variableenigma said:**
> I just got a new Lenovo Thinkpad T61, and I installed Hardy Heron from an installation disk.

The wireless internet is buggy. It is often slow, and stops and starts and stops and starts over and over again. It won't STAY connected!

The following text is in lspci, if that helps (let me know any more information you might need- and how to find it, please!!)

"00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
...
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)"


Thanks in advance :)

I would recommend installing the proprietary driver since it is an Atheros chipset since they are usually well supported in Linux.  Go to System->Admin->Hardware Drivers and check the box next to the appropriate driver if it isn't checked already.  I think the driver will show up there as Atheros HAL module or something of that nature (at least it did last time I used a Atheros chipset).  Working from a T61 myself but got the Intel 3945ABG chipset.

Fitz

---

### Post by variableenigma on 2008-06-01
There are two boxes checked:
Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 Wireless LAN cards

Both are checked and say "In use"

I'm still getting really bad connections. Anyone have other ideas?

---

### Post by variableenigma on 2008-06-02
I'm just going to try to update this thread a bit with what I've been trying to do..

Firstly, I DO get wireless internet, BUT, the signal is very weak- even where my old laptop gets about 75-90% this one gets about 40-70%.

This is an issue because it runs very slowly, and sometimes cuts out and doesn't work at all. 

I tried installing madwifi, but I'm not even sure it installed. I'm not sure how to check to see if it's actually there, but either way, I'm still having the same trouble as before.

I tried booting up to Vista (which came native on this computer), and the signal is "Excellent". I assume, therefore, that it is not my computer, but how the computer interacts with Ubuntu.

The internet also works perfectly fine with a wired connection, so it is only the wireless that has this problem.

What do I do? I need a better wireless connection!

---

### Post by ahmedh on 2008-06-04
Is this the standard card or the 3945/4965 upgraded wireless card?

---

### Post by wabbalee on 2008-06-04
this may be irrelevant as i am no expert, but i have an acer with a broadcom wireless and for this chipset are two drivers available: a native linux one, which is free but does not make it work to the full speed and coverage as it uses an (i think) older standard. the other is the proprietary driver which runs under ndiswrapper, this works with the windows drivers, tricking it to 'think' it is in a windows environment through ndiswrapper. why am i telling you this? because in my case i cannot have both drivers installed, one has to choose: ndiswrapper or native. i think with atheros chipsets you must use mad wifi, you can check in your package manage if it is installed by doing a search for the package. i do not know if atheros has the same conflict with native (if they exist) and proprietary drivers. may be an other and succesful atheros user could give us some insight here.

---

### Post by variableenigma on 2008-06-04
I'm not sure if it's standard or upgraded. I did JUST get this laptop, so maybe it's the upgraded one? How do I find out?

I also have no idea if the madwifi driver is conflicting with another one. In fact, I don't even know what the other one would be called if it was! I will try to figure that out!

---

### Post by ahmedh on 2008-06-04
Hmm, it seems like you have the standard one, because the upgrades are Intel cards and your lspci output says Artheros. The upgrades work "out of the box" with the current linux kernel. You need to blacklist one of the drivers, I think, but I don't know how to do that.

---

### Post by wabbalee on 2008-06-07
black list a driver i have heard of that, also don't know ho to do that, but i do not know if that is nessecary if you can uninstall the native driver. in my case i had to uninstall 'bcm43xx' and 'fwcutter' if i am not mistaking. then i installed ndiswrapper and the proprietary windows driver 'bcmwl5.inf' and it now works the way it should. 

again, i do not know if the atheros driver works in a similar way but this is the path i went through to get mine to work.

you could go through some of your network related installed files in synaptic and read their descriptions to find out what they do and if you need them in your configuration. trial and error got me there many times.

---

### Post by phoenix9262 on 2008-06-11
hey folks, I have a t61 with the wireless n package; installed the wireless n driver thru ndis wrapper and it said it worked. the problem is that the wireless icon doesn't light up on the comp itself and it won't show the wireless connection under network config. help???

---

