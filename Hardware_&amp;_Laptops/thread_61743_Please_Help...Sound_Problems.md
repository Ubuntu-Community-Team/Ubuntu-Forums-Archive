---
title: "Please Help...Sound Problems"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by makisupa123 on 2005-09-01
I have read every thread dealing with this on the board...my eyes are crossing.  I have an M-audio 24/96.  My board also has integrated sound ...which is turned off in the BIOS.  On a fresh reboot if I open the volume monitor i get the folowing error:

cannot connect to sound daemon
please run esd at command prompt

Ok, running esd at command prompt yields the following:

makisupa@semprOn:~$ esd
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.
makisupa@semprOn:~$

Here is my /etc/asound.conf:

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
period_size 2048
buffer_size 32768
periods 128
rate 4800
}
bindings {
0 0
1 1
}
}

Here is my /etc/esound/esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

My volume control on the panel does nothing.  THe Volume control shows the following devices:

Ice1712 multitrack (OSS Mixer)
M audio audiophile 2496 (Alsa Mixer)

That's encouraging...its the chip and the card.  alsamixer shows the card's channels (2)...levels are not muted.  Please help...I need this to be fixed and its driving me NUTS!!!

Thanks

/mak

---

### Post by makisupa123 on 2005-09-02
does anyone have an Maudio card working in Hoary?  If so, that would give me some hope  :???: 

I've literally been up all night working on this.....i'm getting desperate.

/mak

---

### Post by buddachile on 2005-09-02
I have the same audio card.  I tried to get audio to come out of the digital output but got nothing.  I opened the ALSA mixer, played around with ALL the controls, but nothing.   I haven't delved into trying to get the card working properly yet because I have too many other things to deal with first, but like you I am interested in any pointers on how to get this card working on a Hoary install.

I'll follow this thread and if I have anything to contribute I'll be sure to post.

---

