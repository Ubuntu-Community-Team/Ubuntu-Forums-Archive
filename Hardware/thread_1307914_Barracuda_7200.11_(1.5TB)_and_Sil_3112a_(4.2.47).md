---
title: "Barracuda 7200.11 (1.5TB) and Sil 3112a (4.2.47)"
date: 2009-10-31
forum: Hardware
---

### Post by DJTurboToJo on 2009-10-31
Hello Community,

I just bought a new Seagate Barracuda ST31500341AS and I planned to put this into my old desktop computer. Unfortunately the system boots only until the SATA controller checks for some sata hard drives and simply stops doing anything after showing at least the name of the new hard drive. Here some more tech details:

motherboard: ASUS A7N8x Deluxe (Board Rev. 1.04), BIOS Rev. 1008
sata controller (onboard): Silicon Image Sil 3112A (BIOS Version 4.2.27)

1. sata controller is 150MB/s
2. sata hard drive is 300MB/s
=> could this be the problem?

I read ([http://www.seagate.com/staticfiles/support/disc/manuals/desktop/Barracuda%207200.11/100507013e.pdf](http://www.seagate.com/staticfiles/support/disc/manuals/desktop/Barracuda%207200.11/100507013e.pdf)) on the internet that it's possible to set a jumper for 300 disk to limit it to 150 in order to work with older controllers. However in the manual above the ST31500341AS is not mentioned to have this feature but my drive has four pins where I can set a jumper. I tried this but no luck.

I also read that sata drives are always downgradable. What do you guys think: is it the size that is limited by the BIOS or is it the speed that bothering my controller?

Is it possible to update only the sata controller? I do have the latest BIOS updates for the mainboard but this is really old as I have the first board revision and Asus has some newer updates but not for my board :(. 

So I dont know what the problem is... Any help or some suggestions what I could do to save my day?

THANKS
DJTurboToJo

---

### Post by DJTurboToJo on 2009-10-31
Sorry, if this was the wrong forum.

Anyway I could solve it:

I downloaded the newest BIOS (beta 1009) => it didnt work as the SATA was still the same. So I created my own BIOS I took the 1009 version and downloaded the newest one from Silicon Image. And changed the BIOS using cbrom (in windows - shame on me -).

this might help anybody else have this problem:
[http://www.nforcershq.com/forum/a7n8x-deluxe-pcb-revision-1-04-1-06-with-sata-rom-4279-t68207.html](http://www.nforcershq.com/forum/a7n8x-deluxe-pcb-revision-1-04-1-06-with-sata-rom-4279-t68207.html)

---

### Post by viper250 on 2009-10-31
the thing is you found a fix and posted it here on the forum this is a valuable addition of info to the forum thank you very much.

---

