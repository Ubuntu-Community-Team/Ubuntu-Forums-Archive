---
title: "Ubuntu and ASUS M50 version notebooks"
date: 2008-09-16
forum: Hardware
---

### Post by cfaulkner on 2008-09-16
I've seen a few posts about this particular model.  My son has one and i'm busy trying to get it to work correctly.  Here are the problems i'm having with this.

His laptop is Model: M50VM-X1
Version: Hardy Heron 8.04.1

I was able to install nVidia graphics drivers via EnvyNG only by going into console, typing "envyng -t" as root.  ( sudo envyng -t )

If you don't have envyng, i would suggest turning on the 3rd party repositories and at console type ( apt-get install envyng )

I did the manual driver install, took a minute or two and it was done.  Rebooted, all was well.

Wireless does not work.

Wired eth0 does not work.  rmmod r8169 and then a modprobe r8169 reveals in the /var/log/messages that the driver does indeed load, but errors out with an Error -22.  I assume that this driver is not correct.  Proper googling on this particular issue reveals that the driver has not made it into 2.6.26 kernel but it is in the 2.6.27 kernel right now.  I don't dare rebuild a kernel on Ubuntu.

I'm going to load Gentoo on this to see if I can get 2.6.27 kernel on it and see what happens, i'll report back with my findings.  If anyone else has anything to offer on this subject, please post your findings and what exact model you have.

Thanks!

EDIT:  Update.  Loaded Gentoo 2008.1 on it and with 2.6.24 kernel on the minimal isntall disc, it found the wired ethernet port just fine.  Hrmm

---

### Post by cfaulkner on 2008-09-16
Ok, Tried to load Gentoo 2008.1 but it seems the ethernet comes and goes as it pleases.  Had a little problem trying to load it so i'm going to try a few new things shortly.

---

### Post by cat bar on 2008-10-04
Hi!  I am running Intrepid Beta on a M50Vm-B2 and I can confirm that wireless does indeed work with the 2.6.27 kernel.  However, you will probably have to delete a file in /etc/acpi/start.d called something like '60-asuswirelessled.sh' as it causes the hardware RF kill switch to be permanently engaged.

Everything works well for me except I am having a strange problem with the DVD-ROM drive 'hanging' and becoming unreachable, for example while trying to burn .iso files or trying to install ubuntu from cd.  Sometimes it will work and sometimes not, and it is NOT a burn quality issue:).

Would be interested to know if you or anyone else has run into this issue, I am currently investigating it...

---

### Post by R0r0 on 2008-10-15
> **cat bar said:**
> Hi!  I am running Intrepid Beta on a M50Vm-B2 and I can confirm that wireless does indeed work with the 2.6.27 kernel.  However, you will probably have to delete a file in /etc/acpi/start.d called something like '60-asuswirelessled.sh' as it causes the hardware RF kill switch to be permanently engaged.

Everything works well for me except I am having a strange problem with the DVD-ROM drive 'hanging' and becoming unreachable, for example while trying to burn .iso files or trying to install ubuntu from cd.  Sometimes it will work and sometimes not, and it is NOT a burn quality issue:).

Would be interested to know if you or anyone else has run into this issue, I am currently investigating it...

About your DVD-Rom drive, it works for me : There is an option for the drive in the Bios (F2 at the startup), you must change it from "Enhanced" to "Compatible" and there won't be any problem from now :)

---

### Post by Gilles.t on 2008-10-23
I'm experiencing this problem with my DVD on M50VM AS010C 
The otpion of bios switch SATA to IDE mode for both drives (hard disk and dvd rom). This worry me for hard disk.
Any other fix for this bug? 


Thanks

---

### Post by felyduw on 2008-10-24
Are there bug reports about the wireless and dvd issues ?

Thanks

---

### Post by Gilles.t on 2008-10-25
I've made a bug report for dvd issue

