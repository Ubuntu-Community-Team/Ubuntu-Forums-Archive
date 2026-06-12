---
title: "No sound from external jack-plug speakers!"
date: 2009-09-01
forum: Hardware
---

### Post by Oestergaard on 2009-09-01
My first post in here, and I'm complaining because I'm such a noob in Ubuntu I guess.. well, here goes:

I installed Ubuntu 9.04 on my Acer Aspire 5738ZG some while ago, because i got fed up with Windows Vista.. (and decided to install my old Windows XP along with this interesting open source project). I succeeded in installing a graphics driver for my nVIDIA GeForce g105m, but my great luck in getting the hardware to work with Ubuntu stopped there. I can't get the sound to work (in what i plug in to my laptop with a jack!) 

The thing is that my internal speakers work fine, so no doubt that my sound card has a fine driver to mate with. I've browsed through several fora before getting as far as creating one in here. I see that a lot of people has issues with their sound in ubuntu like i have, but none really with the exact same as i have. I have downloaded the newest ALSA upgrade script, run it and installed what it had. Still, i can't make my laptop playing good music through the external speakers.
It seems that people have been able to solve their problems simply by enabling Headset in the Mixer preferences, or whatever, but won't work for me. I don't even have the option to manage a headset in there.

I know - i'm a noob - but I would be grateful and feel as if I had gotten help from the Lord himself, if somebody could help me with making my external jack speakers work. i' not really satisfied with the bass in the internal ones ;)
Here's what the terminal would let me now about my sound hardware:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thank you.

---

### Post by tnek on 2009-09-01
I have a HDA Intel chipset too. I use Xubuntu but you can find the mixer in Ubuntu and Kubuntu too, I guess, look around in the menus:

[http://tsnippets.tumblr.com/post/168966221/xubuntu-ich7-sound](http://tsnippets.tumblr.com/post/168966221/xubuntu-ich7-sound)

Tell me if it works.

---

### Post by tgeer43 on 2009-09-02
> It seems that people have been able to solve their problems simply by enabling Headset in the Mixer preferences, or whatever, but won't work for me. I don't even have the option to manage a headset in there.It might just be that the Headphone channel is not set to be visible in the Volume Control window. Go back into the volume control and select 'Preferences'. Make sure that everything is selected.

tgeer

---

### Post by Oestergaard on 2009-09-02
I found a sollution. In my frustration i checked all the options that could be checked in mixer preferences, and found out that Front speaker had to be muted (mutes the internal laptop speakers) and the Surround speaker unmuted. Aparrently Ubuntu counts the speakers as being a Surround sound device. To have downloaded the upgraded ALSA script may have helped as well. not sure if changing the Surround speaker settings before i ran the AlsaUpgrade-1.0.x-rev-1.17.sh script made any changes, so that may have been the trigger.

Even though this is very simple, this might help others, as I haven't seen a sollution like this anywhere on the web. Thank you for yours responds!

---

