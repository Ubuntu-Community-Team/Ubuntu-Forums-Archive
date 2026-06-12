---
title: "Want to convert old VHS tape home movies to Digital files"
date: 2020-11-07
forum: Hardware
---

### Post by cybrsaylr on 2020-11-07
Have ~40 hours of old home videotape movies. What is the best/easy way to convert and save them as digital files?

What is the best Video Capture Device to use? There seem to be so many.
Is there good Linux software for this, so Windows is not needed for this?

---

### Post by TheFu on 2020-11-09
> **cybrsaylr said:**
>  What is the best/easy way to convert and save them as digital files?
Pay someone else to do it. That is certainly the easiest way.

> **cybrsaylr said:**
>  What is the best Video Capture Device to use? There seem to be so many.
Is there good Linux software for this, so Windows is not needed for this?

"Best" is highly subjective.  

About 10 yrs ago, you could buy a VHS+DVD device for $400 which would let us play the VHS tape and write to the DVD until full (usually about 2 hrs). That would be the easiest, self-service, method.

If you are cheaper and have a working VHS player still, you can use most USB-TV-Tuner devices to record anything through the "yellow cable" output from the VHS machine.  I have a Haupauge 950Q device [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q) , but it is really old and I think they make newer models. These tuners are about $30.  The main thing is that you want one that is plug-n-play supported by Linux. The V4L2 list of compatible devices is where I'd start.  Some links:
[https://en.wikipedia.org/wiki/Video4Linux](https://en.wikipedia.org/wiki/Video4Linux)
[https://www.linuxtv.org/wiki/index.php/Supported_Hardware](https://www.linuxtv.org/wiki/index.php/Supported_Hardware)
[U]
**Very Important**: The type of VHS output is different around the world due to different standards.  You'll need to get a tuner/capture device that supports the output from your VHS player.  The USA used NTSC format, so you need a device that supports that.  Europe used PAL, so if the player is PAL, you'll need a capture/tuner that supports that.[/U]

There must be 20 different Linux software items that can record from a compatible V4L capture device. Chances are that the device will output MPEG2 video, so that is what you'd want to save to a file for editing. Then you might want to transcode to a more efficient format. Mpeg2 can be burned to DVD media, so you may want to do that. Expect to waste 2-3 DVD discs as you learn the way that works.  I've never burned a video DVD in my life. I have burned hundreds of data DVDs over the decades, though the last time must have been about 10 yrs ago.  For lower definition files, like a VHS would use, the most efficient compression would be xvid or divx probably. As resolutions became higher, newer video codecs were created to optimize storage and quality for each resolution.

Paying someone to handle this is definitely the easiest.

---

### Post by rsteinmetz70112 on 2020-11-09
Walmart used to do all sorts of transfers about 15 years ago my brother had all of my Dad's 8mm home movies transferred to DVDs.

---

### Post by cybrsaylr on 2020-11-09
> **TheFu said:**
> Pay someone else to do it. That is certainly the easiest way.



"Best" is highly subjective.  

Paying someone to handle this is definitely the easiest.

Agree after doing a Google a search and seeing all the options available there and all found on YouTube for this type conversion.

Don't want to convert to DVDs because I've found DVDs may corrupt and fail to play after a few years. 

Prefer saving them to either a couple SSDs or a few thumb/flash drives as backup. 

Got and am playing around with an [Aluratek Digital TV Converter Box]("https://aluratek.com/digital-tv-converter-box-with-digital-video-recorder") hoping that may do the job.
Aluratek does a great job as a DVR saving OTA, over the air, free TV channels about 50 free local channels for me, to Mpeg2 format.
However Aluratek will not recognize my old but still working VCR that displays/plays these old tapes on Ch 3 on my large screen HDTV.

Aluratek uses Mpeg2 and an hour of tape takes about 4.66667 GBs of space on a HD. So my ~40 hours of old home movies would take about 186.6667 GBs, easily fitting on any SSD or flash drive. 
Mpeg2 files play great on Linux PCs using VLC media player. However find when using Ubuntu default Video Player, it locks up my PC forcing me to do a 'hard shutdown' to restart my desktop to get it running again! So I just avoid using Video Player for playing these Mpeg2 files.

Just have to find the right Video Capture Device and software to use to achieve this.

---

### Post by CelticWarrior on 2020-11-09
The Aluratek Digital Converter Box only tunes digital TV. The RF output of any VHS VCR is analogue.

---

### Post by cybrsaylr on 2020-11-09
Yes TV stations going to digital TV signals rendered all old VHS VCRs unusable for recording. 
Adding an analogue Ch 3 manually to my large screen HDTV was the only way I can now use that old VHS VCR for playback purposes only. 
Was hoping an analogue Ch 3 could be added to that Aluratek Digital Converter Box but it looks like that may not be possible.

---

### Post by CelticWarrior on 2020-11-09
Definitely not possible. It doesn't have the hardware for the old analogue TV.
And you don't want to use a RF connection anyway. Someone already mentioned the "yellow cable" (plus the red and the white for stereo or just the white for mono). That is what you want to use and the only connection for a video capture device. The Aluratek doesn't even have that because not designed for that purpose.

---

### Post by MartyBuntu on 2020-11-09
There are plenty of devices for capturing analog video from VCR's. Hauppauge, "EasyCap"...lots of them all over eBay and Amazon.

---

### Post by cybrsaylr on 2020-11-13
Yes there are many devices out there now. 
Found this device that looks intriguing. Claims you don't even need a PC or software to do the job. Looks very simple to hook up and use.
 
[ezcap272 AV Capture Recorder Analog to Digital Video Converter AV HD Output TF Card Save File Plug and Play]("https://www.newegg.com/p/2CX-00B7-00007?Description=vhs%20to%20digital%20converter&cm_re=vhs_to%20digital%20converter-_-9SIANRBBY38277-_-Product")

Anyone ever use it, or have any thoughts on it?

---

### Post by CelticWarrior on 2020-11-13
It should do the job but how good it does it needs to be tested.

---

