---
title: "Kernel update breaks pulseaudio in Ubunutu 8.10"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by bowens44 on 2009-03-08
I have been trying to get Ubuntu 8.10 to be completely functional. I have had several problems. The most recent is the 'no sound' problem. I have found that updating the kerenel to either 2.6.27-11 or 2.6.27-13 breaks pulseaudio.

 
After doing a fresh install and updating the kernel I have no sound. If I boot into the 2.6.27-7 kernel pulseaudio seems to work perfectly.

I am hoping that someone can tell me what it is about these updates that breaks pulseaudio. Is there a way to update the kernel without breaking pulseaudio?

---

### Post by Neo_The_User on 2009-03-08
This error is caused by a kernel config option being turned off. You're going to have to either use that old kernel or compile your own.

---

### Post by bowens44 on 2009-03-08
> **Neo_The_User said:**
> This error is caused by a kernel config option being turned off. You're going to have to either use that old kernel or compile your own.

What config option? do you know why this was done? Did this break pulseaudio for everyone who upgraded the kernel?

---

### Post by Neo_The_User on 2009-03-08
Not everybody. Only the people who have the same soundcard and chipset as you. Try lspci on the new kernel and post output then post output of lspci on the old kernel. Here is how.

In a terminal:

```

lspci

```

If they both detect your sound card (usually labeled as Multimedia device) then try changing the audio output modules by going into System > Preferences > Sound and change it from Autodetect to... Eh try em all and see what you get. OSS, Alsa etc. Lots of times when I compile my custom kernels and I re-use the exact same config that I made, you never know until you actually compile it and run it. So... maybe the code for your chipset, sound card, or alsa code in the kernel source code was just changed around a bit so it doesn't work. I'd file a bug if I were you and I'd use a different kernel in the mean time until it gets fixed (or just never touch that kernel again.)

---

### Post by bowens44 on 2009-03-08
> **Neo_The_User said:**
> Not everybody. Only the people who have the same soundcard and chipset as you. Try lspci on the new kernel and post output then post output of lspci on the old kernel. Here is how.

In a terminal:

```

lspci

```

If they both detect your sound card (usually labeled as Multimedia device) then try changing the audio output modules by going into System > Preferences > Sound and change it from Autodetect to... Eh try em all and see what you get. OSS, Alsa etc. Lots of times when I compile my custom kernels and I re-use the exact same config that I made, you never know until you actually compile it and run it. So... maybe the code for your chipset, sound card, or alsa code in the kernel source code was just changed around a bit so it doesn't work. I'd file a bug if I were you and I'd use a different kernel in the mean time until it gets fixed (or just never touch that kernel again.)

lspci - from 2.6.27-13 - no sound with this kernel

03:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)


lspci - from 2.6.27-7 - sound works flawlessly with this kernel

03:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

I tried the various audio output modules in System > Preferences > Sound

with the 2.6.27-7 kernel all three work oss,alsa and pulseaudio
with kernel 2.6.27-13 none of the three options work. They look as if they're working but there is no sound.

---

### Post by Neo_The_User on 2009-03-08
If it finds your hardware but doesn't work, it's a kernel problem. I've compiled over 100 kernels in my past and I see this pattern a lot. Don't worry about it. You can't do anything about it. Uninstall the -13 kernel and double check menu.lst to make sure it doesn't show up. It will be a waste of space and a pain to select the older kernel from the grub menu by hand after every reboot.

---

### Post by kostkon on 2009-03-08
> **bowens44 said:**
> lspci - from 2.6.27-13 - no sound with this kernel

03:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)


lspci - from 2.6.27-7 - sound works flawlessly with this kernel

03:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

I tried the various audio output modules in System > Preferences > Sound

with the 2.6.27-7 kernel all three work oss,alsa and pulseaudio
with kernel 2.6.27-13 none of the three options work. They look as if they're working but there is no sound.
Try this. Boot with the non working kernel. Revert your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to the defaults you had.

Then right click on the speaker in your system tray and select *Open Volume Control*. Select the *Switches* tab and see if the *Analog/Digital* switch is enabled. If it is, disable it. Then check if your sound is working.

It happens sometimes with the Audigy cards. The new kernel after an kernel update enables this switch for some strange reason. It must be disabled at all times.

---

### Post by Neo_The_User on 2009-03-08
The audio control panel probably won't open for him. It will probably say something about gstreamer plugins not found or whatever.

---

### Post by bowens44 on 2009-03-09
> **kostkon said:**
> Try this. Boot with the non working kernel. Revert your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to the defaults you had.

Then right click on the speaker in your system tray and select *Open Volume Control*. Select the *Switches* tab and see if the *Analog/Digital* switch is enabled. If it is, disable it. Then check if your sound is working.

It happens sometimes with the Audigy cards. The new kernel after an kernel update enables this switch for some strange reason. It must be disabled at all times.

This did the trick, I now have sound when using the 2.6.27-13 kernel!!

Thank you

---

### Post by bowens44 on 2009-03-09
> **Neo_The_User said:**
> The audio control panel probably won't open for him. It will probably say something about gstreamer plugins not found or whatever.

Neo_The_uUser, kostkon's suggestion worked. Thank you for your time and assistance.....

---

### Post by MusicallyInspired on 2009-05-01
I'm having the same problem but there is no Switches tab in my volume control. Just Playback and Record. I have an Audigy 2 ZS.

---

