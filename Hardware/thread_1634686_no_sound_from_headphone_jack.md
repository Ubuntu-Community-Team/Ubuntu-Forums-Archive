---
title: "no sound from headphone jack"
date: 2010-11-30
forum: Hardware
---

### Post by sk8rjess on 2010-11-30
i'm getting a little annoyed at jumping onto windows just to listen to music through my sound system.
i'm using an alienware m17x and cannot for the life of me get the headphone jacks to work, although i get sound through my laptop speakers. 
also, i'm running ubuntu 10.10
any ideas?

---

### Post by killa.fr0gg on 2010-11-30
How much of a beginner are you? If you have any trouble with what I'm about to say, repost and let me know. Here we go:

From main menu, select Applications->Accessories->Terminal

When that open, type "alsamixer" without the quotes and hit Enter.

You'll be greeted with a semi-UI that looks much like a mixer (imagine that!). Chances are, you will see a muted channel somewhere in that. Use the left and right arrow keys to highlight the muted channel, and press the M key to unmute it.

Press esc to exit alsamixer.

Test.

Report back here!

Cheers!

---

### Post by sk8rjess on 2010-11-30
not horribly, i've learned alot in the last few weeks and learning is pretty much natural for me.
i never knew i would see graphics in a terminal! ha.
but nope, nothing was muted :\

---

### Post by killa.fr0gg on 2010-12-01
Are you certain? I only ask that you make sure because this is the *much* easier way of fixing your problem if it can be done this way. The thing is, too, that the indicator for mutedness in alsamixer is somewhat overlookable. Run alsamixer one more time and make sure there are no channels with an "mm" underneath. If not, well we'll see where to go...

---

### Post by sk8rjess on 2010-12-01
Yes sir, positive.

since the screenshot is huge, i'll just link it so it doesn't goof up the forums formatting.
**[screenshot]("http://i74.photobucket.com/albums/i245/sk8rjess/Screenshot.png")**

---

### Post by killa.fr0gg on 2010-12-01
Type this into a Terminal:

ubuntu-bug audio

---

### Post by sk8rjess on 2010-12-01
unfortunately, that didn't help. i submitted a bug report. ugh.
i had the same issue a couple months ago when i installed 10.04 but didn't use ubuntu enough to worry about it.

here's the lspci if it helps
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:05.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 3 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc M98 XT [Mobility Radeon HD 4870]
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
03:00.0 VGA compatible controller: ATI Technologies Inc M98 XT [Mobility Radeon HD 4870]
06:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
08:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
08:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
08:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
08:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

---

### Post by sk8rjess on 2010-12-01
fixed. if anyone else has this issue, here is the fix:

1.) Add the ppa for the new alsa driver modules
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```

2.) Download driver modules
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

3.) Open the alsa config file to edit it..
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

4.) And now add this to the end of the file
```
options snd-hda-intel model=alienware
```

Save, Reboot, and all should be good :)
thanks Daniel T Chen (crimsun)

---

### Post by RebateFX on 2011-05-19
Hey another Alienware M17x user! :)

On mine, the headphones are muted by default in Kubuntu 11.04. Unmuting in Alsamixer fixes that.

---

### Post by sk8rjess on 2011-05-19
rare aren't we :D

---

### Post by BeatnikStrict on 2012-08-05
Hi.. 

I'm new to Linux OS but I love, love it..

I had a problem with my headphone socket. I followed the above instructions via terminal..  it sorted my problem straight away :)

I know what caused my problem:

I installed Lexicon Alpha drivers for win. through the cheeky little Wine program..  Had no problems there really apart from my own daftness.  When I then went to play music through Clementine, it played through the laptop speakers but not through headphone socket..

Like I say, I followed the above instructions and now its fine..  I just wondered if somebody might be able to explain to me in laymen terms why this happened and if this will happen each time I use the Lexicon?

Thanks so much..
BNS

---

