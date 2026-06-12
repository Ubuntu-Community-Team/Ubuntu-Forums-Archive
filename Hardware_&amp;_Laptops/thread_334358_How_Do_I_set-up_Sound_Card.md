---
title: "How Do I set-up Sound Card"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by tjb_15 on 2007-01-08
How do I set up a Creative Sound Blaster X-fi Xtreme audio Sound card. I have no clue were to start.

---

### Post by Quillz on 2007-01-09
I have the same sound card on my desktop, and it wasn't recognized by Ubuntu, either.

---

### Post by Pjotr123 on 2007-01-09
Run alsaconf?

[http://ubuntuforums.org/showthread.php?t=330454&highlight=alsaconf](http://ubuntuforums.org/showthread.php?t=330454&highlight=alsaconf)

Greeting, Pjotr.

---

### Post by tjb_15 on 2007-01-09
> **Pjotr123 said:**
> Run alsaconf?

[http://ubuntuforums.org/showthread.php?t=330454&highlight=alsaconf](http://ubuntuforums.org/showthread.php?t=330454&highlight=alsaconf)

Greeting, Pjotr.

Ok I did that but I still got no sound ](*,)

---

### Post by Quillz on 2007-01-09
> **tjb_15 said:**
> Ok I did that but I still got no sound ](*,)
Same here. My card was recognized and supposedly configured, and no dice.

---

### Post by Jaygo333 on 2007-01-10
Same here.
Tried to install but no sound.
How do check that it was installed ?

 I tried
jaygo333@edgy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jaygo333@edgy:~$ 

P.S. I also have a Soundblaster Xtreme Audio thingie.

---

### Post by tjb_15 on 2007-01-11
Any one?  ](*,)

---

### Post by tjb_15 on 2007-01-13
Please? :D

---

### Post by np2 on 2007-01-14
[http://opensource.creative.com/]("http://opensource.creative.com/")

Which means, wait and pray like the rest of us, or buy a new card :p  ALSA doesn't support X-Fi

"Sound Blaster X-Fi  	UNKNOWN  	  	 [X-]
Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time."

From ALSA's sound card compatibility list

---

### Post by tjb_15 on 2007-01-14
> **np2 said:**
> [http://opensource.creative.com/]("http://opensource.creative.com/")

Which means, wait and pray like the rest of us, or buy a new card :p  ALSA doesn't support X-Fi

"Sound Blaster X-Fi  	UNKNOWN  	  	 [X-]
Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time."

From ALSA's sound card compatibility listI Just got this card for christmas. I guess ubuntu is going to have to wait. Got to have music;)

---

### Post by didobuntu on 2007-01-17
> **Jaygo333 said:**
> Same here.
Tried to install but no sound.
How do check that it was installed ?

 I tried
jaygo333@edgy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jaygo333@edgy:~$ 

P.S. I also have a Soundblaster Xtreme Audio thingie.


Hello,
This sound chipset, e.g. ALC882 poses many problems with alsa. For laptops, it only runs on some Acer laptops, and not for asus such like asus w2jc.
On desktops, some configs make it run well as I saw in many forums.

---

### Post by tjb_15 on 2007-03-02
It's been a while has any one figured it out?

---

### Post by gwoodard on 2007-03-02
Okay have You done all the updates? If so you should check out the volume control (Speaker near power off icon) go to it right click it and select volume control, go to file, go to change device and make sure there isnt anything muted, disabled, or turned off.

---

### Post by tjb_15 on 2007-03-03
> **gwoodard said:**
> Okay have You done all the updates? If so you should check out the volume control (Speaker near power off icon) go to it right click it and select volume control, go to file, go to change device and make sure there isnt anything muted, disabled, or turned off.I just updated it and there isn't any thing disabled

---

### Post by christhemonkey on 2007-03-03
See here:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

> Card: Sound Blaster X-Fi
Chipset: UNKNOWN
Driver and Docs: None
Notes: [X-] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.


---

