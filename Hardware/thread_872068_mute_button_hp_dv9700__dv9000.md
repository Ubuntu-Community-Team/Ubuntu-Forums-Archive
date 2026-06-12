---
title: "mute button hp dv9700 / dv9000"
date: 2008-07-27
forum: Hardware
---

### Post by wardy277 on 2008-07-27
hello i have a hp dv9700. So far pretty good. there is one strange thing that has been bugging me for a while now.

when i am watching a video on vlc with headphones, sound comes out of headphones and not speakers. when the mute is pressed (on the laptop physically or in the sound preferences software) and then unmuted, the sound plays through my headphones as before but also on the main speakers. this has been quite enoying. especially when my girlfriend is trying to concentrate on an essay!!

Also when muted in windows the mute button turns orange but stays blue in Ubuntu. could this be related?

any help would be greatly appreciated.

(running ubuntu hardy with compiz)

Chris

---

### Post by jmesmon on 2008-08-03
In order to get sound only on the headphones when they are plugged in open up alsamixer and mute the "Front Speakers" while setting the "Headphones" at 100%. 

This for some reason causes the desired behavior: when headphones are plugged it plays over them and not speakers, and when headphones are unplugged sound plays over the speakers.

As for the color of the mute button, this is an unrelated but important issue. In windows, when muted the sound card is unpowered, which causes the color to change to orange as well as possible power savings. Linux does not currently function that well, unfortunately. You might be able to achieve the power-down of the card some how (rmmod the module, or through alsa in some strange way) but don't expect anyone to know how. This is something that'll take quite a bit of manual reading and searching, and probably source code reading as well. I have the same laptop, so I'll have my eyes open, but don't expect fast results.

---

### Post by wardy277 on 2008-08-05
Ah, thanx for that. i think i understand it now.

chris

---

### Post by doas777 on 2008-08-05
> **wardy277 said:**
> hello i have a hp dv9700. So far pretty good. there is one strange thing that has been bugging me for a while now.

when i am watching a video on vlc with headphones, sound comes out of headphones and not speakers. when the mute is pressed (on the laptop physically or in the sound preferences software) and then unmuted, the sound plays through my headphones as before but also on the main speakers. this has been quite enoying. especially when my girlfriend is trying to concentrate on an essay!!

Also when muted in windows the mute button turns orange but stays blue in Ubuntu. could this be related?

any help would be greatly appreciated.

(running ubuntu hardy with compiz)

Chris

My dv9205 and dv98xx both turn orange when tapping the mute button straight out of the box. I'm afraid i can't help there, but it does work for me. i don't use headphones often, so I don't know if I have the same issue in terms of sound channels.

good luck.

---

### Post by jmesmon on 2008-08-07
that is interesting that yours turn orange. could you tell me the chipset and driver of your sound card? it may be different from the one we are having issues with, thus indicating that a driver modification may be needed.

---

### Post by doas777 on 2008-08-09
> **jmesmon said:**
> that is interesting that yours turn orange. could you tell me the chipset and driver of your sound card? it may be different from the one we are having issues with, thus indicating that a driver modification may be needed.

Here is my lshw output (made with lshw-gtk) from my 9810us. the 9205 got rebuilt with <cough> another OS <cough> recently when I loaned it to my roommate, but it had worked correctly for me up until then. 

hope that helps. LMK if you need anything else.

have fun,
franklin

---

### Post by jordanp on 2008-10-31
I'm having the exact same problem as the Original Poster - only difference is, mine was working great out of box (mostly) - mute turned the button orange, and it didn't cause signal to bounce between built-in and external speakers - but now has suddenly ceased to work right, and is now behaving as the OP stated.  Big problem, obviously.

Really could use some help here; one of my machine's main values is as a DJ-ing platform, and it being unreliable with audio is a huge problem.

I installed ALPAMixergui and did what jmesmon suggested, and that's fixed one problem (to be more specific, the program you need to have is the GNOME ASLA Mixer).  But Mute still doesn't turn orange.

Also, none of my touch buttons for play/pause, next, previous, and stop seem to do anything, at all.  Frustrating.  Yes, I went to keyboard shortcuts, cleared them, and reset them.

Thanks for any help!

---

### Post by sa_dan on 2008-11-13
I had the same problem with my mute button on my main user after upgrading to Intrepid from Hardy. Logging in as Guest, the button would work, no problem.

Fixed it by going to System -> Preferences -> Keyboard Shortcuts. Select the 'Volume Mute' entry and press the Mute button.

---

