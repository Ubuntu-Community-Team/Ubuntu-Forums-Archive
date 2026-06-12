---
title: "ICE1712 Module does not detect Delta 66 sound card"
date: 2008-10-16
forum: Hardware
---

### Post by Tom Mann on 2008-10-16
Hi Guys,

I have recently acquired a Delta 66 sound card for my PC, with the hope of using it's multi-recording facility. However, with the modules loaded (snd_ice1712) the card is not detected by Alsa, and refuses to function.

I am running the 64 bit version of Ubuntu, so would like to know if anyone has a new (revision E) Delta 66 working on 32 bit Ubuntu, or if anyone else is suffering from the same problem.

DMesg shows that the card fails to initialise, so I have filed a bug [here]("https://bugs.launchpad.net/ubuntu/+bug/280847").

Any help would be greatly appreciated.

Thanks,
T

---

### Post by Tom Mann on 2008-10-21
To add to this - in Intrepid the ALSA module fails to install via module assistant:
(sudo)
m-a update
m-a a-i alsa

gives me:
   CC [M]  /usr/src/modules/alsa-driver/acore/info.o
 /usr/src/modules/alsa-driver/acore/info.c: In function
 &#8216;resize_info_buffer&#8217;:
 /usr/src/modules/alsa-driver/acore/info.c:90: error: implicit
 declaration of function &#8216;PAGE_ALIGN&#8217;
 make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
 make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
 make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
 make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic' 
 make[2]: *** [compile] Error 2
 make[2]: Leaving directory `/usr/src/modules/alsa-driver' 
 make[1]: *** [build-stamp] Error 2
 make[1]: Leaving directory `/usr/src/modules/alsa-driver'
 make: *** [kdist_image] Error 2

---

### Post by Tom Mann on 2008-10-23
Fixed - by adding a line to /etc/modprobe.d/alsa-base

options snd-ice1712 model=delta1010lt


I also added snd-hda-intel to /etc/modprobe.d/blacklist to prevent ATI HDMI sound from loading in.

---

