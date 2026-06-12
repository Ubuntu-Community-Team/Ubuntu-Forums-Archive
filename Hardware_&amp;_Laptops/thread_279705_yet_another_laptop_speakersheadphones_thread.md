---
title: "yet another laptop speakers/headphones thread"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by spiderworm on 2006-10-18
Hi all,

Plugging in headphones.  Sometimes it switches the audio to the headphones, sometimes it doesn't.  Sometimes it mutes the laptop speakers, sometimes it doesn't.  Sometimes I can get volume ONLY from the headphones, as if my laptop speakers had spontaneously broken.  I've searched the forums and found a lot of people posting that they have the same or similar problems.  However, their solutions do not work for me.  I do not have a "headphone sense" option in the mixer anywhere.  Adding "options snd-hda-intel model=z71v position_fix=1" to /etc/modprobe.d/alsa-base didn't help.

Here's some system info:

-------------------------------------------

Dell Inspiron 9400

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]


uname -a:
Linux silversurfer 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

lsmod | grep snd:
snd_hda_intel          20468  6
snd_hda_codec         166096  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

-------------------------------------------

It seems like a lot of people are having this trouble with the Intel sound chipsets.  Could this be a driver issue?  Is there a way to manually route the audio through headphones or speakers without a "headphone jack sense" option?

Thanks in advance for any help.
spiderworm

---

### Post by spiderworm on 2006-10-19
bump

---

### Post by TorchlightJay on 2006-10-19
I have a similar problem. I have a Core 2 Duo and am using Dapper. I get sound on my speakers but they are crappy and my Kmix has less features than I have ever had before. Also, when I plug in my headphones, it doesn't swith over. intel-hda-snd is my card. What is the deal? Anyone have any clue. 

I was told to reinstall ALSA, it works for some people but not me. You can try it.

[http://www.linux-on-laptops.com/forum/showthread.php?t=286](http://www.linux-on-laptops.com/forum/showthread.php?t=286)

---

### Post by wylie348 on 2006-10-23
Same here HDA-intel 82801G only sound from headphones not speakers on laptop - Fujistu T4210.
Looked around for awhile and tired of trying things like re-installing alsa and then getting not sound period!  Total re-install and things are back to headphones, but speakers sure would be nice.
:confused:

---

### Post by maniacmartin on 2006-10-27
I have a HP nx6325 laptop running Dapper

I have noticed that on my machine

If the headphones are plugged in during boot-up then audio works only works on the headphones and not the laptop speakers, even if the headphones are unplugged.

If the headphones are not plugged in during boot-up then ubuntu will always use the speakers. If I then plug the headphones in after booting, I get sound out of the headphones AND the speakers.

It seems to me that the sound drivers seem to remember on my laptop the state of the headphone jack when the drivers are initialised.

Ideas?

---

### Post by MHD on 2006-11-05
Me too!
Inspiron 6400
with Intel 82801G

Sound works perfectly but no headphone sense so speakers do not mute when I use headphones...

Very annoying...
I'm using Kubuntu Edgy

---

### Post by MHD on 2006-11-05
Oh yeah... I should add neither alsamixer or kmix have jack sense switches...

---

### Post by tajmox on 2006-11-11
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME)
worked for me

also try not plugging the jack in all the way (2/3)

---

### Post by jpyanowski on 2006-11-13
> **spiderworm said:**
> Hi all,

Plugging in headphones.  Sometimes it switches the audio to the headphones, sometimes it doesn't.  Sometimes it mutes the laptop speakers, sometimes it doesn't.  Sometimes I can get volume ONLY from the headphones, as if my laptop speakers had spontaneously broken.  I've searched the forums and found a lot of people posting that they have the same or similar problems.  However, their solutions do not work for me.  I do not have a "headphone sense" option in the mixer anywhere.  Adding "options snd-hda-intel model=z71v position_fix=1" to /etc/modprobe.d/alsa-base didn't help.

Here's some system info:

-------------------------------------------

Dell Inspiron 9400

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]


uname -a:
Linux silversurfer 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

lsmod | grep snd:
snd_hda_intel          20468  6
snd_hda_codec         166096  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

-------------------------------------------

It seems like a lot of people are having this trouble with the Intel sound chipsets.  Could this be a driver issue?  Is there a way to manually route the audio through headphones or speakers without a "headphone jack sense" option?

Thanks in advance for any help.
spiderworm

I wish I could offer some sage advice. I have a 2002 HP Omnibook XE3 GF and I have no issues with either the laptop speakers or headphones. I'm listening to Tom Petty on last.fm because my wife is testing our daughter for a school test tomorrow. Hope you find a solution to the problem.

---

### Post by maniacmartin on 2006-11-15
i did a fresh install with Edgy and its fixed here now

---

### Post by poco3000 on 2006-12-06
Ok, I know this is old by now - but I thought I'd add my 2 cents.

I added the line "options snd-hda-intel model=hp position_fix=1" (without quotes) into "/etc/modprobe.d/alsa-base"

I finally have my onboard speakers working on my nx6325!

---

