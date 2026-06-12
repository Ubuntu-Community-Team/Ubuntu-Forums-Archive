---
title: "Laptop problems with HP 6510b series laptop"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by rzei on 2007-09-10
Hey everyone!

I recently bought a HP 6510b laptop, with the following configuration:
[LIST]
[*]Intel Core 2 Duo T7300 and 2*1024MB sticks
[*]Intel PRO 3945ABG WLAN chip
[*]HP Integrated Module with Bluetooth Wireless Technology
[/LIST]

There's nothing more info about the bluetooth module on the [quickspecs sheet]("http://h18000.www1.hp.com/products/quickspecs/12684_div/12684_div.HTML") [hp.com].

**Problems with Kubuntu 7.04:**
[LIST]
[*]Entering SUSPEND mode works, but when waking up, neither of synaptic touchpad or keyboard works, however login screen can be invoked by pressing power button
[*]After hibernating in MS Vista, then hibernating in Kubuntu, and resuming Kubuntu, battery information stays in "Charging" with no time information regardless if it really is charging or using the battery
[*]Battery is spent about two times faster in Kubuntu than MS Vista, with full charge in vista 4 houres is reported, in Linux 3 houres, with the same processor speed (800MHz both cores)
[/LIST]

The battery usage under Kubuntu might be related to the bluetooth device and possibly powering down the hard disk... Latter I don't matter, but I'd like to disable bluetooth.. Any ideas anyone?

The non-working suspend mode also puzzles me. If anyone has any ideas how to trace or solve this problem, please report any ideas! :)

---

### Post by archie_ on 2007-09-10
I'm running Ubuntu 7.04 and can confirm some issues with the suspend mode, however, hibernating works fine for me. Are you also having problem with the CD/DVD? I can neither read or write CDs or DVDs which is, to say the least, quite annoying.

---

### Post by rzei on 2007-09-13
> **archie_ said:**
> I'm running Ubuntu 7.04 and can confirm some issues with the suspend mode, however, hibernating works fine for me. Are you also having problem with the CD/DVD? I can neither read or write CDs or DVDs which is, to say the least, quite annoying.

I have now tried out running the latest stable kernel, which seems to fix at least the problem with suspend to ram, and in general using the more recent kernel seems to give lower power consumption.

I tested it with ipw3945 driver version 1.2.2 which needs more recent wireless-tools package and newer ieee802.11 stack and a more recent regulatory daemon for the wireless chip -- which the current 7.04 distribution doesn't provide. Result is bad Wi-Fi connection (breaking up randomly plus errors in daemon log).

I'll try it next with the same version (1.2.0) than the current linux-generic image and see what happens! I might write out an tutorial and try out how to solve that CD/DVD problem.. I imagine that the latest kernel also corrects that!

---

### Post by rzei on 2007-09-13
Oki, I've now tried out the latest kernel 2.6.22.6 with ipw3945 driver version 1.2.0.

Everything else than the ipw3945 driver seems to work! Lower power usage etc. than the default Kubuntu/Ubuntu kernel.

Too bad that the ipw3945 driver oopsed the kernel!

I have no idea how to continue from here... I guess I'll stick to the generic kernel for now on.

---

### Post by rzei on 2007-09-21
Archie, the CD drive problem can be solved easily by the following commands:
> sudo modprobe ide_generic

For some reason, ide_generic driver doesn't load automatically.. Possibly the kernel or what ever feels it's unnecessary as we already have main hard disk support :)

ide_generic will load ide_cd and cdrom modules automatically.

---

### Post by maclenin on 2007-10-22
**rzei:**

Fantastic. My similar DVD/CD drive issue (in Fesity) seems to have been resolved by the ide_generic modprobe. I am using an HP 6910p with a dual-layer DVD/CD burner....

Thanks for the post!

---

### Post by ercans on 2008-03-07
I bought hp compaq 6510b (it's specifications are nearly like [THIS]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/321957-321957-64295-321838-89315-3355650-3355661-3434183.html?jumpid=oc_R1002_USENC-001_HP%20Compaq%206510b%20Notebook%20PC&lang=en&cc=us"))

And I use Kubuntu v7.10 on it. I have problem with wireless connection. The light of the wireless connection don't work. And no connection.

can anybody help me


THANKS 

es

---

### Post by robenroute on 2008-03-07
Hi ercans,

Have you tried the wireless switch (which incidently is the same as the little blue wireless light)? Just touch it softly. It might sound silly, but I remember my own bewilderment about the "absence" of the wireless switch when I first got my 65010b...

---

### Post by rzei on 2008-03-07
hi ercans,

you can check robenroute's hint (wheter you have accidentally pressed the wireless button or not) by opening up a console/konsole and writing:
```

dmesg | grep ipw3945

```

If above doesn't print out any lines, it seems that you have to solve why aren't your wifi modules loading..

Following commands on a console will attempt to reload wifi drivers.. Sometimes the ipw3945d process (regulatory daemon for the chipset) hangs or dies unexpectedly, so you might need to use these in the future too!
```

sudo modprobe -r ipw3945 # try to unload the module ("-r" stands for "remove")
sudo modprobe ipw3945 # try to load the module

```

---

