---
title: "[SOLVED] HOWTO:  Swap headphone and surround sound channels with Realtek alc882"
date: 2008-05-12
forum: Hardware
---

### Post by otrojake on 2008-05-12
I've been plagued with this problem since I started using Ubuntu back in the days of Edgy.  I'm no expert, but this is the knowledge I've gleaned from my year-long struggle to get my headphones, once plugged in, to mute the front speakers on my Asus z96fm.  This will only apply to those who have a Realtek alc882 chip for their Intel high definition audio chip.  Maybe this will help someone else out, since I haven't seen any topics addressing this particular issue anywhere on the forums or elsewhere.  

**Note**:  I've only tested this on Hardy with Alsa 1.0.16.

1)  To see what Realtek audio chip you have, type in ```
alsamixer
``` into a terminal.  Where it says chip, it should say what particular Realtek (or otherwise) chip you have.

2)  Edit your alsa-base file.```
sudo gedit /etc/modprobe.d/alsa-base
```  If you don't already have this line, add it in at the very bottom. > options snd-hda-intel model=mbp3  The mbp3 is the configuration for the MacBook Pro rev3, but thankfully Apple did the same thing as Asus did with switching the pins for the headphones and the surround channel.

3)  Reboot, and if necessary, enable the headphone switch by double-clicking on the sound applet in the top taskbar and then going to Edit>Preferences.  In my case the headphone switch is titled 'speaker', which is a little confusing but I'm not complaining, because it finally works.

My internal microphone still doesn't work, but that's a non-issue since I have a USB mic that works just fine.

And, of course, the [source of the information]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt") where you can find models for your specific chip.  It's a really valuable resource for troubleshooting sound.

If anyone has questions for me, don't hesitate to ask!:)

---

### Post by paxorius on 2008-05-12
Thanks!  My Asus Z96FM had same problem (same Realtek chip) and I was going nuts -- you saved my sanity and my allegiance to Ubuntu!

---

### Post by BlueSkyNIS on 2008-06-02
Hi otrojake, 

Do you know, or anyone else, how to enable High Definition sound e.g 192kHz/24bit? Current 44kHz/16bit sound sounds really awful :confused: :(

---

