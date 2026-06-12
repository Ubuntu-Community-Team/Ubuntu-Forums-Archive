---
title: "Simultaneous Sound Problems"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by Tylo on 2005-09-17
I have looked at the guides to get sound support for more than one application running at a time. I have been successful in getting an Alsa specific player to play two MP3 files at the same time, however, my goal is to give Skype the ability to ring when a call is in-bound and also be able to run a music player (preferabbly Quod Libet) whenever I'd like. I don't want the music playing while I am talking or anything like that, but would like to be able to listen to music without attending to the computer to watch for Skype to pop-up and tell me I have a call.

With my goal out of the way, allow me to give some specifics.

First, I have ALSA configured (to the best of my knowledge) and have followed this guide most prominently. ([http://www.ubuntuforums.org/showthread.php?t=32063&page=1&pp=10&highlight=Failed+construct+test+pipeline](http://www.ubuntuforums.org/showthread.php?t=32063&page=1&pp=10&highlight=Failed+construct+test+pipeline))

I have also attempted several modifications to the above tutorial (mostly in the asound.conf file) with no success.

It did not work for me, as Skype did not ring unless my music player was closed. Also worthy of note is that I cannot listen to Voicemails if a Quod Libet is opened (even if it is paused). I suppose this has something to do with Quod Libet, but if I can get simultaneous sounds working, then this won't be a problem.

Here is some technical info, which I hope may be of some help. This was taken from lsmod | grep snd:

```
snd_intel8x0           29984  19
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  19 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  19 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

```

Also, when I try to play XMMS when Skype is playing sound (for example, playing a voice mail message), I get this pop-up from XMMS:

[[IMG]http://students.cup.edu/coo9893/pics/thumb1.png[/IMG]](http://students.cup.edu/coo9893/pics/couldn't_open_audio.png)
Thumbnail^

I thought maybe this had something to do with Skype still using OSS (since I hear OSS only allows one application to play sound at a time). However, this is the only information I could find about what Skype is using as sound:

[[IMG]http://students.cup.edu/coo9893/pics/thumb3.png[/IMG]](http://students.cup.edu/coo9893/pics/skype_options.png)

Listed below is 
[list=1]
[*]My current AlsaMixer setting
[*]My current ALSA config for XMMS
[*]All the asound.conf configurations I have tried over the last several hours.
[/list]

[[IMG]http://students.cup.edu/coo9893/pics/thumb4.png[/IMG]](http://students.cup.edu/coo9893/pics/AlsaMixer.png)

[[IMG]http://students.cup.edu/coo9893/pics/thumb2.png[/IMG]](http://students.cup.edu/coo9893/pics/ALSA_driver_config.png)

**The first asound.conf config:***This was a configuration I had previous to my attempts at getting simultaneous sound output. I had this configuration in an attempt to get the sounds on Flash to sync, with success.*
```

pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP output device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```

**My second asound.conf configuration:**
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}

```

**My third asound.conf configuration:**
```

# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

```

**And finally, my current asound.conf configuration:**
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024	#1024
buffer_size 4096	#4096
periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}

```

---

### Post by Tylo on 2005-09-17
**Update**

It seems I won't be using Quod Libet after all. This program called "Music Player" (I assume it came default with Ubuntu) has the awesome filtering abilities I was so fond of in Quod Libet. Also, this "Music Player" seems to work with my ATI remote, making it all the more sweet.

I was able to get a further clue as to what's going on. This window appears when I try to play an MP3 with "Music Player" while listening to a voicemail on Skype simultaneously.

[img]http://students.cup.edu/coo9893/pics/Error.png[/img]

I thought ALSA was designed to handle multiple occurances and not clog up the Pipeline? Does anyone know what is going on?

**EDIT**
Haha, I just found out that this "Music Player" turns out to be the Rythmbox I hear so much about. Not a bad player, if I do say so myself.

---

### Post by Tylo on 2005-09-18
Would it help if I included this information?

```

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC '97 Audio Controller (rev 02)
```

---

### Post by Tylo on 2005-09-18
What if I threw in five bucks over paypal to sweeten the deal?

Where are all you sound gurus!?  :)

---

### Post by galileon on 2006-06-24
hello, did you figure it out? coz im trying it myself, and with no luck until now...I've posted on this thread: [http://ubuntuforums.org/showthread.php?t=203108](http://ubuntuforums.org/showthread.php?t=203108)
cheers

---

### Post by tyufi on 2006-07-26
I had the same problem formerly and after 2 weeks of searching the net I have found this: [http://mail.gnome.org/archives/gnomemeeting-list/2005-December/msg00227.html](http://mail.gnome.org/archives/gnomemeeting-list/2005-December/msg00227.html)

Now it is working - except for the recording is not loud enogh. But there should be solution for that.

I am listening to music - hearing the ringing of the skype - picking it up and talking.
I would not have belived it if someone had told me two days before.

Cheers!
\\:D/

---

