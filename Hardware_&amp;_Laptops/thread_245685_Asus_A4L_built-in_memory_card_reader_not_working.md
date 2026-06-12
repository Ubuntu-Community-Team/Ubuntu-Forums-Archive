---
title: "Asus A4L built-in memory card reader not working"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by plasmafusion on 2006-08-28
hey all :)
running dapper with all updates and have recently updated to the 2.6.17.7 kernel.

the idea was that i'd heard it supported the sd card reader that's built into my asus a4l notebook. i compiled all the usb modules and everything else that i thought was related but i've still got no joy with it.

anybody had an success with this? it's the only thing stopping me from using linux exclusively...

cheers

---

### Post by plasmafusion on 2006-11-19
sorry for bumping this one up but i've still had no joy getting this working...help!! :)

---

### Post by 56phil on 2006-11-19
I had the same problem on my Gateway M680.

Here's how to fix it:
```

sudo modprobe tifm_core
sudo modprobe tifm_sd

```
Then put that same code, without, the sudo, in your /etc/modules file.

Happy Ubuntu.

---

### Post by plasmafusion on 2006-11-19
hey :) thanks for replying.
that worked a treat.
thanks a lot for the info

---

### Post by ampop on 2006-12-28
I have the same problem on a Acer laptop. After doing:
```
sudo modprobe tifm_core
sudo modprobe tifm_sd
```
I can see the memory card:
```
ampop@acer-laptop:~$ dmesg
[17181307.332000] tifm_7xx1: ms card detected in socket 0
```
But I haven't any /dev/sd*
```
ampop@acer-laptop:~$ ls /dev/s*
/dev/sequencer   /dev/snapshot  /dev/stderr  /dev/stdout
/dev/sequencer2  /dev/sndstat   /dev/stdin

/dev/shm:

/dev/snd:
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D6c  pcmC0D6p  seq  timer
```
Any Idea how to mount the card? Thank you.

---

