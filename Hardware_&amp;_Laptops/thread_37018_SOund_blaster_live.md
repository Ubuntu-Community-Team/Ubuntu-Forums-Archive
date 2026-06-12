---
title: "SOund blaster live"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by DaGGer on 2005-05-25
ok well i have put it in and then i look in the device manager and it sees the card but it won't use it....it is using the wrong sound...i have onboard and its using that right now...please some one help...i just got the sound card and i want it to work

---

### Post by jkndrkn on 2005-05-25
Have you tried setting up alsa? If not, check out the following links:

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}
```


Notice:

```
pcm "hw:0,0"
```

Change the 0,0 to point to your new soundcard.

Good luck.

---

### Post by DaGGer on 2005-05-25
ok well i havn't tried to change anything...but i can changesthe stuff to alsa....also i htink that i may try to turn off the onboard sound card in my bios...maybe this will help

---

### Post by DaGGer on 2005-05-25
i did that but the thing is that it still doesn't work..ubuntu is still using the onboard card and i need to change it so it uses the sound blaster card

---

### Post by DaGGer on 2005-05-25
when you say change 0.0 to the new sound card what do you mean...put the name of the card or what

---

