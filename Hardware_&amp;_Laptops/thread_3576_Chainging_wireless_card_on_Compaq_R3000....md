---
title: "Chainging wireless card on Compaq R3000..."
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by oberon on 2004-11-07
Has anyone changed out the wireless (mini-PCI) card in their R3000 series Compaq notebook?  This may sound bad, but I can't even find the mini-PCI slot.  I have removed the entire bottom plastics, heat pipe, etc, but I can not find any way of removing the KB or top plastics to gain access to that part of the pc.  I think that is where it is located since I haven't found it anywhere else.  I though maybe someone here may have swaped it out and could let me know the secret to getting to it. :grin:  Please let me know, thanks.

---

### Post by oberon on 2004-11-07
Okay, I found a service manual and got under the KB.  I have installed the card (PrismGT), but now I get an error during POST: "104-Unsupported wireless network device detected."  If I remove it the pc boots up fine.  Doing some digging I found that HP usses some thing calle BIOSLock to whitelist mini-PCI devices and anything not on it apparently doesn't work.  Has anyone found a "fix", or a hacked bios to get around this?

---

### Post by oberon on 2004-11-08
The more I look into the problem, it sounds like a TCPA enabled bios.    I will keep looking to see if I can locate some way to flash the chip with a modified whitelist.  This is just another example of vendors locking you in to hardware and preventing fair use of the equipent you **_purchased_**. :evil:

---

### Post by ianhogben on 2005-01-17
I just came across this problem myself. I went out and bought a new WiFi card without stopping to wonder if my craptop would prevent me from using it or not. I am so disappointed in this kind of restriction. I can't imagine buying HP again. :x

---

### Post by swim_arch on 2005-04-29
Hi, desperatley seeking release from broadcom!
any luck with the swap?

---

### Post by banditjing on 2005-05-03
i'm assuming all of the R3000 use amd64.  I have gotten the broadcom wireless to work with the ndiswrapper and a 64bit compiled version of the driver (found somewhere here on the forums).

however it's stopped working now.  i'm considering getting another wireless card, but will probably take back the laptop instead.

---

### Post by ubutribe on 2005-12-20
Anybody know where exactly the Broadcom wlan 802.11bg antenna is within the Presario R3000 notebook casing?

---

### Post by vertigo23 on 2006-01-24
At one point I found a technician's manual for that laptop on Compaq/HP's web site.  To get at the mini-PCI slot, you need to unscrew three long screws from the bottom back of the laptop, near the ports.  Then, you wedge out the panel with the power button on it above the keyboard.  You can do this with a screwdriver under the 'insert' key.  After that, there are four easy-to-access screws holding down the keyboard, under which is the mini-pci slot, and a 2nd RAM slot.

Hope this helps!  I found this thread after I got burned by the same 104-yuor-card-suxorz.  You can't put a stock US$27 Intel 2200 wireless card in the damn thing.  :mad:

---

### Post by zonzhal on 2006-02-05
This guy edited his bios on a hp pavilion if you're interested.... bit hard though it seems.  It has the same bios problem.

[http://www.richud.com/HP-Pavilion-104-Bios-Fix/]("http://www.richud.com/HP-Pavilion-104-Bios-Fix/")

---

### Post by latas on 2006-04-03
You can get your own customized and patched BIOS from here: [http://www.hydra-networks.com/biospresario/index-en.html](http://www.hydra-networks.com/biospresario/index-en.html)

Cheers.

---

### Post by rojan shmavonian on 2006-04-16
[QUOTE=oberon]Okay, I found a service manual and got under the KB.  I have installed the card (PrismGT), but now I get an error during POST: "104-Unsupported wireless network device detected."  If I remove it the pc boots up fine.  Doing some digging I found that HP usses some thing calle BIOSLock to whitelist mini-PCI devices and anything not on it apparently doesn't work.  Has anyone found a "fix", or a hacked bios to get around this?[/QUOTE]


how did you remove the top case? I need to replace the keyboard.
thank you

---

