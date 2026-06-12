---
title: "usb sounddevice not working"
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by sonium on 2005-12-07
Hi,
my USB-Sounddevice (M-Audio (former Midiman) Mobile-Pre USB) isn't working anymore. I don't no why and don't see any coincidence.
At Boottime the only Card 0 is mentioned, but not as before Card 1.
lsusb tells me that the card is connected but the gnome device manager calls it "unknown" 
I tried without success, to adapt my /etc/modules

```
alias snd-card-0 snd-cmipci
alias snd-card-1 snd-usb-audio
alias snd-card-2 snd-usb-audio
options snd cards_limit=3
options snd-cmipci index=0
options snd-usb-audio index=1,2 vid=0x0763,0x0763 pid=0x1010,0x2804
```

(the second usb-audio is a midi-interface)

/proc/asound/cards says:

```
0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                     C-Media PCI CMI8738-MC6 (model 55) at 0xb800, irq 21
```

which is only my PCI sound-card, but not the usb device.

Restarting neighter alsa-utils restart nor reconnecting the device does fix the problem.

---

### Post by 23meg on 2005-12-08
Did it work before with Ubuntu? Did it start not working after a kernel or other critical update?

---

### Post by sonium on 2005-12-08
yes, it worked before on ubuntu. After installing some critical update (also profided a new kernel, but the old doesn't work too) it didn't work. Unfortunately I don't know which update it was.

---