[https://bugs.launchpad.net/ubuntu/+bug/289261](https://bugs.launchpad.net/ubuntu/+bug/289261)

gilles

---

### Post by felixnine on 2008-11-09
does anyone have any updates on these issues now that intrepid has come out? i'm very much considering picking up one of these, despite the glossy screen.

---

### Post by RaZe42 on 2008-11-10
Basic functions work well. My M50VM's intel 5100 wifi works out of the box, light sensor also seems to work. The fingerprint sensor should work with fprint, but some people have advised against it so I haven't tried it. Also the "dual mode" thingie on the touchpad doesn't work

---

### Post by Maximinus on 2008-11-15
RaZe42, are you able to give us the full model number of your M50VM?  I'm looking at getting an M50VM-AS001G, but I was worried when I googled around before Intrepid's release by reports of the wireless not being supported.  Is anybody able to shed some light on whether the M50VM-AS001G is any good under Intrepid?

Cheers,
Max

---

### Post by Katas on 2008-11-17
Hi guys,

I have a m50vn and i cant set the sound working.. Could you guys please help me? Thanks.

---

### Post by Maximinus on 2008-11-18
I've just ordered an Asus M50VM-AS001G.  It should arrive tomorrow, so I'll post again when I have it and can verify what does/doesn't work.

Wish me luck!

-Max

---

### Post by Gilles.t on 2008-11-19
For the sound problem

Can you post the output of this command?

cat /proc/asound/card0/codec\#* | grep Codec

---

### Post by RaZe42 on 2008-11-19
EDIT: double post, see below

---

### Post by RaZe42 on 2008-11-19
Sorry for the late reply.
My laptop is an Asus M50VM-AS009C with an Intel 5100 wifi chip
[http://www.fonepoint.fi/PublishedService?file=page&pageID=9&itemcode=M50VM-AS009C](http://www.fonepoint.fi/PublishedService?file=page&pageID=9&itemcode=M50VM-AS009C)

The only problems I seem to be having now is that I can't get loud sound from the speakers (or headphones) and I also have the same bug as in the M50SV that when you plug in headphones sound still comes out of the speakers. But I'm sure that's an easy fix

---

### Post by Maximinus on 2008-11-19
> **RaZe42 said:**
> when you plug in headphones sound still comes out of the speakers.

It is indeed an easy fix - you just need to manually upgrade to alsa 1.0.18a (I had the same problem).  There's a [handy script available]("http://ubuntuforums.org/showthread.php?t=962695") from soundcheck that does all the work for you - just be prepared to let it download a reasonable amount of stuff if you don't already have relevant tools such as build-essential, g++ and various -dev packages.


Hope that helps,
-Max

---

### Post by Katas on 2008-11-20
I Still whitout sound.. does someone know where i can find a tutorial how-to install alsa? i get an error when i make the command make instal. thx

i get the following output from the comand: 

Codec: Realtek ALC663
Address: 0
Vendor Id: 0x10ec0663
Subsystem Id: 0x10431893
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x2c 0x2c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x02 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400700: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081003c: IN OUT HP EAPD Detect
  EAPD 0x0:
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081003c: IN OUT HP EAPD Detect
  EAPD 0x0:
  Pin Default 0x0121441f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0834: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x0810: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x081734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a19840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x99a3094f: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x081734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x0820: IN
  Pin Default 0x598301f0: [N/A] Line In at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x0814: OUT Detect
  Pin Default 0x99430130: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x01211420: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x13
Codec: LSI ID 1040
Address: 1
Vendor Id: 0x11c11040
Subsystem Id: 0x10431636
Revision Id: 0x100200
Modem Function Group: 0x1
Codec: Generic 10de ID 6
Address: 2
Vendor Id: 0x10de0006
Subsystem Id: 0x10de0101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x0814: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x0814: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x0814: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x0814: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x0814: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c


thx..

---

### Post by Gilles.t on 2008-11-20
You may try this if you are using alsa 1.0.17

gksudo gedit /etc/modprobe.d/alsa-base

add this lines to the end of file:

options snd-hda-intel model=3stack-dig position_fix=0


alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

save and restart

hope it helps you as it did for me

[edit]:If you upgrade to 1.0.18 the problem should be fixed (I just did it and it works well!!)

Gilles

---

### Post by Gilles.t on 2008-11-20
hi!
I'm still looking for some fixes for my laptop M50VM

- DVD drive doesn't work really (firts disk inserted mount but second one doesn't) 

- loud beeps on boot with usplash (so I actually boot on text mode)

- fprint-demo crash when trying to enroll fingerprints

- I'm on single boot intrepid (astalavista vista!), I tought splashtop was on ROM in some chip, but there were some files on drive. Anybody knows how to install it on ubuntu?

Thanks.

Gilles

---

### Post by Maximinus on 2008-11-22
Gilles, I was getting the loud beeping on startup until I upgraded to Alsa 1.0.18a - and then I thought it was gone, but it still seems to happen occasionally.  There doesn't seem to be any pattern to it - at first I thought it beeped only if I had headphones plugged in while it was booting, but since then it's been pretty much 50/50 as to whether it beeps or not, without headphones.  I'm guessing there's something still not quite right with alsa - I might try playing with the options tomorrow, and will post again when I've checked.

As for the DVD drive, I haven't tried mine - although I did notice that when I booted into Ubuntu after installing, and I still had the disc in the drive, it didn't seem to want to stop spinning the disc... and it seems to be doing something with the drive repeatedly during startup, then settles when the login screen comes up.

I am, however, happy to report that the card reader seems to work perfectly - at least with SD/SDHC cards.  My old laptop's card reader was a bit iffy - sometimes it'd just cut out in the middle of a transfer for no reason.

Also, if anybody has managed to work out xmodmap config that will turn the menu key into a Super_R, could you please share this with me?  I tried using xkeycaps, but I ended up with it being some kind of weird double-modifier key that doesn't actually do anything of value.

One last thing - I use (and love) Amarok, and I've found that it'll only save state if I manually exit it before shutting down - whereas on 7.10 on my old laptop, it got closed nicely on shutdown and so it saved state.  The gnome session manager also doesn't seem to save state, even with the box ticked, so I wonder if these are connected somehow?  If anybody has any insight on that, it would be much appreciated.


~Max

---

### Post by Gilles.t on 2008-11-22
Hi!

Maximinus, since last updates (daily + alsa 1.0.18a) I've noticed also some changes.
Still having beeps, randomly, on approx. 1 of 3 boot with usplash, but it beep not so loud and no so long it did before.(?)

Fprint-demo seems to work better, I don't know which package fixed this.

What about splashtop for you? Are so still in double boot with vista?
If you are, can you identify the files needed by splashtop.
I have made an image of my vista partition in which I could maybe get back the files without restoring it on my laptop.

I'm not using amarok yet, going to try this.

):P from the other side of earth

