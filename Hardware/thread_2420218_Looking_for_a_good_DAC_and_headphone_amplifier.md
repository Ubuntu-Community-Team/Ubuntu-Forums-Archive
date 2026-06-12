---
title: "Looking for a good DAC and headphone amplifier"
date: 2019-06-01
forum: Hardware
---

### Post by jis on 2019-06-01
They say anything that can not be played at 44kHz or 48kHz sample rate is unhearable. Do you agree? Are the greater sample rates just for selling more expensive DACs and headphone amplifiers? I think signal to noise ratio (SNR) and total harmonic distortion plus noise (THD+N) are more relevant properties. What is such a good USB device for Linux?

---

### Post by Autodave on 2019-06-01
SNR and THD+N are pretty much terms not used anymore.  Tape recorders (except in a few cases) recorded analog signals that were processed by analog amps, pre-amps, etc.  But, with digital recording (which is what your computer does) the SNR and THD are actually zero.  Once a signal becomes digital and no longer analog, it can be processed through hundreds of pieces of equipment and the SNR and THD remain the same.

44khz is above human hearing.  The average human's hearing ends at about 16khz to 20khz.  The argument is made that harmonics from stringed instruments, even though above the human range of hearing, when all combined with other instruments, can be heard better at higher hz.  Many argue that it is true.  Personally, with a very decent home system, I hear no difference between recordings limited to 22khz as opposed to 44khz sampling rates.  Are there more frequencies at 44khz sampling?  Absolutely.  Can you hear them? Not likely.  Your dog *may *be able to, but not you.  (And I am sure that there are those who will argue this.)

Sampling rate gets a little more confusing.  In theory, if the sampling rate is twice the highest frequency that you can hear, then the recording will faithfully sound the way you originally heard it.  [https://www.sweetwater.com/insync/7-things-about-sample-rate/](https://www.sweetwater.com/insync/7-things-about-sample-rate/) does a very good job of explaining this.

So, going back to what I stated earlier, a sampling rate of 32khz will reproduce what an average person's hearing can comprehend.  If I am recording a few singers, a couple guitars, a keyboard, and a drummer, I'll use 22khz.  My recording will be quite smaller than at 44khz, but sounds just fine when played back through my headphones, my home system, or the 6,000 watt system at church.

Your mileage may vary.

What kind of USB device are you looking for?

---

### Post by jis on 2019-06-01
I am looking for a decent quality device that can convert the digital signal to analog line level signal and maybe signal for headphones.

---

### Post by CatKiller on 2019-06-01
> **jis said:**
> I am looking for a decent quality device that can convert the digital signal to analog line level signal and maybe signal for headphones.

The Scarlett 212 is supported by ALSA and is entirely painless. It's powered by USB, has L/R outputs for speakers, headphone out, and a nice large volume control, and they sell so many of them that they aren't terribly expensive. I've been very pleased with mine.

---

### Post by CatKiller on 2019-06-01
> **Autodave said:**
> 
44khz is above human hearing.

The 44 kHz sample rate is so that you can capture signals of up to 22 kHz. If you use a 22 kHz sample rate, you can't reproduce anything over 11 kHz. While you do lose the ability to hear the highest frequencies with age and hearing damage, most people can still hear frequencies above 11 kHz.

Whether you choose to use 44.1 or 48 kHz as your sample rate is dependent on the rest of your gear and the sample rate of the signals you're using: you don't want to have lots of conversions. Pretty much anything can be configured to use either these days, but it used to be a real hassle.

---

### Post by CatKiller on 2019-06-01
> **jis said:**
> Are the greater sample rates just for selling more expensive DACs and headphone amplifiers?

The higher sample rates are for when you're combining multiple signals: multitrack audio. The potential errors are then small, and the effects of those errors are *way* outside the audible range. It's not for direct playback; you're going to be downconverting your mix to 44.1 kHz (cd) or 48 kHz (dvd) before playback.

---

### Post by jis on 2019-06-01
Isn't that Scarlett 2i2 and made for recording music?

---

### Post by CatKiller on 2019-06-01
You're right on the typo. It does have 2 inputs as well, but you don't have to use them.

---

### Post by jis on 2019-06-01
> **CatKiller said:**
> The Scarlett 212 is supported by ALSA and is entirely painless. It's powered by USB, has L/R outputs for speakers, headphone out, and a nice large volume control, and they sell so many of them that they aren't terribly expensive. I've been very pleased with mine.

It has balanced TRS line outs, so how would you connect it to a regular hifi amplifier that has regular RCA inputs?

---

### Post by CatKiller on 2019-06-01
> **jis said:**
> It has balanced TRS line outs, so how would you connect it to a regular hifi amplifier that has regular RCA inputs?

You can get adaptors between RCA and TRS for pennies. 

Don't get me wrong, I'm not saying that it's the best DAC ever, and is ideal for everyone under all circumstances; just that I've used one and it was entirely painless, and much better than you might expect for the price.

---

### Post by jis on 2019-06-01
> **CatKiller said:**
> The higher sample rates are for when you're combining multiple signals: multitrack audio. The potential errors are then small, and the effects of those errors are *way* outside the audible range. It's not for direct playback; you're going to be downconverting your mix to 44.1 kHz (cd) or 48 kHz (dvd) before playback.

Still there are plenty of  e.g. 96kHz DACs and headpone amplifiers made for playback. And apparently some music is sold having higher sample rate. Having the ability in DAC will save you from sample rate conversion in Linux in some cases with such files, so I guess that is the only benefit.

I think bit depth is more relevant during processing of recordings.

This article tries to explain:
[https://www.wikiaudio.org/best-audio-interface/](https://www.wikiaudio.org/best-audio-interface/)

---

