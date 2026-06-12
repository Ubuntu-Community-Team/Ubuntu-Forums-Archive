---
title: "Headphone sound won't work, speakers are fine..."
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by dbee on 2007-02-17
I just got a new laptop,  and I dual-booted ubuntu on to it. I'm having a problem though with my headphone sound. When I put my headphones into the headphone jack, the sound continues to play from the laptop speakers ONLY instead.

I'm on edgy 386 gnome, new install with the repository nvidia drivers. 

Speaker sound works fine, when I put in my headphones, the speaker sound continues to work - but the I don't get anything from my headphones.

I have an intel sound card, it seems to be working fine. I didn't have the same issue with windows. I've checked my headphones, they work fine as well. I have only one soundcard installed (that I know of). I've had a look at alsamixer, and I've messed around with it a bit, it didn't help though. I switched from alsa to oss from the dropdown menu and that didn't make a difference either.
```

babo@eire:~/Desktop$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
Does anyone have any ideas ? ... I thought this might be a hardware issue. But again, it seems to work fine on windows ...

Thanks in advance,

---

### Post by mikewhatever on 2007-02-17
Intel audio cards, although supported, seem to act weird. Some have sound working but no mic, others no sound and no mic, and so on...
Have you tried reinstalling the driver yet? 
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

---

### Post by dbee on 2007-02-19
Ok thanks, MikeWhatEver.

I went through the alsa libs, drivers and utils installation. 

It seemed to work out fine. My speaker sound works, and when I plug in the headphones - they work fine for me too. The only trouble now, is that I don't have microphone sound.

The little speaker LED on my HP Pavillion shows up red, even though I can toggle it up and down and the volume will change. Obviously something must be muted - the button comes out blue in Windows - but I'm not entirely sure what...

I've had a look at alsamixer, it doesn't seem to have any mute buttons in it for some reason. It just has L - R Capture instead, which is a bit confusing. I've changed everything and then I've changed it back, both from the command line (amixer) and from the terminal GUI. I guess it must be just something small.

Here is a code dump that I thought might come in handy (as per SoundDebugging Tutorial). I've toggled ExtMic and LineIn back and forth but I didn't get any change. They were both turned off though when I hit 'amixer' for this print out ...

[http://www.pastebin.ca/363526](http://www.pastebin.ca/363526)

Thanks

---

### Post by mikewhatever on 2007-02-19
Have you tried setting the external mic to capture in alsamixer? It doesn't make sense, because you want the internal one, but in my case, setting the internal one to capture made the external one work. In alsamixer (from the terminal) hit Tab twice to show more options, then move to external mic and hit space.

---

### Post by dbee on 2007-02-20
Nope, like I said mikewhatever - I tried fiddling with just about everything on the alsamixer and it still didn't make any difference. 

I've attached the state of my alsamixer below. Hopefully, if I'm doing something wrong you can take a look at it for me ?

Thanks,

---

### Post by mikewhatever on 2007-02-20
You don't seem to  have an internal mic in alsamixer and I don't know why that is. If you double click the speaker in the top panel and go to the Switches tab, is there a box for internal mix?

---

### Post by dbee on 2007-02-21
Hi Mikewhatever,

Unfortunately, since I reinstalled the alsa libs/drivers/utils. I no longer have the sound widget on my desktop. All I have is the alsamixer. And that seems to be a little bit weird - like you said.

---

### Post by mikewhatever on 2007-02-21
You should be able to add it to the panel by right clicking the panel, selecting Add to panel and adding Volume Control from the list that opens.

---

### Post by dbee on 2007-02-26
Ok, I've added the alsa widget to the panel. I've checked the MicIn and LineIn settings. I have Capture, Switches, Playback. Then Master, PCM, Mike Bypass , Capture, LineIn.

This hasn't made any difference at all though :-(

---

### Post by dbee on 2007-02-27
Help, this is really annoying.

I need to get my MicIn working ...

---

### Post by dbee on 2007-03-05
Guys, my sound still won't work. 

Can anyone help ?

---

### Post by the_analyzer on 2007-10-13
[QUOTE=dbee;2220601] went through the alsa libs, drivers and utils installationQUOTE]

hey, dbee how you fix the headphone problem, because I have the same problem.

thanks

---

