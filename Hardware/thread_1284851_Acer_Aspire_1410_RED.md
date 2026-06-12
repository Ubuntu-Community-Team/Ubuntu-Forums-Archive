---
title: "Acer Aspire 1410 RED"
date: 2009-10-07
forum: Hardware
---

### Post by deemoowoor on 2009-10-07
Dear Ubuntu community!

Recently I've bought a new shiny Acer Aspire 1410 RED, which features an **Intel WiFi Link 100** wireless card (whole chipset is actually Intel). It shipped with a very limited Linpus Linux (there was even no X, just bare console!) based on 2.6.24 kernel. Even pci.ids database was missing there... :P 

Anyway, after installing Ubuntu 9.04 "Jaunty Jackalope", with its 2.6.28 kernel, GDM, XOrg worked fine. But the wireless card I've got doesn't work in 2.6.28. 

A little Googling led me to a page, where I found out that the driver for this wireless card is "iwlagn", and that I needed firmware for this card to work. I've downloaded iwlwifi-1000-ucode-128.50.3.1.tgz firmware archive from [http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads) and extracted it to /lib/kernel/firmware or something like that (dmesg showed that driver module did find the firmware there, but I would then basically get the same issue, as in the following bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/439285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/439285)).

It doesn't work in Karmic's 2.6.31-11, too, according to the above mentioned bug. 

Also in that bug report, there are two options reported:

1. Install linux-backports-modules for the kernel in use
2. Install linux-image-2.6.32 from [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) 

I tried both, with little overall success. First, linux-backports-modules for 2.6.28-11 would not work. It would complain about iwlagn not being able to find EEPROM on the wifi card. (I'm currently away from that laptop, so cannot give you any actual logs, I'll add them later today).

Second option is actually moderately successful -- the card is being correctly detected and even WiFi card's LED is lit up! But I could not connect to my AP to get an IP address using DHCP -- which is a problem I'd leave to be solved later.

Because there's another issue with 2.6.32: for some reason with v2.6.32-RC1 kernel from the above mentioned link, it would not load GNOME. It manages to load XOrg server until black screen with mouse pointer appears and then it stops. I can't change to a console using any of the CTRL+ALT+F1 ... F6 buttons, I can't kill (restart) X using CTRL+ALT+BACKSPACE. Only hard reboot helps. :(

The video card is **Intel GMA 4500 MHD**.

I tried to see the X.0.log, dmesg, everything, but it would be almost completely identical to the logs of a successful load of 2.6.28-11, except for timestamps and kernel version, of course, without any errors or warnings... :( Maybe someone of you knows of any known compatibility issues of Jaunty with that newer kernel?

I can see, that I could try and install the **9.10 Karmic Koala** Beta, which has a slightly newer kernel than Jaunty and then install the linux-backports-modules for 2.6.31 on to that... Anyone of you tried it? Any luck?

I'd like to know if anyone had any similar issues (with Acer Aspire 1410 RED, or at least with the **WiFi Link 100** wireless LAN card) and if they did, maybe they could point me to a possible solution or lack thereof? Let's investigate this together, because I think my head will explode soon from all these problems... :)

---

### Post by deemoowoor on 2009-10-08
Anyone having the same issue? Maybe I missed something obvious?

---

### Post by oscarenzo on 2009-10-08
i have the same problem, i use a laptop 64 bit, amd, someone can help me?

---

### Post by deemoowoor on 2009-10-08
Do you mean that you've got the same WiFi card? Or same laptop (Acer Aspire 1410 RED / 1810T)? It actually comes with a Celeron Core 2 Solo with an Intel chipset motherboard...

If you just happen to have a problem with another WiFi card, I'd suggest you to open a new thread. Definitely specify the model of the WiFi card installed (this can be done by typing the following on the console:

```

lspci

```

You will find the WiFi card listed as a Wireless LAN card or something similar.

---

### Post by tudalex on 2009-10-08
> **deemoowoor said:**
> Do you mean that you've got the same WiFi card? Or same laptop (Acer Aspire 1410 RED / 1810T)? It actually comes with a Celeron Core 2 Solo with an Intel chipset motherboard...

If you just happen to have a problem with another WiFi card, I'd suggest you to open a new thread. Definitely specify the model of the WiFi card installed (this can be done by typing the following on the console:

```

lspci

```You will find the WiFi card listed as a Wireless LAN card or something similar.

OK I had put the 2.26.32 RC3 kernel on mine and manged to switch to CTRL+ALT+F2, the wifi card works well, I managed to connect to my wireless network from command line and get a dhcp.

