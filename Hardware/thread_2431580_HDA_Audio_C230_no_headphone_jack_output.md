---
title: "HDA Audio C230 no headphone jack output"
date: 2019-11-18
forum: Hardware
---

### Post by docdoc2 on 2019-11-18
Hey peers,

I have the Realtek ALC668 in an Asus Rog Laptop. When inserting the Headphones the sound still comes out of the front speakers but no sound on the headphones. In Windows, when inserting the Headphones a Realtek HD Audio Manager pops up, and the sound will only be directed to the headphone jack after the user has told the prompt wether it is an headphone or loutspeakers. So i suppose this sound card needs to be switched by the OS somehow.

The sound card has also a line-out which could be used but it has a terrible high pitched noise - the switching workes in case though.

Do you have any idea how to make it work?

here is some more Info:
```
cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC668
```

```
cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xda128000 irq 141
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdc080000 irq 17
```

---

### Post by icegood on 2019-12-01
Hi. I have the very same issue with my ROG G752VL. And i wonder why audio output in ubuntu is mapped to port which purpose is input. Happens in both 18.04 and 19.10. See picture.

[IMG]https://i.imgur.com/CVRSd3A.png[/IMG]
Who knows how to remap it properly? 

P.S. My output is (almost the same as in topic starter):
```

ice@ice-ubuntu:~$ sudo dmidecode -s bios-version
G752VL.307
ice@ice-ubuntu:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC668
ice@ice-ubuntu:~$ cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xda128000 irq 139
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdc080000 irq 17

```

---

### Post by him610 on 2019-12-02
Have you tried adjusting the ins/outs using alsamixer? PulseAudio volume Control (PAVU)?

---

### Post by Yellow Pasque on 2019-12-03
You may have to play with hdajackretask (found in alsa-tools-gui). I'm sorry that I can't be more specific, but it usually involves some guessing and testing.

---

