---
title: "Xircom/Compaq issue"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by troplicalotus on 2005-07-31
Hello Ubuntu forumers,

I would be most grateful for any help with the following issue:

My Compaq Armada 6500 has an integrated Xircom 56K Modem+10/100Mb Combo PCMCIA card. This device was automatically detected by Redhat 8.0 and I have used it successfully for 2-3 years. Recently I installed Ubuntu 5.0.4 and this is the only bit which does not seem to work.

Any advice as to how this device can be used correctly with Ubuntu? Although I have been using Linux for several years (since Caldera OpenLinux 1.3) it has been very user friendly so I haven't done any serious tinkering with it.

With thanks and best regards,
Sunny

---

### Post by troplicalotus on 2005-08-02
Bump

Any suggestions? The fact that this was detected and worked in Redhat makes me think it should not be too difficult in Ubuntu. There must be some way to manually input the settings, perhaps from the command line?

Thanks again

Sunny

---

### Post by bin on 2005-08-02
Hi

Sorry, just a little confused by the hardware.

Does the laptop have a built in modem and then you are using a combo card as well, or is it just a Xircom combo card.

Am I correct in assumomg that neither the modem nor the network connection work?

When you were installing Ubuntu, did you have the network connection in place and connected to a router or something similar. the reason I ask is that I had all sorts of fun with a supported wireless PCMCIA until I did the install with it in place, During the install it shoyuld have come up with netework detection on your screen - did that happen?

If it's just the modem side then we're off down a different track.

Try doing lspci -v and have a look for anything related to the Xircom

in light

bin

---

### Post by troplicalotus on 2005-08-03
hello bin, and thanks for the reply.

The Armada 6500 has a preinstalled Xircom combo card, that is part of the PCMCIA system but is not in either of the two PCMCIA slots - it is in the back of the machine where all the other ports are found.

The machine is not connected to a LAN but will be used with dialup internet, so my goal at this point is to get the modem function operating. At install time I chose not to configure network settings. 

There must be a relatively simple way, perhaps requiring some command line instructions, but in my ignorance I don't know it. In seven years of Linux use almost everything has been done from the GUI, so shame on me for failing to learn more.

cheers,
sunny

---