Gilles

---

### Post by Gilles.t on 2009-03-01
Hi!

Some good news for Asus M50VM Users.

DVD: The issue come from the drive firmware (should be >RR05 to work)
*sudo lshw -class disk* will let you know which one you have. If it's RR04 you should contact Asus for RMA

Sound: Works perfectly with alsa1.1.18a 
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Expressgate:create a small FAT32 partition(ex:3GB).Download from asus and install expressgate on a computer under windows(works on virtualbox).Copy the expressgate folders and files on the new FAT32 of your laptop (**asus.000**,**asus.sys**,**splash.idx**,**version**, they are hidden files on root of the installation drive).
Get UUID of your FAT32 drive ex: *sudo vol_id  /dev/sda4*.
Edit (as root) splash.idx and replace UUID by the new one.
That's it!

---

### Post by luckyluca on 2009-03-03
what about the sata mode in the bios?
does ubuntu install and run ok with sata set to optimal?

Thanks
L

> **Gilles.t said:**
> Hi!

Some good news for Asus M50VM Users.

DVD: The issue come from the drive firmware (should be >RR05 to work)
*sudo lshw -class disk* will let you know which one you have. If it's RR04 you should contact Asus for RMA

Sound: Works perfectly with alsa1.1.18a 
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Expressgate:create a small FAT32 partition(ex:3GB).Download from asus and install expressgate on a computer under windows(works on virtualbox).Copy the expressgate folders and files on the new FAT32 of your laptop (**asus.000**,**asus.sys**,**splash.idx**,**version**, they are hidden files on root of the installation drive).
Get UUID of your FAT32 drive ex: *sudo vol_id  /dev/sda4*.
Edit (as root) splash.idx and replace UUID by the new one.
That's it!

