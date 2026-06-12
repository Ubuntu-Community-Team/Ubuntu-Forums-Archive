---
title: "Sound not working on Sony Vaio VGN-X505ZP (X505)"
date: 2009-01-17
forum: Hardware
---

### Post by nyvaerld on 2009-01-17
Hello,

I have installed Ubuntu on my Sony Vaio VGN-X505ZP.  So far everything works perfectly, except for sound.  There is no sound at all.  However, alsamixer "sees" the sound chip and I can even change volumes.
Alsamixer finds this:
Card: Intel 82801DB-ICH4
Chip: Analog Devices AD1981B

If anyone has a tip or solution, I'd be very grateful :)

---

### Post by linux_tech on 2009-01-17
Pls check post output of ```
aplay -l
```
and 
```
cat /proc/asound/card0/codec#* | grep Codec
 
```

---

### Post by nyvaerld on 2009-01-21
aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

There is a folder named
/proc/asound/card0/codec97#0/

Thanks in advance :)

---

### Post by imilnes on 2011-03-31
I have a VGN-X505VP that outputs sound only when headphones are plugged in.
 
I'd guess the current driver set aren't detecting the headphone switch correctly?
 
This is common across a variety of ubuntu distributions.
 
I've seen this from 9.10 to 10.10 (May have been earlier too)
 
This is a driver issue as the windows drivers are fine (I dual-boot)

---

### Post by lidex on 2011-04-03
> **imilnes said:**
> I have a VGN-X505VP that outputs sound only when headphones are plugged in.
 
I'd guess the current driver set aren't detecting the headphone switch correctly?
 
This is common across a variety of ubuntu distributions.
 
I've seen this from 9.10 to 10.10 (May have been earlier too)
 
This is a driver issue as the windows drivers are fine (I dual-boot)

Please stop waking up ancient threads. If you have a problem, create your own thread. thankyou

---

