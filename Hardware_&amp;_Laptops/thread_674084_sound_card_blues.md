---
title: "sound card blues"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by schnitz17 on 2008-01-21
ok so i recently installed ubuntu and everything is running smooth.....except i gots no sound....i have a emachines W3118 and the driver for it is realteck AC 97....any suggestions?
thanks in adavance

---

### Post by texasjim on 2008-03-15
SCHNITZ17
   I feel your pain.  Just bought the k8mc51g with amd 3100+ for $50US at goodwill.  Works like a champ except I gots no sound either. I have been installin, pushin buttons. flippin switches, uninstallin, reading posts everywhere but no joy.
  Beginning to believe it's a driver problem or NVIDIA BIOS, still reluctant to go there as there is at best an "unofficial" E-machine site, but the FIC web site looks ok. I just found out my model from your post.  Will come back here when I figure it out.
  Jim

---

### Post by Yellow Pasque on 2008-03-15
Try OSS4 (see my sig for link)

---

### Post by texasjim on 2008-03-15
Temujin,
Thanks for the quick reply. Followed by-the-numbers, everything went ok, did the gnome 
volume-control patch but still no joy.  Here is ossdetect and ossinfo:

studio@studio:~$ sudo ossdetect -v
[sudo] password for studio:
Detected Nvidia MCP51
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
studio@studio:~$ ossinfo
Version info: OSS 4.0 (b1014/200802280648) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 (studio)

Number of audio devices:        2
Number of audio engines:        11
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 Nvidia MCP51 interrupts=28714 (28714)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: ICH AC97 Mixer (ALC655) (Mixer 0 of device object 1)

Audio devices
Nvidia MCP51                      /dev/oss/ich0/pcm0  (device index 0)
Nvidia MCP51 S/PDIF out           /dev/oss/ich0/spdout  (device index 1)
studio@studio:~$ 

May be back to hardware or BIOS, I'm leaning toward the latter even if I'm kinda
wimpy on the idea.

    Jim

---

### Post by texasjim on 2008-03-16
OK, Either I'm dumber than I look or the audio plugs on the backpanel are mislabeled:
One blue jack in a blue panel labeled ((<))--- which I mistook for Line in.
One green jack in a green panel labeled ((-))--> which I foolisly assumed was Line out.

NOPE - Put the out plug in the in jack and played test tone.
            Put the in plug in the out jack and my wintv played thru the speakers.

---

### Post by texasjim on 2008-04-03
OK, Maybe I'm not quite as dumb as I look after all.  The OSS sound was pretty bad, so out
of desperation I installed winxpsp2pro... No sound. Then installed the Nvidia ac97 drivers
 from Nvidia web site. All installed OK but... No sound.   In monkeying around with the
 Nvidia configuration tool I discovered that the BLUE (middle) jack is switchable between LINE IN
 and REAR SPEAKER OUT !?!?!?

  Is it possible the OSS driver is configured in this manner?

 Still no sound, but maybe a haircut will make me look smarter.

  Think I'm gonna get either a USB sound adapter or the new SoundBlaster PCI-E for that little bitty slot.

 Still may be hardware.

  Jim #-o

Between the last post and this one I installed Hardy Beta to see if any better.  Nope.

---

