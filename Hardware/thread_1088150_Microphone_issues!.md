---
title: "Microphone issues!"
date: 2009-03-05
forum: Hardware
---

### Post by ilcontegis on 2009-03-05
Hi guys,
I finally trashed vista from my pc (sonva vaio tt50B) it was too slow.
Now I am having some minor issues. One of them I would like to solve it.
It is the integrated mic. I cannot use it.
as I have HDA intel sound card i followed the wiki on the forum but t does not work.
```
teo@teo:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889
Codec: Intel G45 DEVCTG

```
Why I have 2?
```
teo@teo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0b:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0b:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
0b:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0b:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

```
As i did not find my model I added
```
options snd-hda-intel model=auto
```
when I gave this command ```
teo@teo:~$ sudo gedit /etc/modprobe.d/alsa-base

```

If you can help me it will be nice

---

### Post by ilcontegis on 2009-03-06
up

---

### Post by ilcontegis on 2009-03-06
nobody? please I need to make conferences with this laptop.
Thank you :D

---

### Post by ubuntu27 on 2009-03-06
I don't know the answer to it..but, if noone can help you with this hardware issue, you might want to seek help at [LinuxQuestions.org]("http://www.linuxquestions.org/")

---

### Post by ilcontegis on 2009-03-10
> **ubuntu27 said:**
> I don't know the answer to it..but, if noone can help you with this hardware issue, you might want to seek help at [LinuxQuestions.org]("http://www.linuxquestions.org/")

nobody answers..
nobody has this card in the whole word? i am the only one :(

---

### Post by maligent on 2009-03-15
> **ilcontegis said:**
> nobody answers..
nobody has this card in the whole word? i am the only one :(

I don't think that it's so much nobody has it, as that nobody who does have this card has the microphone working (I'm one of them)

---

### Post by ilcontegis on 2009-03-15
> **maligent said:**
> I don't think that it's so much nobody has it, as that nobody who does have this card has the microphone working (I'm one of them)

auch....very bad.
If I buy an external mic will this one work?
thank you for the answer, at least now I know I am not alone

---

