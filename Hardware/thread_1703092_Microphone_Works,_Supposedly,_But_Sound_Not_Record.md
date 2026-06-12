---
title: "Microphone Works, Supposedly, But Sound Not Recording or Being Heard Over the Net? WT"
date: 2011-03-08
forum: Hardware
---

### Post by djpurity on 2011-03-08
This is weird. I have a Acer laptop with a built-in webcam and it has a basic Radeon HD 4200 series internal soundcard. I haven't had this laptop too long, only like 5-6 months, but I've already been pissed at it once and hit the keyboard and I had to replace the harddrive. But I've been able to once or twice use Skype and talk using the webcam and built-in mic.

Then the mic started to go in and out, and soon the other person just can't hear me at all. So I switched to Google Talk, and I set it up, but no one can hear me.

So I got myself an external microphone and headset. It seems to work. I fiddled with the settings and when I open Sound Preferences in Ubuntu, the microphone under Output will show a response when I talk. It also is NOT MUTED, I know to check for that.

It's a logitech headset someone gave me. Everything appears to be fine, I can hear through it okay. I went to GMail's settings and opened the settings for Chat which is what works for Google Talk, and I set it up so it shows a response when I talk into the microphone. The bar moves when I talk and everything. And it is the same way in Sound Preferences. I have tried even amping the microphone as high as it will go in Sound Preferences. I've checked every setting available. 

But when I open Sound Recorder in Ubuntu and try to record something, nothing is recorded through the mic, even though the Sound Preferences and everything is showing a sound response. And when I answer the phone through Google Talk, no one can hear me talk, but someone has said they have heard a muffled breaking up sound like once or something, but mostly they've heard nothing at all. 

I don't understand. My computer is showing that I should be receiving sound. But it is not recording it nor is it sending it so that other people can hear it. So. Did I break my sound card? It still works in every other way. I can play music and hear sounds just fine. I just can't record or use a a microphone it seems. Even though the settings indicate it knows that I am speaking. It responds exactly when I talk. I don't get it. Why is the sound not coming out as output? It's being detected....

It shouldn't require drivers. Not when it's a plug and play device like this. Right? And what about the built-in mic? It sounds to me like a hardware issue but I am not sure because I never experienced anything like this before....

Any help or tips would be so greatly appreciated. I am going mad about all this. My laptop is an Acer Aspire 5251-1805.

I have an HDMI output and usually use it to use my Emerson HDTV as my monitor and the sound usually is routed through the HDMI output so it comes out of the TV speakers, but I changed it so it comes just out of the headphones or just out of my laptop speakers, too, and same problem.

I like to keep my laptop closed and have my HDTV as my monitor, and an external keyboard and mouse set up so that my laptop is like a desktop computer. Not that it has anything to do with the sound.... because it USED TO WORK. Even after I hit the damn thing and had to replace the hard drive. When I replaced the Hard drive, I installed Ubuntu 10.10 on it, rather than Windows 7, which is what my laptop had come with initially. Just FYI.

Thanks.
:confused:

---

### Post by djpurity on 2011-04-28
Wow Could it be that EVERYONE is STUMPED??? Not even a question to maybe narrow down the possibilities? Wow, I am a little disappointed here.... I always have been getting very quick and satisfactory replies while I am learning the ins and outs of Ubuntu, and refreshing my memory of using a Linux like shell environment, but with a much better GUI than Red Hat days....!

Honestly, no one knows whether or not there is a hardware issue with the sound card hardware, or whether or not there is a software issue with this particular sound card?? After all, it did work at one time, but now, it just doesn't work at all when recording through a microphone that has been verified as working and registers in the reaction waveform on screen.... there has to be something routed incorrectly, or there must be something about how the sound system of Ubuntu works.

:arrow: Please, this is very important. I am about to start a very important and very, very insanely cutting-edge in recording and producing music over long distances and without giving away the details, I was planning on using some middle man program such as Google Talk to answer the phone registered in Google Voice, and record accapella samples and using them as the inspiration for making a beat and song wrapped around it... but I need to be able to record through the program, which I believe I can hear the caller just fine and can record him talking while online -- but the problem is he cannot hear me and thus hear any instructions, cues, or critiques... etc. Please, anyone know a damn thing about how the music interface is routed through Ubuntu?

Thank you so much for just a little bit of information that would lead to perhaps solving this mystery on a bigger level and perhaps more participation from other Ubuntu gurus out there? Or are there none in this area? :-s :?: [-(

---

### Post by lidex on 2011-04-30
A million sorrows with these mic issues and they all seem to require a different solution. It can be intimidating. Let's throw some stuff at the wall and see what sticks.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

> Changing default subdevice configuration

    Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default.

        Open the pulseaudio record meter (pavumeter --record)
        Talk into your chosen device while you carry out the process and watch the meter.
            Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. 

        Use alsamixer -c n (where n is your sound card number, probably 0)
            Press F4 to get to the capture console
            Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up.
            Check the first input source is switched to your chosen plug (Mic, in my case) 
        At this point, you should see the record meter bouncing in response to your voice.
        I found that I had to repeat this procedure each time I wanted to use the Mic, even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized until it was repeated.
        This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

### Post by NoNameWill on 2011-04-30
My Acer 4520's mic doesn't work. But a separate mic works just fine. I believe mine is Nvidia though. I suspect even my cheap mic is better than the build in.

---

### Post by djpurity on 2011-05-15
> **lidex said:**
> A million sorrows with these mic issues and they all seem to require a different solution. It can be intimidating. Let's throw some stuff at the wall and see what sticks.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

From alsa documentation:
Thank you so much! This really helped me out sooooo much... I found out that when I typed gnome-alsamixer into the terminal, it said it was not found or installed. It said to install to do exactly what you said, so I typed sudo apt-get install gnome-alsamixer and then it went to download some files and installed it. Then I ran gnome-alsamixer again and was able to turn my mic off MUTE!!! And turn my headphones UP and turn my speakers UP (they were turned all the way down for some reason) and fix a few other problems... it was very nice to finally hear my own voice in my headset!!! I know the mic works now and it isn't flat!) just like you said. I am soooo happy just to get this far. Thank you so much for your help!!!! 

kudos!!!!

---

### Post by djpurity on 2011-05-15
Wait, now I am confused... I did everything and hear the mic working and hear it in my headphones, but I still do not see the sound response to my voice in the voice meter when set to "CAPTURE" and the MIC was the first one in the Capture place. There were two Capture places... the other was blank... just a ----- in place rather than the name of the mic and sound card for the capture device like the first one.

Now where u said:

> Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. 

I could NOT run the command PAVUMETER --RECORD at all. It gave me an error. So is THAT the problem?

---

### Post by lidex on 2011-05-15
> **djpurity said:**
> Wait, now I am confused... I did everything and hear the mic working and hear it in my headphones, but I still do not see the sound response to my voice in the voice meter when set to "CAPTURE" and the MIC was the first one in the Capture place. There were two Capture places... the other was blank... just a ----- in place rather than the name of the mic and sound card for the capture device like the first one.

Now where u said:



I could NOT run the command PAVUMETER --RECORD at all. It gave me an error. So is THAT the problem?
You entered that in lowercase, correct? You'll need to install it and i recommend the volume control as well:
```
sudo apt-get install pavucontrol pavumeter

```

---

