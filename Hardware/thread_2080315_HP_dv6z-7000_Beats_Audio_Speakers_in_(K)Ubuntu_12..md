---
title: "HP dv6z-7000 Beats Audio Speakers in (K)Ubuntu 12.10?"
date: 2012-11-03
forum: Hardware
---

### Post by CalcProgrammer1 on 2012-11-03
I got myself a dv6z-7000 a few months ago.  This is the AMD Trinity version of HP's 15.6" laptop lineup and it comes with HP's Beats Audio technology (2 main speakers above keyboard, two tweeters below LCD, and one subwoofer facing out under the laptop).  It works fine in Windows and I had it sort of working in 12.04 (with the "model=ref" option) though that broke headphones.

I reinstalled it with Kubuntu 12.10 as I wanted to move to KDE and wanted a clean system.  It's back to two speakers and working headphones.  The Beats speakers really improve sound quality out of the laptop when not using headphones and I'd like to get it working.

I have tried the snd-hda-intel model=ref option again but it did not change anything.  I have run the alsa-info.sh script, here is my output:

[http://www.alsa-project.org/db/?f=3c89e273beb52ac4ca57389050662841ab2b29c0](http://www.alsa-project.org/db/?f=3c89e273beb52ac4ca57389050662841ab2b29c0)

This is on a fresh 12.10 Kubuntu install, and I previously had Ubuntu 12.04 which had similar problems.  Any help would be greatly appreciated!

---

### Post by CalcProgrammer1 on 2013-02-03
OK!  I figured it out!  It sounds *awesome*!

Step 1:  Install hda-jack-retask from here: [https://launchpad.net/~diwic/+archive/hda](https://launchpad.net/~diwic/+archive/hda) (ppa:diwic/hda)

Step 2:  Open hda-jack-retask

Step 3:  Select the IDT 92HD91BXX codec (may be different on other models)

Step 4:  Check the "Show unconnected pins" box (the internal speakers do not show as connected)

Step 5:  Remap 0x0d (Internal Speaker, Front side) to "Internal speaker"

Step 6:  Remap 0x0f ("Not connected" but is the under-display speakers) to "Internal speaker"

Step 7:  Remap 0x10 ("Not connected" but is the subwoofer) to "Internal speaker (LFE)"

Step 8:  Apply now, then test with your favorite audio program (some may not work due to Pulse reset, so find one that does, verify sound is coming from all speakers).

Step 9:  If it works, select "Install boot override" to save the settings to apply at boot time.

Step 10:  Reboot.  When it comes back, you should have full sound from all speakers.  Also test headphones.  Plugging in headphones should disable sound from all internal speakers.

[[IMG]http://i.imgur.com/iLZsMJCl.jpg[/IMG]](http://imgur.com/iLZsMJC)

---

### Post by MarcoDePollo on 2013-02-04
Thank you for this, it worked perfectly on my HP Envy.

---

### Post by TPMF on 2013-02-05
I have just tested your method on the HP Pacilion dv6 with beats audio (I am unsure of the detailed model number).
The speakers work wonderfully after your fix!
However, after applying it I realized the the headphones no longer worked. After playing around for a bit the way to fix this is to:
[LIST]
[*]Check "Show Unconnected Pins"
[*]Override 0x0c (I know it is listed as a mic, but it controls the two headphone jacks for what ever reason)
[*]Select "Line out (Front)" from the drop box
[*]Apply
[*]Test
[*]Install boot override
[*]Reset your computer and ensure it worked.
[/LIST]

---

### Post by w96 on 2013-03-07
Thank you so much for this, this was the only thing holding me back from using Linux full time. For anyone with an HP DV7 6c95dx or similar model, here's the configuration.
[IMG]http://i.imgur.com/0TBIZ74.png[/IMG]

---

### Post by DarkSwordmaster on 2013-05-14
Thanks! It worked for me, I have a HP Pavilion dv7-4165dx and this is the best audio configuration I've found so far. Subwoofer doesn't seem crashed whith high volume, 5 speakers working and they disable when I plug headphones on. Thanks again for sharing the solution.

---

### Post by ferd on 2013-05-21
Does not work on 13.04. Config cannot be saved. Save file does not exist. Created save file but does not work with VLC and does not work with keyboard controls and eliminates almost all options from Phonon. Not advised.

---

### Post by xav42 on 2013-06-05
I have a HP Envy 17 (3070nr) running Kubuntu 13.04.

hda-jack-retask found the codec IDT 92HD91BXX.

I am able to remap everything as mentionned without errors, but it does not change anything : only the two front speakers are working. Also, I don't see any "Speaker1" in AlsaMixer...

I also noticed that after appying the changes, the Phonon-PulseAudio integration is lost : "PulseAudio Sound Server" is the only device showed in Phonon. So I have to manually launch start-pulseaudio-kde to get the Phonon-PulseAudio integration back.

Anything I could try ?

---

### Post by xav42 on 2013-06-06
To all that succeeded to get the 4 speakers + subwoofer working in 12.10, please can you confirm it still works in 13.10 ?

Thanks.

---

### Post by russomarco on 2013-10-26
I own a HP Envy 14 Spectre. I followed the steps but it seems to me that nothing changes, and I don't see any "Speaker1" in AlsaMixer. The only change is that in the Sound settings I see a new profile, [COLOR=#000000][FONT=verdana]"Analog Surround 4.0 Output", but if I select this nothing changes, the subwoofer is still grey, and if I try to do a test sound only the two front speakers work... Any suggestion?

EDIT: The weird thing is that with thedefault configuration (without using hda-jack-retask), if I try to do a speakers test through [/FONT][/COLOR]```
speaker-test -c5 -l1 -twav
``` I get 5 working speakers:

```
speaker-test 1.0.25


Playback device is default
Stream parameters are 48000Hz, S16_LE, 5 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 39 to 419430
Period size range from 12 to 139810
Using max buffer size 419428
Periods = 4
was set period_size = 104857
was set buffer_size = 419428
 0 - Front Left
 1 - Front Right
 2 - Rear Left
 3 - Rear Right
 4 - Center
Time per period = 9,273190

```
But If I go to Sound settings or in alsamixer I only have two speakers...

---

### Post by chris270 on 2014-07-30
I just tried this on my dv6 7227sa, however, it broke my sound. I'm currently at step 8, but my sound doesn't work at all. The icon is now a speaker with 3 dots following and neither Chrome, nor gmusicbrowser will do anything to change it. I even tried to set it back to the original options and that has now caused a lack of sound.

I'm not sure what to do, but I'm sure I did it all correctly.

**Edit: **I found that if I go into a program that would normally give me sound, it lights up red. Even after restarting, so I think this may have come from an earlier step...

---

### Post by thehud on 2014-08-27
I've managed to get sound from all speakers here, in 14.04, but they're only playing sound from the front center channel. Is there any way to use hdajackretask to map the speakers to at least the left and right channels, or even better, left and right and front and back, for a surround 4.1 setup?

This is on an HP Envy touchsmart 17, if it helps.

Cheers,
Hud.

---

### Post by christophelol on 2014-10-29
.

---

### Post by leandronn on 2014-11-03
> **thehud said:**
> I've managed to get sound from all speakers here, in 14.04, but they're only playing sound from the front center channel. Is there any way to use hdajackretask to map the speakers to at least the left and right channels, or even better, left and right and front and back, for a surround 4.1 setup?

This is on an HP Envy touchsmart 17, if it helps.

Cheers,
Hud.

Hi, this is the configuration I used in my HP ENVY Touchsmart 15-j173cl, Ubuntu 14.04 / 14.10

[IMG]http://www.protecciontotalsa.com.ar/hdajackretask.png[/IMG]


Now, I hear FRONT RIGHT/LEFT and REAR RIGHT/LEFT.

Hope this helps.

REgards,


LN

---

