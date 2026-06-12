---
title: "No surround sound onboard option when Nvidia card installed"
date: 2019-10-28
forum: Hardware
---

### Post by tekkerz on 2019-10-28
I am trying to get 7.1 sound via my Asus P8H67-M onboard HDMI port (to connect it directly to my soundbar), but when my Nvidia Geforce 1030 video card is connected also by HDMI the 7.1 profile doesn't show up on my onboard port. 

When I choose the onboard device as the default output device (using the Digital Stereo profile option), I can see sound being outputted via pavucontrol but I can't actually hear anything via my Soundbar (directly connected to PC)

[B]Screenshots: 
[/B]
[No 7.1 option on onboard HDMI]("https://i.stack.imgur.com/bgSq0.jpg")

[Limited onboard profiles for onboard port when Nvidia card also connected]("https://i.stack.imgur.com/Y8SzP.jpg")


When the Nvidia card is disconnected the onboard port plays 7.1 sound perfectly fine (tested using a Dolby 7.1 test video)

[7.1 option available on onboard HDMI when graphics card disconnected]("https://i.stack.imgur.com/tYpLq.png")


Should it be possible to have 7.1 support available on both devices? I know both support them, but it appears Ubuntu is allowing the graphics card to output 7.1 only when it's connected.

---

### Post by wildmanne39 on 2019-10-28
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by tekkerz on 2019-10-29
> **wildmanne39 said:**
> Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

I bolded some text - is that a no-no?

---

### Post by wildmanne39 on 2019-10-29
You made all the text lighter which makes it harder to read, that is what I was referring to, if you want to bold a small portion of text to draw attention to it that is fine, I just used the quick way to fix that much font issues by removing all formatting with one click.

---

### Post by tekkerz on 2019-10-29
> **wildmanne39 said:**
> You made all the text lighter which makes it harder to read, that is what I was referring to, if you want to bold a small portion of text to draw attention to it that is fine, I just used the quick way to fix that much font issues by removing all formatting with one click.

Ah thank you. I wasn't aware the text was not default. 

Now hopefully it's more readable and someone can help me out :)

---

### Post by CatKiller on 2019-10-29
> **tekkerz said:**
> Should it be possible to have 7.1 support available on both devices? I know both support them, but it appears Ubuntu is allowing the graphics card to output 7.1 only when it's connected.

It should *be* possible. My sound configuration has available 7.1 from my Nvidia card, 5.1 from my onboard sound, and stereo duplex for the external sound card that I actually use. However, each motherboard has its quirks, particularly around onboard sound, and the nvidia driver has quirks all of its own.

I do notice from your screenshots that it's always HDMI2 that has 7.1 available - even when you only actually have one HDMI port - maybe there's some name collision there?

Another thing to look at would be to check dmesg to see if there is a difference in how the onboard sound is identified when you have the graphics card installed and when you don't. ALSA - which handles the hardware layer - makes its best guess at which of the myriad of available onboard sound quirks apply during the hardware detection stage, and then passes those results on to PulseAudio for the signal routing layer. You might only need to specify a couple of parameters to help out with that step. Otherwise, it's possible to give a full manual channel map, but that way madness lies.

---

### Post by tekkerz on 2019-10-29
> **CatKiller said:**
> I do notice from your screenshots that it's always HDMI2 that has 7.1 available - even when you only actually have one HDMI port - maybe there's some name collision there?

I do have two HDMI ports though - one on the Nvivisa and an onboard. Perhaps the HDMI2 (onboard?) port is being incorrectly assigned to the Nvidia card? How would I go about sorting any naming collisions out?

> **CatKiller said:**
> 
Another thing to look at would be to check dmesg to see if there is a difference in how the onboard sound is identified when you have the graphics card installed and when you don't. ALSA - which handles the hardware layer - makes its best guess at which of the myriad of available onboard sound quirks apply during the hardware detection stage, and then passes those results on to PulseAudio for the signal routing layer. You might only need to specify a couple of parameters to help out with that step. Otherwise, it's possible to give a full manual channel map, but that way madness lies.

[IMG]https://imgur.com/a/ujnZsn5[/IMG]
[IMG]https://imgur.com/a/ujnZsn5[/IMG]Does my Alsamixer look odd to you also? Why are there no channels and only SPDIF? [https://imgur.com/a/ujnZsn5](https://imgur.com/a/ujnZsn5)

---

