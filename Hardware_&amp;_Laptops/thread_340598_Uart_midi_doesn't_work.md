---
title: "Uart midi doesn't work"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by wistily on 2007-01-17
Hello.
I have been trying to make my midi keyboard to work on edgy, but i'm unable to.
I use it through the joystick port on my motherboard (ASUS P4P800, audio chipset Intel ICH5).
The midi port seems to be recognised by the system:

 ```
amidi -l

Device    Name
hw:1,0    MPU-401 UART MIDI
hw:2,0    Audigy MPU-401 (UART)
hw:2,1    Audigy MPU-401 #2
hw:2,2    Emu10k1 Synth MIDI (16 subdevices)
hw:2,3    Emu10k1 Synth MIDI (16 subdevices)

```

The correct port is the first (mpu-401 UART MIDI).
The problem is that when i try to connect something in jack, the connection disappears immediately.

Here seems to be the problem:

```
cat /dev/snd/midiC1D0 

cat: /dev/snd/midiC1D0: Erreur d'entrée/sortie

```
which is french for "i/o error".

The keyboard work correctly when i reboot under win, so this doesn't seem to be a hardware problem.

Thank you in advance for any help you can provide.

---

### Post by wistily on 2007-01-18
Bump

---

### Post by wistily on 2007-01-18
Bump

---

