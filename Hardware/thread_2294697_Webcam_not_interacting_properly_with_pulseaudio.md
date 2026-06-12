---
title: "Webcam not interacting properly with pulseaudio"
date: 2015-09-12
forum: Hardware
---

### Post by neltnerb on 2015-09-12
I am using a Logitech Quickcam 3000 for Business, and trying to get the mic to work with skype on Ubuntu 15.04. I am able to get video to work, but not audio. However, the webcam mic itself appears to be fine.

According to [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) the webcam itself is compatible with Skype and "works out of the box" using uvcvideo.

I needed to use guvcview in order to make the video work at all. At first it just showed black, but this seems to have been because the automatic video controls are non-functional. However, I now have that part working fine.

I was able to get audio to work in fine on VLC by using "Open Capture Device" and selecting /dev/video0 and hw:2,0

When I look at the volume control in Sound Settings, it lists under the Input tab "Microphone Quickcam 3000 for Business" as an input device, but shows no input levels.

pavucontrol for input devices only lists the built in microphone port.

I thought perhaps the microphone reads as disconnected unless the webcam is on, so I started a video call with someone on skype, but the mic continues to not detect anything.

I tried checking in alsamixer but the input is not muted (and besides, it works in VLC).

The mic clearly works, although vlc is probably directly accessing the device instead of using pulseaudio. So it seems that the issue is that pulseaudio isn't properly handling the input source. It's clearly not muted in alsa, but pulseaudio shows no input levels. I am not really sure where I can go from here, does anyone have any ideas?

---

### Post by Mike_Walsh on 2015-09-13
Hallo, neltnerb.

I daresay you're well aware of this, but since MS bought Skype out not so long ago, it hasn't worked properly in Linux.....and PulseAudio is the main culprit. This is in no way 'MS-bashing'; I'm merely stating the bald facts!

I've been 'all-Linux' since last April, when XP went end-of-life.....and I've been trying to make Skype function correctly ever since. I've finally given up on it. Not being able to convince friends and associates to try any of the open-source alternatives, I've taken the unplanned, retrograde step of re-installing XP on an old machine, simply **for** Skype.....along with all the security implications that entails.

It's locked down tighter than a nun's chastity belt, and is being used only for that purpose. But for everything else, Linux (Xubuntu & Puppy) suits my needs very nicely.

I doubt you'll get many replies on this one, to be honest. There **is** no real solution (that anyone in the open-source community has yet come up with, anyway); and a scan through the Forums will show many people asking this same question.....with not much in the way of resolution. There have been various half-hearted projects attempting to make it work with ALSA instead, but there's not been a lot of interest, it seems. Skype is, unfortunately, proprietary software with 'closed-source' code, and is a 'sticking-point' for many people making the switch to Linux.....and this, along with various other things that WINE won't handle, is one of the main reasons why so many of us either dual-boot with Windows, or keep it on a separate machine.

Sorry to sound so negative, but I'm only trying to be constructive with my advice..! The only reason I've re-installed XP is because the machine it's now on originally came with it (an elderly 12-yr old Dell Inspiron laptop; an early 5100 from 2003, which I recently picked up for a song.....the 'big' brother to my even older 1100), and it just won't run any newer versions of Windows. I refuse to shell out hundreds of pounds on a new machine **simply** for Skype...

(I admit it.....I'm a 'tight-ass'. So sue me..!) Besides, I enjoy playing around with old tech...and no-one wants the stuff these days... :D

Regards,

Mike. ;)

---

### Post by neltnerb on 2015-09-14
That may well be the case in general, but I think that in this instance it is the interface between alsa and pulseaudio where the problem lay.

Pulseaudio doesn't register any signal level whatsoever in the mixer, but the mic works when VLC captures audio using the (presumably) alsa direct interface. It reports that the mic exists as a device in the ubuntu sound settings, but pavucontrol does not. There is definitely something strange going on between the mic and pulseaudio.

Skype did work fine for sending video, but if pulseaudio isn't getting data from the mic, I can hardly blame skype itself for failing as well.

It's totally possible that Skype will still not work for audio, bu for now I think the blame is most likely on pulseaudio.

---

### Post by Mike_Walsh on 2015-09-14
> **neltnerb said:**
> Skype did work fine for sending video, but if pulseaudio isn't getting data from the mic, I can hardly blame skype itself for failing as well.

It's totally possible that Skype will still not work for audio, bu for now I think the blame is most likely on pulseaudio.

I'm not laying the blame at Skype's door per se, but prior to the takeover, Skype was always built to use ALSA. After the takeover (shortly before 4.2, I believe), Microsoft, in their 'wisdom', decided to change the default audio-server to PulseAudio. I could be wrong about this, but I rather suspect that there are certain API's that are not being disclosed.....so, naturally, the developers of the Linux version are working with one hand tied behind their backs, so to speak.

In the last 18 months or so, I have tried everything I can possibly dream up, including all the steps that you yourself have tried (and several more besides.....and **then **some!) I think it's almost impossible to come up with combinations of settings, etc., that haven't been tried already by someone else. And I honestly believe that when that 'breakthrough' does eventually come, it'll be all over the web in very short order!

Unless, of course, VOIP changes out of all recognition in the meantime.....


Regards,

Mike. ;)

---