BTW it the notebook also comes in a version with a Celeron 743M with the same wireless card. Guess will have to wait for the official 2.26.32 Kernel to come up... wondered if we would use Kernel 2.26.31 (which partially identfies the network card) and try to compile the kernel module from the sources of the .32 Did anybody try?

---

### Post by tudalex on 2009-10-08
Ok I got it working. I am using ubuntu 9.10 beta with kernel 2,.6.31-12 generic. Hope this helps. I had to activate in the software sources the karmic repositories for it to do a partial upgrade which included the new kernel. Waiting to hear if you managed to make it work, maybe we can write a tutorial or smth...

---

### Post by deemoowoor on 2009-10-09
Thanks a lot for the info, I'll try it out!

---

### Post by deemoowoor on 2009-10-09
Yes, it's a success!! :) Let's write a how-to. :)

I've also noticed now, that **Bluetooth doesn't work in Karmic** on this laptop, although it used to in Jaunty with 2.6.28-11... A regression in kernel package or something needs to be setup first?

Basically, to make the WiFi Link 100 work in Ubuntu:

Update to Karmic's kernel:
**Option 1**: Install Karmic from scratch or make a dist-upgrade to it
**Option 2**: Install kernel image 2.6.31-12 from Karmic's updates [http://packages.ubuntu.com/karmic/base/linux-image-2.6.31-12-generic](http://packages.ubuntu.com/karmic/base/linux-image-2.6.31-12-generic)

Second option is an alternative, which should also do the trick. Did not try it myself, but I think it should work, too!

---

### Post by deemoowoor on 2009-10-09
Concerning Bluetooth, it was my mistake: I forgot about the hardware button to switch it on. :) It works as good as it did in Jaunty.

---

### Post by juliansuddaby on 2009-10-09
Hi,

This is all a bit confusing to me: on my Acer Aspire 1410 (Black, not red), the wireless works fine on a fresh install of 9.04 Jaunty (amd64).

Lspci reports me having an Intel Corporation Wireless WiFi Link 5100.

Running the 2.6.28-15-generic kernel.

---

### Post by deemoowoor on 2009-10-09
Well, I guess these 1410-s are all different, then. 1410 is just a series number, with actual models being something like ZH7 (in my case). They may have very different specs and hardware, too.

---

### Post by tudalex on 2009-10-09
Well from what I know there are mainly two models the 11.5 inch screen ones and the 15 inch screen ones. We are talking about the 11 inch ones (that's what I have) if it's helpfull my model code is 1410-743G25n

---

### Post by deemoowoor on 2009-10-09
That looks like a serial number. The model number is on the black patch with all CE marks etc. and an Acer logo. 

It says something like:

Aspire 1410 series
MODEL.NO.: ZH7

(in my case)

---

### Post by tudalex on 2009-10-09
Yeap checked it's also ZH7.

---

### Post by PatrickVogeli on 2009-10-18
hi there,

my girlfriend also has a ZH7, but packed for/by Packard Bell and has also the 5100 card.

I plan getting the dual core 1810tz this week, I'll see what wifi I get.

---

### Post by PatrickVogeli on 2009-10-23
Hi, 

I finally got the 1810tz and it also feature the Intel 1000 card. I've installed karmic and the card works out of the box, so everything is fine.

---

### Post by deemoowoor on 2009-12-11
Today, after a system upgrade (to a kernel 2.6.31-16) I had the problem with WiFi reappearing again. But this time it would load the firmware and all is nice, until I tried to connect to my home network AP, which is configured to use a 128-bit WEP key for encryption. It wouldn't connect anymore. Something tells me the problem is in the recent kernel's driver, but it might be something else.

OK, after reconfiguring my WiFi AP to only accept Open System WEP, it suddenly started working. It was set to "Both", i.e. to both Open System and Shared Key authentication mechanisms before.

---

### Post by tehowe on 2009-12-20
This looks like the closest thread relevant to my question...

So, I have this shiny new Acer 'Olympic Edition' 1410 - that's the 11.6" sort-of-netbook, with the dual-core SU3500.

I'm trying Wubi first as I've no intention of taking the chance of wrecking Win7 (any further, ha) with a partition unless I know Ubuntu actually works first.... uh, which it doesn't.

The problem I've experienced are, 9.10 Wubi drops into bash on bootup... as has been documented elsewhere.

9.04 Wubi runs but recognizes neither wireless, ethernet, nor suspend when I close the clamshell.

I might be willing to spend, say, two hours getting this to work, but what do you think? Is there a reasonable fix for this or would I be better advised to wait for the next LTS when *of course* all of these issues will be fixed. :cool:

---

