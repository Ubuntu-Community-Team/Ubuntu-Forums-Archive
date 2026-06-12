---
title: "SB Live! Configured OK but still no sound! Grrr..."
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by johnpipe on 2006-11-05
I had to install Edgy from the alternate install CD, as I could find no way to use the standard CD on a multi-distribution installation box.  I eventually got sound configuration to show up by adding my user to group "audio".  But, though everything appears to work (permission problem though, with sound-juicer) and everything shows up in volume control, sound properties, etc, no sound comes from speakers (all tested and found working with Knoppix 4.0 Live). 

The card is SBLive! Value [CT4832], as reported in sound preferences.

No sound with Edgy Live, either, likewise everything is detected and configured, properly apparently, but I feel as though it's got to be some small configuration detail somewhere! 

As to possible causes, is there any control in alsamixer or other mixers that could cause no sound if off? I tried disabling "external amplifier" as reported here by some users but no fix :(  .

I've checked volume levels, all required seem to be up, mic & line are down, and nothing is plugged into them.

Sound-Juicer has a problem: "Sound-Juicer could not access the CD-ROM device '/dev/hdc' Reason: Permission denied" is the gnome error message.

If I try an aplay example, here is the result (no sound, of course):

johnpipe@linus:~$ !288
aplay /usr/share/sounds/alsa/Rear_Left.wav 
Playing WAVE '/usr/share/sounds/alsa/Rear_Left.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
underrun!!! (at least 0.398 ms long)
underrun!!! (at least 0.286 ms long)
johnpipe@linus:~$ 

Any good suggestions of where to look next?

Thanks, John

---

### Post by NeoLithium on 2006-11-05
Is everything in aslamixer unmuted?

---

### Post by johnpipe on 2006-11-05
Yes, everything.  I read in an archived post about SB Live! emu10k1 settings in alsamixer, to the right of setting ac97, but that was in Dapper, and those settings do not appear in Edgy.

---

### Post by johnpipe on 2006-11-06
After much googling with various phrasing, I finally found the sound-juicer problem; I needed to:

sudo gpasswd -a johnpipe cdrom

which fixed that part. Still, sound doesn't actually play :(

](*,) 

> **johnpipe said:**
> I had to install Edgy from the alternate install CD, as I could find no way to use the standard CD on a multi-distribution installation box.  I eventually got sound configuration to show up by adding my user to group "audio".  But, though everything appears to work (permission problem though, with sound-juicer) and everything shows up in volume control, sound properties, etc, no sound comes from speakers (all tested and found working with Knoppix 4.0 Live).
<SNIP>

Sound-Juicer has a problem: "Sound-Juicer could not access the CD-ROM device '/dev/hdc' Reason: Permission denied" is the gnome error message.

<SNIP>Thanks, John

---

### Post by sebastfr on 2006-11-06
Can you copy/paste '/etc/asound.conf' here? There are quite a few options you can set there.

Seb

---

### Post by johnpipe on 2006-11-06
> **sebastfr said:**
> Can you copy/paste '/etc/asound.conf' here? There are quite a few options you can set there.

Seb

Interestingly, /etc/asound.conf does not exist here:

johnpipe@linus:~$ ls /etc/asound.conf
ls: /etc/asound.conf: No such file or directory
johnpipe@linus:~$ locate asound.conf
/usr/share/gnome/help/desktopguide/sample/asound.conf_configuresoundproperly

It may not have been used in Edgy;

johnpipe@linus:~$ man asoundconf
Reformatting asoundconf(1), please wait...
<snip excess>
 ...
>
WARNING
       This program is under development.  Its features  will  change  without
       notice and without preservation of backward compatibility, except inso-
       far as they are put to use by other components  of  the  Debian  and/or
       Ubuntu  operating  systems.   (As of this writing the Ubuntu developers
       have plans to use asoundconf for setting the value of defaults.pcm.card
       from the system sound preferences menu.)
FILES
       ~/.asoundrc
              user-specific ALSA library configuration file

       ~/.asoundrc.asoundconf
              file containing asoundconf-managed parameter settings
>

Note that there is no mention of asound.conf here, nor does .asoundrc exist either:

johnpipe@linus:~$ locate .asoundrc
johnpipe@linus:~$ ls .as*
ls: .as*: No such file or directory
johnpipe@linus:~$ locate asoundrc
johnpipe@linus:~$ 

So, some one or more of these might be the culprit, but which files SHOULD exist in Edgy?

If it should happen not to be a missing configuration file (up to now, everything HAS been a configuration problem), then it would have to be a kernel bug, and I'm still betting on configuration as the culprit, but as the man page indicates, it's hard to tell what should or should not be in a default Edgy setup!

Thanks, John

---

### Post by tonymene on 2006-11-18
Any other developments on your sound problem?
I have a very similar problem with Ubuntu Edgy - SB Live! emu10k1 detected but no sound. 

I will list below some history on the problem. Bear with me, I am a newbie to Ubuntu/Linux.

1. My first distro install was Kubuntu Edgy. SB Live worked fine.
2. On a separate partition, I also installed Ubuntu Edgy to compare the two distros. SB Live card also worked fine.
3. Recently I had to reset the BIOS on computer. Forgot to disabled AC97 audio in BIOS as before.
4. Ubuntu and Kubuntu recognized AC97 as the default audio system in the computer. Switching the speacker cable to AC97 output, the sound would work fine.
5. Disabled AC97 from BIOS. SB Live is now the default audio device, but no sound comes out. Programs like Totem seem to be happy with the audio configuration, but ... no sound.

If anyone has any idea how to fix this problem please post.

---

### Post by johnpipe on 2006-11-19
What is that about diabling AC97? I've not seen this mentioned, does it have anything to do with getting the SBLive! to work? 

Unfortunately, there are several variations of SBLive! to confuse the issues. Mine is the "value" card (identical physically to SBLive! 5.1, except no CD SPDIF connector installed on the card (space is there, unpopulated)). This version has the five jacks, Analog/Digital out, line in, mic in, line out and rear spkr out.

johnpipe

---

