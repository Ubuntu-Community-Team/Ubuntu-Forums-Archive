---
title: "[SOLVED] Advent 8212 Laptop Experience"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by moeFinley on 2008-01-06
I've just bought an Advent 8212 from PC World and installed Ubuntu on it.  I thought I'd share my experience for those who might be about to or already have done the same thing.

I'd highly recommend the laptop to anyone.  Although the speakers are terrible - really bad - the rest of the machine is bargain.

In Ubuntu the graphics card has not been picked up so I don't have 3D and the sound does not switch off the main speakers when the headphones are plugged in.  Both are to do with the limited support for Intel chipset.  Installing Fedora Core 8 got me 3D on the graphics card but nothing seemed to get the audio fixed.

I don't want to use vista :(

Here's a screenshot of my volume control.  Why do I have a 'Headphones' volume control that does nothing?  Front and PCM control both the speakers and headphones.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=55589&stc=1&d=1199719498[/IMG]

What normally controls the disabling of the main speakers?  I always figured it was a hardware thing.

---

### Post by Vadi on 2008-01-06
Have you tried installing resticted drivers?

Though I have no idea how to Intel graphics card work here.

---

### Post by Lord Illidan on 2008-01-06
Hardware wise, I guess it's similar to the specs here : [http://www.pcpro.co.uk/labs/128726/advent-8212.html](http://www.pcpro.co.uk/labs/128726/advent-8212.html)

right?

---

### Post by moeFinley on 2008-01-06
> **Lord Illidan said:**
> Hardware wise, I guess it's similar to the specs here : [http://www.pcpro.co.uk/labs/128726/advent-8212.html](http://www.pcpro.co.uk/labs/128726/advent-8212.html)

right?

Yes that is exactly the same laptop.  The motherboard chipset is an Intel Crestline GM965 + ICH8M and it uses the onboard grpahics card and sound.

I've not tried restricted drivers before for anything but networking.  Would that would for sound or video?

---

### Post by Vadi on 2008-01-06
Video

---

### Post by moeFinley on 2008-01-06
When I open the restricted drivers manager it states that none of my hardware needs restricted drivers and then closes.

---

### Post by moeFinley on 2008-01-07
I updated some of the details above.  I installed Hardy Heron today to see if it would make any difference.  It didn't :(

I really don't want to use Vista.  I've been using Ubuntu for over a year now and there's so much I would miss.  It's annoying that something so simple makes the laptop unusable if I anywhere public.  I wouldn't mind if I just had to manually mute the speakers!

---

### Post by moeFinley on 2008-01-07
> **virtuoso said:**
> wiered... my Compaq laptop's controls work great.
even my quick launch buttons work wil visual as well as audio alerts!!

Does your Compaq have the same chipset?  Mine is revision three if that makes any difference.
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

---

### Post by moeFinley on 2008-01-07
The following comes from the [ALSA change logs]("http://www.alsa-project.org/main/index.php/Changes_v1.0.14rc4_v1.0.14").  Can someone tell me what non-eapd means?

```
HDA: Fix headphone mute issue on non-eapd Conexant systems
```

Thanks for all the help so far.

---

### Post by moeFinley on 2008-01-07
WAHOOO! Solved thanks to [this post]("http://ubuntuforums.org/showthread.php?t=616845&highlight=ALC883").

I came across lots of post that suggest the line ```
options snd-hda-intel model=3stack
``` but this didn't work for me.  It seems that is just one of hundreds of options.  For me the following worked best ```
options snd-hda-intel model=acer-aspire
``` but I am only half way through the list so there maybe a better one.  This option doesn't give me automatic switching, just an toggle in the volume settings.  But I'm happy with that! :)

---

### Post by holnrew on 2008-05-14
I have the same laptop. Haven't tried the headphone socket in Ubuntu yet.

Did you have any issues with the wireless?

---

### Post by moeFinley on 2008-05-15
Not with Unbuntu but I did have trouble with some other distros.  Have you got a problem with the wireless in Ubuntu?

---

