---
title: "Touchpad doesn't work"
date: 2016-02-20
forum: Hardware
---

### Post by deppgirl on 2016-02-20
At this moment in time I only have 2 problems with Lubuntu which I also had with Ubuntu, Linux Mint, Elementary OS... basically any linux distro. 

1. the touchpad will not work and I've tried a lot of different options, but I'm not convinced I have tried everything

2. when I shut down the computer it gets stuck on the splash screen and will not shut down. at one time the screen would at least go black but the computer was still on, now it just freezes on the splash. 

any help would be appreciated!

Note: I'm most worried about the touchpad.

---

### Post by veddox on 2016-02-21
Hi there :-)

My first thoughts on the touchpad: check this [Ubuntu help page]("https://help.ubuntu.com/community/SynapticsTouchpad"). Also, it might help to reinstall the touchpad driver (if you have a Synaptics touchpad, that's the [synaptics package]("http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html")).

On the other hand, both of these problems might be hardware related. Could tell us the specs of your laptop? How old is it, what processor does it have, how much RAM, etc.?

Cheers,
veddox

P.S. You brought forward two issues in this thread. In future, please open a new thread for every issue you have, it makes the whole troubleshooting process that much easier.

---

### Post by deppgirl on 2016-02-21
Thank you for the reply, I'm most worried about the touchpad anyway so I could always edit my post. 

My laptop is an Acer E 15 start, I've only had it a year, Intel Celeron Processor N2840, Intel HD Graphics, 4GB DDR3 L Memory, 500 GB HDD

Pardon me if I missed anything out, I'm repeating the above off the sticker on the computer as I'm not really sure how else to find it. This laptop came with Win 8.1 but I believe windows was too much for it and it froze way too often for it to even be usable, so it is now strictly Linux (Lubuntu), works a lot faster, only issues is the touchpad and the shutting down.

Oh, I've also run xinput list and I frankly don't think my touchpad is even being detected as nothing seems to come up other than the optical physical mouse i'm using and virtual core Xtest pointer

---

### Post by veddox on 2016-02-21
I just found [this thread]("http://community.acer.com/t5/E-and-M-Series/Aspire-e15-e5-511-p9y3-Touchpad-not-working-on-windows8-1/td-p/277578") on an Acer support forum. It's in reference to Win8.1, but seems to describe your problem exactly and involves the same laptop model. There, the situation was to install the OS in UEFI mode (help guide for Ubuntu [here]("https://help.ubuntu.com/community/UEFI")).

I don't know if reinstalling the OS is an option for you. In any case, you might like to try (re-)installing the synaptics package - just for good measure.

If you're feeling adventurous, [this thread]("http://ubuntuforums.org/showthread.php?t=2244174") recommends installing the package i2c-tools. However, I do not know what the package does, nor could I find anything out with a quick web search. The posters on that thread also didn't seem to be the most knowledgeable around. So while I wanted to point it out to you as a possible course of action, you follow that route at your own risk ;-)

---

### Post by deppgirl on 2016-02-21
Thank you for the help, I had just started to wonder if I should have installed the OS in UEFI mode as a posed to legacy and was looking up that route when I came across your reply. That may be what i need to do, or I can possibly try boot repair and see if that helps. 

Thanks!

---

### Post by deppgirl on 2016-02-21
I managed to reinstall lubuntu in UEFI and the touchpad now works. The computer will not boot correctly or restart correctly but since I can boot in a round about way and still turn it off via the physical button i'm not too worried about it. 

thanks for all the help.

---

### Post by veddox on 2016-02-21
Great to hear the touchpad works at least! If I were you I would open a new thread for the booting issues - you don't really want to be booting your computer in "a round about way" for ever... ;-)

---

### Post by deppgirl on 2016-02-21
I actually got the boot to work now, I had to go into BIOS and set supervisor password and then select which efi to trust and that fixed the problem, so It boots perfectly! Only problem now is that it freezes at shutdown and restart and i have to use the physical power button.

---

