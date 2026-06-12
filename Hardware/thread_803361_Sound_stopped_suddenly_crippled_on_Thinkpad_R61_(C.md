---
title: "Sound stopped suddenly crippled on Thinkpad R61 (Conexant CX20549 Venice)"
date: 2008-05-22
forum: Hardware
---

### Post by ireneshusband on 2008-05-22
Sorry, thread title should have been:
SOUND SUDDENLY AND UNEXPECTEDLY CRIPPLED ON THINKPAD R61 (CONEXANT CX20549 VENICE)

The internal sound was working on my Hardy installation on my Thinkpad R61, but now it isn't.

Where I'm at now is that there is no sound output, either through the speakers or through the headphone socket (both worked before).

There is sound input of a sort through the microphone socket, but it's a bit weird. Skype seems to be able to be able to use the microphone without any problem, and you can even see Skype adjusting the sound levels gracefully to get them just right. However when I start jackd and attach meterbridge (a simple audio level meter) to the audio input, meterbridge either peaks out so completely that the needles are stationary at the top of their range, or else only the right channel needle is jammed at the top while the left channel needle flickers very close to the top, well into the red zone, and peaks a good deal of the time. Changing the internal mic and external mic levels makes no difference. Nor does muting or unmuting those mics.

Another issue, which may or may not be connected, is that mixers such as gamix see the external mic as an internal one (I know this from playing with the mixer while testing Skype).

I have been able to play and input sound successfully using an external USB audio interface.

I did make some changes a while back to /etc/asound.conf in order to enable Skype and pulseaudio to share the internal sound device using dmix. However I believe that I have reversed all those changes and I have rebooted a few times since then. I have also made sure to kill skype and pulseaudio when troubleshooting. Tests I have carried out have included running mplayer from the console and running hydrogen as a jack client.

I should also add that I was able to run pulseaudio and skype alongside each other for a while after implementing that dmix hack. I can think of nothing I did between then and the the time sound stopped working that could have had a bearing on the configuration of sound devices. Nor could I find any security update or other change in the dpkg history that might account for this.

Any ideas?
Many thanks in advance.

---

### Post by jasper.noid on 2008-07-26
I have the same problem (also with Hardy on an R61), and I didn't even fiddle with my configuration. As far as I can recall, all I did was install Skype. Sound stopped working.

Did you ever manage to fix this?

Thanks
/Jasper.

---

### Post by ireneshusband on 2008-07-26
I did get it working again, but I can't remember with any clarity what I did because life has been pretty busy the last couple of months. However I believe I did something to my /etc/asound.conf not too long ago and I suspect that that is what did the trick. So here it is:

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

pcm.skypeout
{
    type plug
    slave.pcm "dmix"
}
    ctl.skypeout
{
    type hw
    card 0
}
    pcm.skypein
{
    type plug
    slave.pcm "dsnoop"
}
    ctl.skypein
{
    type hw
    card 0
}

---

### Post by jasper.noid on 2008-07-26
No, didn't work for me.

I'm not so sure anymore it's Skype related. Seems a lot of people are having sound trouble with Hardy on machines with Intel's ICH8 sound chip, like the Lenovo R61 you and I have.

But you got it to work again, so it's not impossible :-) Can you tell me what kernel and ALSA versions you have installed, and also if you have any custom config in your /etc/modprobe.d/alsa-base?

Thanks,
Jasper.

---

### Post by ireneshusband on 2008-07-26
Ah. I think what you may be looking for is

options snd-hda-intel model=thinkpad

Failing that, I can at least tell you that I'm using the official realtime kernel (currently 2.6.24-19-rt #1 SMP PREEMPT RT Fri Jul 11 23:20:22 UTC 2008 x86_64 GNU/Linux)

---

### Post by Yellow Pasque on 2008-07-26
OSS4 is known to work for this chip [http://ubuntuforums.org/showthread.php?t=712823](http://ubuntuforums.org/showthread.php?t=712823)

> Ah. I think what you may be looking for is
options snd-hda-intel model=thinkpad
The 'thinkpad' keyword is not listed as an option for the Conexant 5045/20549
```
	Conexant 5045
	  laptop-hpsense    Laptop with HP sense (old model laptop)
	  laptop-micsense   Laptop with Mic sense (old model fujitsu)
	  laptop-hpmicsense Laptop with HP and Mic senses
	  benq		Benq R55E
```

---

### Post by ireneshusband on 2008-07-26
> **Temüjin said:**
> OSS4 is known to work for this chip [http://ubuntuforums.org/showthread.php?t=712823](http://ubuntuforums.org/showthread.php?t=712823)


The 'thinkpad' keyword is not listed as an option for the Conexant 5045/20549

Try it anyway. This is voodoo. It's not supposed to make sense. I had a problem. I don't have it any more. This means that either the line above worked or the problem spontaneously disappeared (which is possible of course).

---

