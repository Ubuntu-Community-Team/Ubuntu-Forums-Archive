---
title: "Asus M5A78L-M LX PLUS motherboard recording sound issue"
date: 2012-10-23
forum: Hardware
---

### Post by goodbye-windows(tm) on 2012-10-23
Hi All,

I bought an ASUS Motherboard, a six core processor and 8 GB of 1800 MHz ram. It's fast, runs great. Except..... I can't record from the mic input or do skype. Anything that uses the mic input produces crackling audio in the saved file or on the other end of the skype/google voice calls. The audio output to the speaker/headphones was not a problem.
feel free to compare the improvement. Note these were made when I had a  cold, so the nasal sound is not a sound card induced anomaly.

The entire motherboard (ASUS M5A78L-M LX PLUS Socket AM3+ 760G mATX AMD Motherboard) and processor (FX 6100 Black Edition 3.3GHz Hexa-Core Socket AM3+ Boxed Processor) cost $110, the ram was an additional $40. So the price was unbeatable. 

I tried everything to fix the audio problem......this forum, multiple google searches and the suggestions from the official Ubuntu sound system troubleshooting guide.

My nephew has the same motherboard and the same sound issue.

As a last resort, I ordered some $3 usb sound cards from a US ebay seller. They are the same size as a USB memory stick. When they arrived, the only issue was they wouldn't work in conjunction with the existing on board sound card. I finally figured out how to disable the stock on board sound card.

After I shut down the on board ALC887 sound card, everything worked!!! Despite the low cost, the playback audio and the mic input recordings sound like a million bucks now!!!

The noise floor was more favourable on the mic input of the $3 sound card, meaning less hiss and white noise output than the stock on board sound system produces. Headphone out audio sounded cleaner than the on board sound card too, it's a win/win option. 

I didn't expect much from these little gems, but they are awesome with respect to audio in/out and seem to run fine in Xubuntu 12.04.

The only downside is that they have limited I/O, which is one mono mic input jack and a headphone output jack. So, they aren't the best answer for everyone......

I'm overjoyed to have decent audio when I use skype and google voice now!!!

I tried to upload a before and after set of recordings, but the forum wouldn't accept my .wav files.
  
Regards,

Art

---

### Post by holastickboy on 2012-10-23
Nice to hear it all worked out.  Perhaps there was electrical issues with your motherboard that were causing the pops and clicks you heard? Static perhaps?

---

### Post by goodbye-windows(tm) on 2012-10-24
> **holastickboy said:**
> Perhaps there was electrical issues with your motherboard that were causing the pops and clicks you heard? 

Hi holastickboy,

I think it was likely a compatibility issue. My nephew returned his (same model) unit to the factory for repair. When it was returned, it still had the same problem. 

It wasn't static, it was crackling. At rest, there was no defect and it would record the noise floor without adding anything that wasn't white noise. As soon as voice was recorded though, it would put out audio with many short bursts of very brief 'lightning' type crackles.....like extremely brief (and numerous) 'ticks'. The crackles were most significant at the times in the audio where the level went from some above zero level to brief pauses in the words and syllables.  It was not associated with the sampling rate or the gain setting of the mic input.

I made recordings using audigy, and the output shows many extremely brief spikes. When I zoom in on the signal to show the individual sample times, I could see the spikes in detail, they were 2 or 3 sample wide pulses. These pulses did not show up when recording white noise. 

The pulses as viewed when zoomed in with audigy had no spikes that spiked downward, they were always spikes in the positive direction with no negative going spikes that should be present. 

I spent quite a few days researching the issue, and did all the mods suggested by the official documentation for Ubuntu. One of the last google searches was specific to my exact model motherboard. Even then, most of the issues found were 'no sound' issues, which was an Asus issue that was not dependent on the specific model number of the motherboard.

I'm stumped bigtime, which is why I tried the plug in usb sound card. It was definitely a last resort.

Regards,

Art

---

