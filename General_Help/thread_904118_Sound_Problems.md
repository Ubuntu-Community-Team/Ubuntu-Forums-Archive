---
title: "Sound Problems"
date: 2008-08-28
forum: General Help
---

### Post by Pedjt on 2008-08-28
Hello all. I'm fairly new to linux, so I'll try to get in as much information as I can on the first post since I don't know what is relevant to my problem.

I tried performing the fix that allows you to mix sounds through ALSA ( link: [https://help.ubuntu.com/community/EnableSoftwareMixing](https://help.ubuntu.com/community/EnableSoftwareMixing) ).

Afterward, though, I didn't have any sort of sound at all. I followed the instructions in the thread and restored the relevant files and removed the packages outlined (alsa-base and alsa-oss). Still no sound. To note, I did have sound originally, its only when I tried to do this multiple sound fix that I lost that capability altogether.

I'm using a Dell Soundblaster Live! card. There is also an integrated sound card, but that has been disabled in the BIOS.

I tried using "aplay" in recovery mode to see if it was GNOME that was causing the problem, but there still wasn't any sound.

Under System>Preferences>Sound, all playback options are set to Autodetect. Dell Sound Blaster Live (alsa mixer) is set as the default mixer.

Hitting "aplay -l" returns

> **** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Hitting "cat /proc/asound/cards" returns

>  0 [Live           ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0xdf20 irq 23
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xf0000000, irq 22


I'd settle for going back to just being able to use one application at a time. Any advice?

---

### Post by tuxxy on 2008-08-28
> **Pedjt said:**
> Hello all. I'm fairly new to linux, so I'll try to get in as much information as I can on the first post since I don't know what is relevant to my problem.

I tried performing the fix that allows you to mix sounds through ALSA ( link: [https://help.ubuntu.com/community/EnableSoftwareMixing](https://help.ubuntu.com/community/EnableSoftwareMixing) ).

Afterward, though, I didn't have any sort of sound at all. I followed the instructions in the thread and restored the relevant files and removed the packages outlined (alsa-base and alsa-oss). Still no sound. To note, I did have sound originally, its only when I tried to do this multiple sound fix that I lost that capability altogether.

I'm using a Dell Soundblaster Live! card. There is also an integrated sound card, but that has been disabled in the BIOS.

I tried using "aplay" in recovery mode to see if it was GNOME that was causing the problem, but there still wasn't any sound.

Under System>Preferences>Sound, all playback options are set to Autodetect. Dell Sound Blaster Live (alsa mixer) is set as the default mixer.

Hitting "aplay -l" returns



Hitting "cat /proc/asound/cards" returns



I'd settle for going back to just being able to use one application at a time. Any advice?

Have you tried selecting ALSA as the playback options, also what sounds are you trying to mix as ALSA should handle multiple sounds at once anyway

---

### Post by Pedjt on 2008-08-29
> **tuxxy said:**
> Have you tried selecting ALSA as the playback options, also what sounds are you trying to mix as ALSA should handle multiple sounds at once anyway

Yes, I tried setting ALSA as it instructed in the fix, but I undid (or tried to) everything in the fix in an attempt to salvage sound capability. I tried the other options in the drop down box as well but to no avail.

I was trying to mix programs like Movie Player and Firefox, for example. Multiple programs couldn't use the sound card at once, or even sequentially, it seemed. Are you saying the fix is unnecessary? I'm not sure I understand.

---

### Post by Pedjt on 2008-08-29
Anyone? I tried using the integrated sound instead. aplay -l now returns:

> **** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I made sure the master sound was unmuted in alsamixer. Everything is connected properly, as far as I know. I don't get so much as the ubuntu startup jingle. The system is able to find the card, but the pipe is broken somewhere.

Edit: Booting from the ubuntu cd allows sound to be played, just checked.

---

### Post by markbuntu on 2008-08-29
You really borked your sound. Anyway, my overly extensive and longwinded guide should fix you up. It will get you multiple sound application sharing and you can use both of your sound cards. It starts with the basics and has a whole lot of links to just about everywhere you would need to go to fix your sound problem. You will become a Ubuntu Sound expert.
 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If it does not work, you can flame me.

---

### Post by Pedjt on 2008-08-30
Thank you! The problem seemed to be with one of the files created in the fix. I had to change one of the default settings, whose information I found in one of the wikis you linked. The flash support library also fixed firefox sound. Glorious day!

---