---

### Post by Gilles.t on 2009-03-04
As I wrote in previous message, the issue come from DVD firmware.

Temporary fix is to turn SATA mode to enhanced in the bios, or use an USB drive to install Ubuntu...or buy a new drive. 
Samsung SN-S083B is compatible (cf Peter klotz ref in launchpad link below)

[https://bugs.launchpad.net/bugs/289261](https://bugs.launchpad.net/bugs/289261)

If your drive has the bad firmware you should contact Asus for RMA.
The issue exists on windows vista and 7, this can be an argument for RMA.

ex: [http://www.sevenforums.com/drivers/1819-dvd-drive-problem.html](http://www.sevenforums.com/drivers/1819-dvd-drive-problem.html)

---

### Post by SketchyClown on 2009-03-14
I have the ASUS M50VM-A1.

The DVD/CD drive issue has to do with the BIOS setting for the drive.

I am currently on v.209 firmware from ASUS but this worked fine under v.207 as well.

Change the BIOS setting for the optical drive from ***Enhanced*** to ***Compatible*** and you should find all the issues with the drive under Ubuntu are now gone and the drive works properly.

I don't understand resorting to trying to get a RMA from ASUS for an issue like this.

---

### Post by SketchyClown on 2009-03-14
For all of you with ASUS laptops out there, this is an excellent site with a wealth of good information to help anyone who wants to use Linux on ASUS hardware.

[http://www.linlap.com/wiki/asus](http://www.linlap.com/wiki/asus)

Scroll down until you find your model.

Read some of the user comments as well.

Helped me a lot with my A1.

Cheers.

---

### Post by nbo10 on 2009-03-19
> **SketchyClown said:**
> .

Change the BIOS setting for the optical drive from ***Enhanced*** to ***Compatible*** and you should find all the issues with the drive under Ubuntu are now gone and the drive works properly.

I don't understand resorting to trying to get a RMA from ASUS for an issue like this.

The issue is you end up using IDE interface instead of SATA. I don't think you can use the esata port with the compatible mode.

---

### Post by ^[H3ad-Tr1p]^ on 2009-06-23
had you upgrade your m50 from hardy to jaunty?

had you have some problem?

my system is not usable with jaunty but only with intrepid

---

### Post by ^[H3ad-Tr1p]^ on 2009-07-01
help

---

### Post by Maximinus on 2009-07-01
Hi,
My M50Vm is currently awaiting repair, as it suddenly stopped being able to draw power from the power adapter.  As such, I haven't yet had a chance to try the upgrade (from Intrepid) to Jaunty - but I'll be giving it a go once I get it back.

-Max

---

### Post by Lod on 2009-07-02
> **'^[H3ad-Tr1p]^ said:**
> my system is not usable with jaunty but only with intrepidI've had an upgraded system when Jaunty was beta. Now I have a clean install of the official release. In both cases it worked almost flawlessly except for some occasional freeze ups probably connected to the ext4 filesystem (although I haven't had one for weeks now).

What are your problems exactly?

---

### Post by ARam1024 on 2010-02-20
I have the M50VM-B2 and had that DVD issue until about 30 minutes ago.  After countless hours of searching for a good fix, I found one by **xblack86** [here]("https://bugs.launchpad.net/ubuntu/+bug/289261").

You can download an unofficial version of firmware RR07 for the GSA-T50N [here]("http://files.rpc1.org/index.php?act=view&id=5619"). I installed the file in vista, and that fixed the issue.  I'm not sure if you'll be able to do it in WINE.

The CD portion of "sudo lshw" follows (note that it's version RR07):

description: DVD-RAM writer
product: DVDRAM GSA-T50N
vendor: HL-DT-ST
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrwlogical name: /dev/scd0
logical name: /dev/sr0
version: RR07
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=nodisc

---

