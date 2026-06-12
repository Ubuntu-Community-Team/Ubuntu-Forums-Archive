---
title: "no sound on Samsung M50"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by ramiro on 2006-02-26
Hey, I've been using Ubuntu Breezy on my new Samsung M50 laptop and have had no success getting sound to work. I just updated to Dapper flight 4 to see if that had any better luck (and to have a look at glx) and no success with sound.

the card appears to have been detected as HDA Intel chipset with Analog Devices AD1986A Codec.

Windows device manager shows "SoundMAX Integrated Digital HD Audio". 

I made sure the volume was up in alsamixer and also in gnome's volume control. I also tried changing the permissions on /dev/dsp with no luck.

here are some specs on the [Samsung M50]("http://www.cybershop.net.au/Notebooks/samM50.shtml") which I am using. It shows:

SOUND/SPEAKERS: Azalia High Definition Audio & AC '97 2.3 compliant CODEC with Twin Speakers

any ideas?

---

### Post by ramiro on 2006-02-27
ok, now sound has randomly started to work so long as I select Analog Devices sound in volume controls, however, recently while it plays sound the speaker emits a very high pitched noise which is loud and quite rritating.

It only does this in linux and not windows, and when sound first started working, it didn't do it at all, only just started doing it when I unplugged the laptop from the power. Now it's all plugged in and it's still doing it.

It's driving me crazy! anyone have any ideas?

---

### Post by dhalgren on 2006-02-27
hi, have a look at [http://ubuntuforums.org/showthread.php?t=76307]("http://ubuntuforums.org/showthread.php?t=76307")
It may be relevant, or it may not. It certainly solved my problems with snd-hda-intel.  Just make sure you have a realtek sound card and change those bits that need changing, i.,e the model of your computer, and stuff like that.

I really don't know if this will help, but it's a beginning. I had to mess with many different ways to try and fix the problem, but with persistance, I finally got there and have sound.

Good luck

---

