---
title: "Speakers don't mute when headphones plug in.  Help please!"
date: 2010-09-04
forum: Hardware
---

### Post by Horrendus01 on 2010-09-04
I have an HP Pavilion dv7 Laptop. Model #: dv7-3065dx

The problem I am having is that when I plug in my headphones, I get sound out of the speakers as well as the headphones.  The speakers do not mute as they should.  I have looked around and have seen others have had this problem, and have fixed it using a workaround that adds options to the alsa mixer.  Unfortunately I am a bit of an Ubuntu noob, and I was hoping someone could explain to me how to fix this.  I have used Ubuntu before, and have been able to fix some issues myself, but this has been bugging me for quite some time so anyone who could explain how to fix it would be very helpful.  Thanks

If you need other info, let me know.

```
cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf2400000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf2310000 irq 19
 2 [U0x46d0x809    ]: USB-Audio - USB Device 0x46d:0x809
                      USB Device 0x46d:0x809 at usb-0000:00:12.2-1, high speed

```

```
head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

```

---

### Post by Horrendus01 on 2010-09-05
Does anyone have a solution to this?  I was hoping to get it done since I use Mangler, and it is not good to have speakers on when talking to people like that, as they get feedback from my speakers and hear themselves talking.  Being a laptop, the internal speakers come through extremely loud over mic to them, and it is very irritating.  If it helps, I am running Ubuntu 10.04 brand new install just done today, and the only thing I have installed on it are Mangler and xscreensaver.  I would really appreciate any help on this.  Thanks

---

### Post by Horrendus01 on 2010-09-05
It's been 12 hours and no response?  Does nobody know anything about this issue?  I could really use the help...

---

### Post by IcarusR on 2010-09-05
I suggest you search the forum as this topic keeps re-occurring, so should be some useful info.

---

### Post by Horrendus01 on 2010-09-06
I have searched the forums.  I found a fix to it, but that fix broke my sound coming from firefox.  I have since commented out the line that stops my sound card from loading as device 0 in the configuration file, but now I am having the same issue again with the headphones.  The previous fix had my card loading in as device 2, but it needs to load as device 0 to have sound coming from sources like firefox.

---

