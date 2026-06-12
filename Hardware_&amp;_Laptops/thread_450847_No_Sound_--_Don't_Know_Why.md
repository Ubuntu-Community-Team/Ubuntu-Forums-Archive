---
title: "No Sound -- Don't Know Why"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Drowzee on 2007-05-21
hi.. i am having trouble in getting any sound out while using ubuntu.. i followed this guide:
[HTML]https://help.ubuntu.com/community/SoundTroubleshooting[/HTML]
with no luck.. i have done every step.. and still i cannot get any sound..
My sound card is supposed to be a Creative Sound Blaster Live! 5.1 (driver on [HTML]alsa-project.org[/HTML]: emu10k1)

here is how my sound card is listed using ```
aplay -l
```:
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and using ```
lspci -v
```:
02:01.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
        Subsystem: Creative Labs Unknown device 1001
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at a400 [size=32]
        Capabilities: <access denied>

now I have an onboard soundcard, but I use the creative.. naturally..
I have no idea why it won't work on ubuntu it works just fine on WinXP
I went to alsamixer and unmuted everything
I went to the sound settings and selected the Alsa - Advanced Linux Sound Architecture
I didn't manage the compilation bit in the general help.. anyways I would appreciate all the help I can get.. I am new to ubuntu.. started using it recently.. so I would like it very much if the help would be very detailed so that I don't mess anything up.

Thank You in advance for your help

Sincerely
Drowzee

---

### Post by Drowzee on 2007-05-22
bump

---

### Post by Drowzee on 2007-05-23
bump..

---

### Post by dbott67 on 2007-05-23
After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

-Dave

---

### Post by Drowzee on 2007-05-23
Thanks dbott67..
but even when I created a new account there was no sound in that account..
so it seems like I am back to square one -.-

Drowzee

---

