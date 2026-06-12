---
title: "[SOLVED] No sound in HP laptop"
date: 2008-11-22
forum: Hardware
---

### Post by PeteCox on 2008-11-22
Hi,

I thought I'd install Intrepid, finally.

I have an HP Compaq 2230s.

lspci -v | grep -i audio

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I've tried all the settings in the gnome sound tool and alsamixer - no sound is emitted.

There's a hardware sound toggle button which has no effect.

Cheers,

Pete.

---

### Post by Bucky Ball on 2008-11-22
Double clicked your speaker icon to check nothing is muted there?

---

### Post by Jorge_C on 2008-11-22
Did sound work before or did you do anything to make it work? I say it because I have the same audio device and sound doesn't work out of the box, but thankfully the solution is simple:

```
gksudo gedit /etc/modprobe.d/alsa-base
```
And add this line to the end of the file:
```
options snd-hda-intel enable_msi=1
```

If you already did that, and nothing is muted, I don't know what else could be.
By the way, is you sound toggle button a touch button? Is it red instead of white and the light doesn't change to white when you touch it?

---

### Post by PeteCox on 2008-11-22
> **Bucky Ball said:**
> Double clicked your speaker icon to check nothing is muted there?
There was nothing unusual in those settings.

---

### Post by PeteCox on 2008-11-22
> **Jorge_C said:**
> Did sound work before or did you do anything to make it work? I say it because I have the same audio device and sound doesn't work out of the box, but thankfully the solution is simple:

```
gksudo gedit /etc/modprobe.d/alsa-base
```
And add this line to the end of the file:
```
options snd-hda-intel enable_msi=1
```

If you already did that, and nothing is muted, I don't know what else could be.
By the way, is you sound toggle button a touch button? Is it red instead of white and the light doesn't change to white when you touch it?
It's a fresh install of intrepid from CD, so no it never worked.

I have modified the config file as you suggested but still no sound.

Yes the sound button is a toggle button that switches from white to amber. Pressing it changes the color but it doesn't make any difference in terms of the sound. (Of course it works fine in Windows XP!)

---

### Post by Jorge_C on 2008-11-22
OK, did you reboot after changing the file? I don't know if it is compulsory, but it sometimes helps solve things...
What codec is you audio device using?
```
cat /proc/asound/card0/codec#* | grep Codec
```

The mute button in my hp dv7 used to get stuck in red and ubuntu wouldn't be able to play sounds (usually after having booted into windows). Booting from a liveCD would make the button white again and ubuntu would play sounds fine then. That's why I asked about that, but it doesn't seem to be an issue for you.

---

### Post by PeteCox on 2008-11-23
> **Jorge_C said:**
> OK, did you reboot after changing the file? I don't know if it is compulsory, but it sometimes helps solve things...
What codec is you audio device using?
```
cat /proc/asound/card0/codec#* | grep Codec
```

The mute button in my hp dv7 used to get stuck in red and ubuntu wouldn't be able to play sounds (usually after having booted into windows). Booting from a liveCD would make the button white again and ubuntu would play sounds fine then. That's why I asked about that, but it doesn't seem to be an issue for you.

Yes, I had rebooted - no luck!
No problems with the button - I just get no sound :(

For completeness, I tried the ubuntu livecd and the sound didn't work with it.

 cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984A
Codec: LSI ID 1040
Codec: Generic 8086 ID 2802

---

### Post by PeteCox on 2008-11-23
This worked!

options snd-hda-intel model=laptop

I think at times it crackles a little but better than nothing I guess!

---

### Post by Jorge_C on 2008-11-23
Glad you got it working!

I wrongly supposed that since your audio device was like mine, they would share the same codec and thus the same solution would work, but our codecs are different.

Any way, enjoy it and don't forget to mark the thread as solved, please.

---

### Post by talofo on 2008-12-14
Please I have a similar codec. I'm on a hp8530

I cannot get his to work:

options snd-hda-intel model=laptop

Where should we change this? Do we have to do something with the mixer?

Thanks in advance,
:(

MEM

---

### Post by Jorge_C on 2008-12-14
That option has to be added in a file named alsa-base. These are the steps:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
And add this line to the end of the file:
```
options snd-hda-intel enable_msi=1
```

Regarding the mixer, just check no channels are muted.

However, take into account that the option provided may not work for you. It depends on your codec. Can you please post the output of
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

