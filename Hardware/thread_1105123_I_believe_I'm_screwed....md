---
title: "I believe I'm screwed..."
date: 2009-03-24
forum: Hardware
---

### Post by sudoxe on 2009-03-24
K so, I have had Ubuntu on my laptop before, but since I have Atheros, there was a hacked driver or something from Madwifi that is not in use anymore, and am not able to find it. I feel that I'm officially stuck with Vista since Compaq doesn't have any type of Linux drivers...

Is there a Linux-friendly laptop, that has around the same specs as this one?

HDD: 160Gb
Processor: >=1.9-2.0 Ghz
RAM: 2Gb

Oh and something that doesn't have the POS Atheros....

---

### Post by teaker1s on 2009-03-24
A bit blunt title, can you provide output of this command in terminal
```
sudo lspci -v
```

Secondly Atheros cards can be run several ways with
Ath_hal
ath_pci
madwifi trunk drivers
some using ubuntu backports
ndiswrapper and windows driver

if you can provide the output and model number it should be possible to sort it.

---

### Post by stchman on 2009-03-24
> **teaker1s said:**
> A bit blunt title, can you provide output of this command in terminal
```
sudo lspci -v
```

Secondly Atheros cards can be run several ways with
Ath_hal
ath_pci
madwifi trunk drivers
some using ubuntu backports
ndiswrapper and windows driver

if you can provide the output and model number it should be possible to sort it.

You forgot ath5k as well.

The ath_pci madwifi drivers appear to be the best solution for Atheros cards.

---

### Post by kevmitch on 2009-03-24
Actually, you're probably the opposite of screwed. The reason madwifi is no longer active is that ath9k and ath5k have been added into the kernel so there's no need for a non-free driver anymore. You can't get better support than that. They should automatically just work out of the box. I've found this to be the case with my AR5418 card at any rate. You just need to make sure that you're running at least kernel 2.6.27 which comes with Intrepid Ibex.

You can check your kernel version with
```
uname -r
```

---

### Post by sudoxe on 2009-03-27
I got fed up with it, so I went ahead and put Vista ultimate back on, but its the Atheros AR5007. When I had it working in the past, I had it under ath_pci. So you're saying its supported out of the box finally with Intrepid?

---

### Post by blackened on 2009-03-27
> **sudoxe said:**
> I got fed up with it, so I went ahead and put Vista ultimate back on, but its the Atheros AR5007. When I had it working in the past, I had it under ath_pci. So you're saying its supported out of the box finally with Intrepid?

Kernel module support for your hardware is as out of the box as you'll ever get.

---

### Post by kevmitch on 2009-03-27
On Intrepid, it should work out of the box. This won't be the case for Hardy though. 

You could also try installing linux-backports-modules to get a newer version of ath9k as it has improved significantly since the 2.6.27 kernel in Intrepid. Nevertheless, I still found that even the 2.6.27 version is far more stable than ath_pci ever was.

---

