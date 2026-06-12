---
title: "No sound from AMD 780g motherboard"
date: 2008-11-10
forum: Hardware
---

### Post by panfist on 2008-11-10
I just installed ubuntu 8.04 server 64 bit (I installed the ubuntu-desktop package, too), and have been unable to get any sound over HDMI or analog.

When I first installed I had the PC hooked up to my monitor via HDMI. Ubuntu did not detect restricted drivers for my motherboard, so I compiled fglrx drivers and now they do show up in the restricted driver manager, but I get no sound. I know that the HDMI connector works because when I dual boot into windows I get sound over HDMI fine. 

I have also tried connecting analog sound.

Using the gnome sound applet, from System > Preferences > Sound, no amount of fiddling with the options has resulted in any sound. Whether I choose HDMI, analog, digital, ALSA, OSS, PulseAudio, anything I cannot get any sound.

I tried to compile drivers from Realtek's website and I get a couple strange error messages, although it does compile all the way through. I noticed that I get some messages that it can't find /usr/lib64/libasound.so and /usr/lib64/libasound.so.2. This is strange because I have installed all libasound packages and I have libasound.so.2, but not libasound.so. Even though i have libasound.so.2, it says it can't be found.

Despite getting these messages, the driver just keeps building and then dumps me in alsaconf. I have done alsaconf at least 20 times choosing every permutation of option available, and I get no sound.

aplay shows three sound devices, which to my understanding is exactly what it should be showing.

When I boot the computer, during the boot process I can hear the speakers go from silent to hissing for a brief while when they are connected over analog. It sounds as though during the boot process the sound is initialized, but then before I get to GDM the hissing stops.

---

### Post by panfist on 2008-11-12
I was able to get some sound, but I'm still not having a lot of success.

By muting and unmuting the IEC958 device in the terminal, I was able to get some sound. I ran the following commands:

amixer -c 1 sset 'IEC958' mute
amixer -c 1 sset 'IEC958' unmute

Then I opened the sound preferences panel (System > Preferences > Sound) and when I tested my HDMI device, it worked. Success! However, all was not well.

I then tried to play a movie in Mplayer, and I was unsuccessful with OSS, ALSA, and pulseaudio. Then I tried to play the same file in the default ubuntu movie player, and again I had no sound.

I then tried to play some internet radio from RhythmBox player which worked, but the settings in RhythmBox don't really tell me a lot of information about which device it is using. I know Amarok gives you more close control over you playback devices, so I installed that too, but I haven't been able to get any sound out of Amarok.

I know that sound works now, and I'm pretty confident I can get it working in Mplayer, I just need to set the right options.

Any help would be appreciated.

---

