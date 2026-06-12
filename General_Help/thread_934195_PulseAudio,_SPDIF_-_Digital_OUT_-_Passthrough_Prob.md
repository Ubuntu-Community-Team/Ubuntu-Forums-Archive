---
title: "PulseAudio, SPDIF - Digital OUT - Passthrough Problems and Solutions [Hardy Heron]"
date: 2008-09-30
forum: General Help
---

### Post by heytbekankasin on 2008-09-30
Hi!

First of all, i am sorry for my English.. There can be grammar mistakes or improper usage of words. 

I want to share my experiences about Ubuntu Pulseaudio and digital out system. I spent approximately 4 months to accomplish my system to become a stable and correct working sound output system.

I've learned lots of things about Digital output concept.

I want to explain what is my system and what kind of sound system attached to it.

I have a notebook which is Acer Aspire 5920G with 2 digital output support. One is with HDMI and other is toslink (mini jack). I've been using HDMI for digital Video output because of that i've been using toslink output for digital audio out. On the other hand i don't have any idea about digital audio out using HDMI...

I have Creative DDTS-100 external digital sound decoder. Notebook connected to this Decoder for Dolby Digital, DTS and Analog>Digital sound outputs. I also have a 5+1 Speaker system working with this Decoder which is completely off topic right now.

The main idea is getting sound output (DTS, Dolby Digital, Analog) using my digital output system.

First of all, i want to talk about Digital sound system and what kind of mixer must be used to join multi applications which are using digital output.

I can absolutely say that Pulseaudio is NOT support Passthrough digital output or direct DTS or Dolby Digital decoding. I try every way even i wrote pulseaudio codes with C++ and i understand that this job is not as easy as you think. You can use some decoding or encoding libraries to success this thing where i will not write anything in. Because these libraries will convert all sound outputs to the specified format. For example, all your system sound will be Dolby Digital even the output is DTS. The main concept is decode sound and encode the specified format. The result is multi different kind of pulseaudio inputs but only one kind of pulseaudio output.

**[COLOR="Red"]This does not the meaning of your system will not play true DTS or Dolby Digital sounds.[/COLOR]**

There is not any mixer application exists which joins digital output and transfer to the digital sound decoder. This is completely wrong for the concept. Digital Decoder Hardware can solve only one input at a time. If you want to join multi digital audio then you have to accept one kind of digital output format which i've explained in previous paragraph.

So, how can you get your system sounds working with digital decoder hardware using Pulseaudio.

This is a bit tricky. You have to analysis your needs for digital sound output. For example, i am using pulseaudio for joining stereo or analog inputs and transfering to ALSA digital output. This is what the main idea of Pulseaudio i think... When i need to get DTS or Dolby Digital output working, i just kill pulseaudio (pulseaudio -k) and DTS or Dolby Digital working correctly with my decoder hardware. Generally you do not need to get both sounds working together.. This is automatic in Windows. Windows chooses the right output and blocks another. Digital output has the highest priority. If you are watching a DTS movie in Windows, Windows will not play any other analog or digital sound. Because digital output is already in use. Ubuntu don't have this feature that's why we are doing it manually.

So what must pulseaudio do? (need pulseaudio development - [code flow])

Audio type must be understood (DTS, Dolby Digital, Analog)
If there is analog audio then do standard joining (already have this feature)
If there is Dolby Digital audio then blocks all other sound even this DTS and transfer Digital input to Passthrough Digital out (lack of this feature)
If there is DTS audio then check Passthrough is using, if not using then use Passthrough and blocks all other sounds, if Passthrough is using then ignore DTS audio.
This last two concepts are vise versa

If this implementation has done, you do not need to kill pulseaudio daemon for working correct digital audio out. Because it will automatize sound switching like windows.

If this scenario is acceptable for you, you can apply the following settings to your system with your own risk.

I assume that you have a ALSA supported sound device, correct ALSA installation and installed pulseaudio daemon.

First of all backup your system audio settings files. What are those files?

ALSA sound settings
/etc/libao.conf
/etc/asound.conf (this can not be exists)
~/.asoundrc (this can not be exists)

PulseAudio Settings
/etc/pulse/daemon.conf
/etc/pulse/default.pa

On your Volume Control for Alsa Mixer
Change to Switches tab to activate digital out working. 
Check IEC958 

if you don't see Switches tab, click edit>Preferances check IEC958 and do same think i've explained above

Open System>Preferances>Sound
Change everything to PulseAudio Sound Server

Open /etc/libao.conf with gnome editor

sudo gedit /etc/libao.conf

if there is not exists any line begining with default_driver then add this following code line, if exists then changed default_driver value as pulse

```

default_driver=pulse

```

if ~/.asoundrc is exists replace the content with the following but IF YOU HAVE OWN ADDITIONAL SETTINGS IN THIS FILE, KEEP THESE SETTINGS. If not exists create a new file on your home directory with same name and put the following code into it.

```

pcm.pulse {
   type pulse
}

ctl.pulse {
   type pulse
}

pcm.!default {
   type pulse
   slave {
        pcm "spdif"
        format S32_LE
        rate 48000
    }
}

```

pcm.pulse is for application settings which will use pulseaudio output. For example skype sound out settings must be changed to "pulse"

```

   slave {
        pcm "spdif"
        format S32_LE
        rate 48000
    }

```

this is an ALSA-driver bug workaround. When you play a DTS or Dolby Digital sound first time. No more system sounds played with digital output. This fix is making slave your pulseaudio to digital output. if you have any sound playing problems try S16_LE as format.

```

default-fragments = 8
default-fragment-size-msec = 5
resample-method = speex-float-3

```

the above settings must add at the end of the /etc/pulse/daemon.conf file for sound glitch problem. If you don't have any problem with skype, music playing or other analog audio, you won't need to add these lines

```

load-module module-alsa-sink device=hw:0,1 rate=48000

```

search /etc/pulse/default.pa file for this line #load-module module-alsa-sink and change this with the one i write above

This will set your pulseaudio daemon to use digital output.

device=hw:0,1 can change device to device. you can learn which is your digital output of your device by typing aplay-l in your terminal window

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card **0**: Intel [HDA Intel], device **1**: ALC883 Digital [ALC883 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

this is my machines aplay -l output 

card 0, device 1 meaning hw:0,1

at last, you can get a bit cut of sound from the begining when you want to play a music. This is because pulseaudio suspend module. You can disable it from /etc/pulse/default.pa

Just search 
  load-module module-suspend-on-idle
and commend it like
# load-module module-suspend-on-idle

now you can restart your sound services or easily restarting your system (do not use CTRL + ALT + BACKSPACE). Your all analog sounds will be joined by pulseaudio and transfered to digital output.

If you want to use digital out for DTS or Dolby Digital, just kill pulseaudio typing pulseaudio -k from terminal and use your favorite application with ALSA Sound output settings.

If you want to play analog sounds after Digital pleasure, type pulseaudio -D from terminal. If you are using the same application for analog sound don't forget to change audio output to Pulse Audio.

If there is no sound anymore after Digital Pleasure even you apply pcm slave workaround (I explain above), type iecset audio 1 from terminal to reactivate your digital out settings.

I may forget something in this text. If you have any problem after appling these settings, please post a message in this topic. I will try to help you and improve my text according to your problems...

---

