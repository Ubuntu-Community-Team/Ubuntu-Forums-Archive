---
title: "VIA VT1708S on Natty"
date: 2011-08-06
forum: Hardware
---

### Post by headvampyre@hotmail.co.uk on 2011-08-06
Hi, I'm running a VIA VT1708S(Stock sound card on ASRock P43DE) under ubuntu 11.04.

I've got an issue when using surround sound thoug, but im not sure if its a bug, so im gonna ask here if theres a solution first.

Basically, when using 5.1 surround (Or 7.1, etc.), as soon as I change surround mode in the Gnome sound preferences, my Subwooofer is fine for the track I'm playing, but as soon as i change track, or terminate the connections to ALSA, the Subwoofer's volume changes to a minumum(Theres no preference for this, and its not logged as far as I know). 

Does anyone have any experience with this card under ALSA, or am I gonna have to buy a new one?

---

### Post by headvampyre@hotmail.co.uk on 2011-08-07
*BUMP* Does anybody use this chip? D=

---

### Post by headvampyre@hotmail.co.uk on 2011-08-07
This is starting to get even weirder. ALSA appears to be fine, and I know ALL of my hardware is as well :/ I've just installed Mixxx, and the Subwoofer works fine, but only when using 1 - 2 channels, anything above and the Subwoofer is ignored, even though center works fine. :/ Any ideas?

---

### Post by headvampyre@hotmail.co.uk on 2011-08-08
Okay, firstly, thanks for any support guys...
On the bright side, I've sorted this issue, and it appeared to be down to the Ubuntu configuration(What a suprise...), so, heres my configurations to get 5.1 surround sound working on ubuntu. If it already works, skip to step 3(Just the enable-lfe-remixing)

So...:

1) Create a file ~/.asoundrc (The root of your home directory)
2:) For snd-hda-intel insert the following(This may work for other devices, just change "snd-hda-intel" to your sound driver):

#!!! CAN BE DELETED IF CONFIGURATION ISSUES OCCUR !!!#

# 2008-11-15
#
# This .asoundrc will allow the following:
#
# - upmix stereo files to 5.1 speakers.
# - playback real 5.1 sounds, on 5.1 speakers,
# - allow the playback of both stere(oupmixed) and surround(5.1) sources at the same time.
# - use the 6th and 7th channel (side speakers) as a separate soundcard, i.e. for headphones
# (This is called the "alternate" output throughout the file, device names prefixed with 'a')
# - play mono sources in stereo (like skype & ekiga) on the alterate output
#
# Make sure you have "8 Channels" and NOT "6 Channels" selected in alsamixer!
#
# Please try the following commands, to make sure everything is working as it should.
#
# To test stereo upmix : speaker-test -c2 -Ddefault -twav
# To test surround(5.1): speaker-test -c6 -Dplug:dmix6 -twav
# To test alternative output: speaker-test -c2 -Daduplex -twav
# To test mono upmix: speaker-test -c1 -Dmonoduplex -twav
#
#
# It may not work out of the box for all cards. If it doesnt work for you, read the comments throughout the file.
# The basis of this file was written by wishie of #alsa, and then modified with info from various sources by 
# squisher.

#Define the soundcard to use
pcm.snd_card {
type hw
card 0
device 0
}

# 8 channel dmix - output whatever audio, to all 8 speakers
pcm.dmix8 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "snd_card"
rate 44100
channels 8
period_time 0
period_size 1024
buffer_time 0
buffer_size 5120
}

# Some cards, like the "nforce" variants require the following to be uncommented. It routes the audio to t he correct speakers.
bindings {
0 0
1 1
2 4
3 5
4 2
5 3
6 6
7 7
}
}

# upmixing - duplicate stereo data to all 6 channels
pcm.ch51dup {
type route
slave.pcm dmix8
slave.channels 8
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

# this creates a six channel soundcard
# and outputs to the eight channel one
# i.e. for usage in mplayer I had to define in ~/.mplayer/config:
# ao=alsa:device=dmix6
# channels=6
pcm.dmix6 {
type route
slave.pcm dmix8
slave.channels 8
ttable.0.0 1
ttable.1.1 1
ttable.2.2 1
ttable.3.3 1
ttable.4.4 1
ttable.5.5 1
}

# share the microphone, i.e. because virtualbox grabs it by default
pcm.microphone {
type dsnoop
ipc_key 1027
slave {
pcm "snd_card"
}
}

# rate conversion, needed i.e. for wine
pcm.2chplug {
type plug
slave.pcm "ch51dup"
}
pcm.a2chplug {
type plug
slave.pcm "dmix8"
}

# routes the channel for the alternative
# 2 channel output, which becomes the 7th and 8th channel 
# on the real soundcard
pcm.alt2ch {
type route
slave.pcm "a2chplug"
slave.channels 8
ttable.0.6 1
ttable.1.7 1
}

# skype and ekiga are only mono, so route left channel to the right channel
# note: this gets routed to the alternative 2 channels
pcm.mono_playback {
type route
slave.pcm "a2chplug"
slave.channels 8
# Send Skype channel 0 to the L and R speakers at full volume
ttable.0.6 1
ttable.0.7 1
}

# 'full-duplex' device for use with aoss
pcm.duplex {
type asym
playback.pcm "2chplug"
capture.pcm "microphone"
}

pcm.aduplex {
type asym
playback.pcm "alt2ch"
capture.pcm "microphone"
}

pcm.monoduplex {
type asym
playback.pcm "mono_playback"
capture.pcm "microphone"
}

# for aoss
pcm.dsp0 "duplex"
ctl.mixer0 "duplex"

# softvol manages volume in alsa
# i.e. wine likes this
pcm.mainvol {
type softvol
slave.pcm "duplex"
control {
name "2ch-Upmix Master"
card 0
}
}

#pcm.!default "mainvol"

# set the default device according to the environment
# variable ALSA_DEFAULT_PCM and default to mainvol
pcm.!default {
@func refer
name { @func concat 
strings [ "pcm."
{ @func getenv
vars [ ALSA_DEFAULT_PCM ]
default "mainvol"
}
]
}
}

# uncomment the following if you want to be able to control
# the mixer device through environment variables as well
#ctl.!default {
# @func refer
# name { @func concat 
# strings [ "ctl."
# { @func getenv
# vars [ ALSA_DEFAULT_CTL
# ALSA_DEFAULT_PCM
# ]
# default "duplex"
# }
# ]
# }
#}

3) In /etc/pulse/daemon.conf, change the following lines(make sure you uncomment them aswell):

default-sample-channels = 6
(Use 6 for 5.1 or 8 for 7.1)

enable-lfe-remixing = yes

As I have said, Make sure you uncomment those two lines, just remove the "; " in front of the lines.

4) Goto terminal and run "sudo killall pulseaudio" without the quotation marks.

5) Goto the speaker applet in the top right of the panel, select sound preferences, then goto Hardware, then at the bottom of the window, theres a selection box, change it to the type of surround you are using :)

6) Enjoy the bass :D

---

