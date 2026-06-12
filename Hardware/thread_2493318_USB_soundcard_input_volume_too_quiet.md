---
title: "USB soundcard input volume too quiet"
date: 2023-12-11
forum: Hardware
---

### Post by schneil-2k on 2023-12-11
Hello

I use my Ubuntu 22.04 to stream and record my live DJ sets.  I have the rec (line) output from my mixer going into a USB soundcard, which feeds into my mixer.  I use OBS to then video stream the set and at the same time use audacity to record the audio.

The issue I'm having is the input volume seems quite low.  The slider in sound preferences is set to full, but recorded sound in both audacity and OBS is a bit quiet.  I've tried two soundcards: a Behringer UFO-202 and a Roland Cakewalk UA-1G and get the same issue.  I never had this problem with my Trust 5.1 USB soundcard.  Can anyone help?

---

### Post by mnymonyker on 2023-12-17
Hello

I had a similar problem and what worked best for me was to click the three dots by the input audio device in the Audio Mixer of OBS. 
[IMG]https://i.ibb.co/dpZGMcp/Screenshot-from-2023-12-17-05-55-16.png[/IMG]

Select "filters", then click the "+" in the bottom left. The compressor filter was what I used, leaving the settings stock except adding 2.00 dB of gain. (I also set it to duck my desktop audio, this probably is not applicable to your setup) You may just want the gain filter if you don't want to add any compression, I'm just saying the gain in the compressor filter works well. I haven't tried the gain filter or other filters to boost volume. 
[IMG]https://i.ibb.co/v4CdVBK/Screenshot-from-2023-12-17-06-01-18.png[/IMG]

I can tell you that, for me, boosting volume above 100% in the system settings gave me bad audio. Don't do that. Also attempting to boost further with my usb interface gave bad audio. This was the point in the signal chain, and the filter which worked for me. good luck!

I didn't address volume of your Audacity recording. I'm not quite sure how your signal chain works, this may boost that without doing anything in Audacity so try and see. I'm also assuming you only require a small boost, if the OBS stream and Audacity recordings are extremely quiet, you probably have to boost the volume from your mixer to the usb interface on the input side. Possibly by using something other than your recording line out if that doesn't let you boost volume any more.

---

### Post by mnymonyker on 2023-12-17
I do want to add that if you still have the Audacity recordings that were too quiet, you can use ffmpeg to normalize (boost volume). If you don't have it just open terminal and

```
sudo apt install ffmpeg
``` then

```
ffmpeg -i </path/to/input.mp3> -filter:a loudnorm=i=-15.0 </path/to/output.mp3>
```

It probably doesn't matter if it's a .wav, .m4a or some other type of audio file, and you can name "output" whatever you want and probably use some other container than .mp3. ffmpeg is usually pretty flexible that way. -15.0 is a good value in my opinion, but if it's too loud try -20.0. If it's too quiet, try -10.0.

---

### Post by schneil-2k on 2023-12-27
Thank you so much on the three dots trick.  I'm still getting my head round OBS studio and its quirks (like it not liking my USB webcam, unless it's plugged in before I open the programme)

I've set a filter with 2.0dB of gain, this seems to be the right amount without it going into the red and matches the Vu meter of my mixer.

For audacity, to boost volume on a completed recording, I've found the normalise effect.  This boosts the volume of the recording without it clipping

---

