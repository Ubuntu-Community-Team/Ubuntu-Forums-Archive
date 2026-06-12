---
title: "Foxconn NTA-350 no audio out of HDMI ubuntu 11.10"
date: 2011-10-27
forum: Hardware
---

### Post by uncojimmy on 2011-10-27
Hi All,

I am somewhat familiar with Ubuntu. 
I just installed 11.10 on a new Foxconn NTA-350. 
There is no audio coming out of the HDMI.

Any advice is greatly appreciated.

Thanks, 
unco

---

### Post by Roasted on 2011-10-27
> **uncojimmy said:**
> Hi All,

I am somewhat familiar with Ubuntu. 
I just installed 11.10 on a new Foxconn NTA-350. 
There is no audio coming out of the HDMI.

Any advice is greatly appreciated.

Thanks, 
unco

In your sound preferences is the HDMI sound card selected?

---

### Post by uncojimmy on 2011-10-28
I made sure it was selected, still no audio. The audio works fine out of the NTA-350.

---

### Post by Roasted on 2011-10-28
> **uncojimmy said:**
> I made sure it was selected, still no audio. The audio works fine out of the NTA-350.

Just yesterday I ran into something similar on my HTPC build using 11.10 and HDMI for audio/video. I had no audio, yet video worked great.

First, I also made sure under "output" as well as "hardware" that the HDMI sound card was highlighted (so that way any changes you make effects that particular sound card). You might not have more than one item listed... I did as I had onboard audio as well as a dedicated graphics card with HDMI out. After that, I went into sound preferences and under the hardware tab there's a section below known as Profile. I had several options there (about 7 or 8, but again your's may vary as you have different hardware). I just turned on a video and selected each option until I got one that worked. 

In my case, it was something like (trying to recall from memory here...) "HDMI Audio nr 4"

I'm not sure why HDMI Audio nr 1 didn't work. Or nr 2, or nr 3. BUT nr 4 worked.

Moral of the story is, make sure your card is highlighted, play some music, and select each option. And of course, check mute settings on your video/audio player as well as system mute. :guitar:

---

### Post by uncojimmy on 2011-10-28
Thanks for the input....I'll check it out tonight and post the options that worked for me.

---

### Post by Roasted on 2011-10-28
> **uncojimmy said:**
> Thanks for the input....I'll check it out tonight and post the options that worked for me.

Yes - please post back. I'm always curious how things end up. Good luck!

---

### Post by bobsageek on 2011-10-28
I have one of these sitting in my cart at Newegg, please update when you can.

---

### Post by uncojimmy on 2011-10-29
Ok so this is pretty simple...
I went to the sound settings. 
Under the hardware tab I had to devices. 1 for HDMI the other for internal speakers
I disable the internal speakers. 
I set the profile for "Digital Stereo (HDMI) output

Also in the output tab. 
I only had one option. "Internal Audio Digitial Stereo)


Roasted.....Thanks for the advice. 


YES...thank you....no need for a W7 license....
Ubuntu looks sooooo....much better.....

---

### Post by Roasted on 2011-10-31
> **uncojimmy said:**
> Ok so this is pretty simple...
I went to the sound settings. 
Under the hardware tab I had to devices. 1 for HDMI the other for internal speakers
I disable the internal speakers. 
I set the profile for "Digital Stereo (HDMI) output

Also in the output tab. 
I only had one option. "Internal Audio Digitial Stereo)


Roasted.....Thanks for the advice. 


YES...thank you....no need for a W7 license....
Ubuntu looks sooooo....much better.....

That being said, you're good to go and you have sound playing perfectly through HDMI? It would be a great help if you would edit your post to mark as solved if that's the case. :)

---

