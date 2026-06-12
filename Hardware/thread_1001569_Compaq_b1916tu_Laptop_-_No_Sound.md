---
title: "Compaq b1916tu Laptop - No Sound"
date: 2008-12-04
forum: Hardware
---

### Post by fordfan753 on 2008-12-04
Hi everyone,

I have had this laptop (Presario b1916tu) for a couple of years now, running different versions of Ubuntu and Debian. I have never been able to get sound out of it.

If I get alsa-driver from the alsa-project site, and compile that with debug support I am able to get sound out of the MICROPHONE jack by adding the line
```
options snd-hda-intel model=test
```
to /etc/modprobe.d/alsa-base.

I have scoured the internet since I've had the laptop, but have never been able to get past this stage.

Ideally I'd like to have sound using the internal speakers, and also through the headphone jack.

Details as are follows...

```
lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0500000 irq 16
```


Let me know if there are any other commands I can run to give people more information.

Also, I _have_ checked all volumes, mutes, and switches before posting.

All other hardware on this laptop besides the modem (which is not necessary) is detected and works fine, including wireless, bluetooth, and ATI graphics.

Thankyou for your time.

---

### Post by sandlidl on 2008-12-06
Hello, I recently ran into the same problem on a Compaq Presario b1900 laptop with Realtek alc260 soundcard.

Though I don't have a fix, I do have a workaround. It doesn't get the speakers going, but it gives headphones and microphone.

edit alsa-base:

sudo nano /etc/modprobe.d/alsa-base

at the bottom, type in:

options snd-hda-intel model=will

save and reboot

open the sound mixer and change it to whatever sounds the best.

Hope this helps for the time being.

---

### Post by fordfan753 on 2008-12-06
Thankyou very much for your workaround, this worked well for me also. While this still does not give me sound from my internal speakers, it does give me much better quality sound than before. Also it means I won't have to compile alsa-driver all the time. :)

---

