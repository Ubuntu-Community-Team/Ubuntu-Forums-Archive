---
title: "Does Ubuntu 12.04 support USB 3.0 speeds?"
date: 2012-09-07
forum: Hardware
---

### Post by stchman on 2012-09-07
Hello all.  I have a slightly older PC that I would like to add a USB 3.0 card to.

If indeed Ubuntu 12.04 supports USB 3.0 speeds, can the forum recommend a card (either PCI or PCI-e) that is OOB compatible with Ubuntu 12.04.

Thanks.

---

### Post by stchman on 2012-09-11
Bump.

No one knows.

---

### Post by melchiorre on 2012-09-11
Kernel linux was first to support with drivers usb3; so I think there are not problembs with it

---

### Post by Mark Phelps on 2012-09-12
> **melchiorre said:**
> Kernel linux was first to support with drivers usb3; so I think there are not problembs with it

Actually, there ARE.

I've been using a Vantec USB 3.0 external HDD box with my PC and, despite running 12.04, the box did NOT achieve USB 3.0 speeds until I was able to find a firmware update for the motherboard chipset -- and run that in MS Windows.

So, having kernel support is not enough.

---

### Post by rykel on 2012-09-18
I am also getting only 8 MBps speed with Ubuntu 12.04 (fully updated) with my USB 3.0 external HDD.

How can I get 80 MBps?

---

### Post by shreepads on 2012-09-18
> **stchman said:**
> Hello all.  I have a slightly older PC that I would like to add a USB 3.0 card to.

If indeed Ubuntu 12.04 supports USB 3.0 speeds, can the forum recommend a card (either PCI or PCI-e) that is OOB compatible with Ubuntu 12.04.

Thanks.

Yes indeed it does:  Transcend TS PDU3 PCIe USB 3.0 expansion card 

See here:
[http://ubuntuforums.org/showthread.php?t=2058351](http://ubuntuforums.org/showthread.php?t=2058351)

---

### Post by shreepads on 2012-09-18
> **rykel said:**
> I am also getting only 8 MBps speed with Ubuntu 12.04 (fully updated) with my USB 3.0 external HDD.

How can I get 80 MBps?

How are you measuring that and is it read/ write? And what's the HDD inside the external USB 3.0?

(See link in my post above)...

---

### Post by Scott Harrison on 2012-09-18
Seems to work for me?

---

### Post by Jagoly on 2012-09-18
It depends on the controller the card is using. Just try and get one using an NEC controller, and it will work great. ASMedia and Etron controllers MAY cause problems; on one of my computers with an etron controller, the usb3 ports did not work in 11.10, however they are supported by the newer kernel in 12.04. I can't speak for the ASMedia controllers.

---

### Post by jaithehulk on 2012-09-19
I have a USB 3.0 port on my laptop...also I have a 1Tb external HDD.. In order to achieve USB 3.0 speeds both my laptop and HDD shld support USB3.0 correct?

---

### Post by Jagoly on 2012-09-19
> **jaithehulk said:**
> I have a USB 3.0 port on my laptop...also I have a 1Tb external HDD.. In order to achieve USB 3.0 speeds both my laptop and HDD shld support USB3.0 correct?

Short answer is yes.

---

### Post by rykel on 2012-09-28
> **shreepads said:**
> How are you measuring that and is it read/ write? And what's the HDD inside the external USB 3.0?

(See link in my post above)...

I was transferring many large files to and fro the external HDD via USB 3.0. (cannot remember if it was read/write)

The external brand is the Japanese BUFFALO anti-drop but I do not know what is the HDD inside though.

btw, is there any Ubuntu app which can test if my system is running at USB 3.0 speed?

---

### Post by Jagoly on 2012-09-29
Ubuntu comes with an app called disk utility, it can do read benchmarks on a drive. It can also do write benchmarks, but that requires the drive to be completely blank.

---

### Post by rykel on 2012-09-29
> **Jagoly said:**
> Ubuntu comes with an app called disk utility, it can do read benchmarks on a drive. It can also do write benchmarks, but that requires the drive to be completely blank.

Hi, I tried that and it is good. However, I am unsure what READ speed I should be expecting for USB 3.0?

---

### Post by Jagoly on 2012-09-29
You could try plugging the drive into a usb 2 port and benchmarking it there as well, then comparing the results.

---

