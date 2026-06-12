---
title: "Sound ran away after update [2.6.24-24-generic]"
date: 2008-10-20
forum: Hardware
---

### Post by glethro on 2008-10-20
hey i just upgraded the new kernal and i have a huge sound issue....
There is none :P

when i first got this laptop (Acer 8920g) i had the same problem but i followed a tutorial and installed OSS 

but after the update i lost all sound :( so i tried the tutorial again and something didnt work, so i tried installing ALSA and that failed :P so i tried pulse audio.. and i still have nothing

so i have two questions.
1) how do i remove all the ALSA, OSS and pulse audio crap (id like a fresh start)

2) how do i fix the sound problem

thanks :D
(sound still works on vs 2.6.24-21-generic)

Sound INFO
>> aplay-l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

>>  cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc300000 irq 22

>> cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889
Codec: Generic 11c1 ID 1040

---

### Post by pwn2king on 2008-10-21
In a previous thread that now I can't find, lot's of peopele had the same problem. The new update fried the settings. The fix is to boot into the previous build, and set up the boot settings to automatically boot to the previous one. The problem is, I think I can muddle my way and do it manually on the boot up screen, but can someone give the instructions to modify the boot sequence? Thanks

---

