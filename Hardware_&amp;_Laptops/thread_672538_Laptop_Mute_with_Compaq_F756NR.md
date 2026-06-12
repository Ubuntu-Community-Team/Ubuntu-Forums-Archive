---
title: "Laptop Mute with Compaq F756NR"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by timsath on 2008-01-19
Hello, I've searched and searched, and I cannot figure out how to get my speakers to mute when I plug my headphones in.  I never even use the external speakers, but I can't even mute them using the alsamixer.  There are no separate channels for the headphones or external speakers.  

I tried both of these on the alsa-base file:

options snd-hda-intel model=laptop-hp
options snd-hda-intel model=laptop

I also compiled the alsa drivers from source, etc.  

I have everything else working, wireless, widescreen, etc...this is the last hurdle and then my ubuntu laptop will be working great :)

I'll post a HowTo on how to config this system when I figure this out.  Thanks to anyone who can help!

-Tim

**Clarification: ** Does anyone know how to just mute the external speakers?  If I had audio just playing through the headphones, that'd be great.  As it stands right now, I can hear audio through the external speakers and the headphones.  When I go to the mixer, all I have is Master and PCM, but I do have two different devices, the Conexant device, and the nVidia HDA device.  If I mute one, then it mutes the other.  I'm thinking I have the wrong driver installed for my card, and that's why I don't have a separate headphone slider, but who knows.  Again, thanks for any insight!

---

### Post by timsath on 2008-01-19
Also, my soundcard from lspci reads as: 
> 
Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

---

### Post by timsath on 2008-01-19
Does anyone think this might have something to do with Conexant hardware?

---

### Post by timsath on 2008-01-20
Ok, here's some more hardware info:

root@tim-laptop:/home/tim# hwinfo --sound
19: PCI 07.0: 0403 Audio device                                 
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55c
  Unique ID: M71A.fmA23IIoz13
  SysFS ID: /devices/pci0000:00/0000:00:07.0
  SysFS BusID: 0000:00:07.0
  Hardware Class: sound
  Model: "Hewlett-Packard Company Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055c 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30ea 
  Revision: 0xa1
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf6480000-0xf6483fff (rw,non-prefetchable)
  IRQ: 21 (312 events)
  Module Alias: "pci:v000010DEd0000055Csv0000103Csd000030EAbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by wolp on 2008-01-20
Yes I am having the same problem. I'm using a Compaq Presario c500 but it's basically just a low end HP laptop machine..I think it might be the port..since I always get bridge connection not found errors when I boot up. Hopefully someone can help us out in here, good luck to both of us.

---

### Post by timsath on 2008-01-20
> **wolp said:**
> Yes I am having the same problem. I'm using a Compaq Presario c500 but it's basically just a low end HP laptop machine..I think it might be the port..since I always get bridge connection not found errors when I boot up. Hopefully someone can help us out in here, good luck to both of us.

Yeah, I can't even find anything on the web really for my soundcard...let's hope a solution arises. :)  I'm sure it's something simple...

---

### Post by wolp on 2008-01-20
Yeah I have the same exact specs you have...The main thing is that it works and plays sounds lol

---

### Post by timsath on 2008-01-20
> **wolp said:**
> Yeah I have the same exact specs you have...The main thing is that it works and plays sounds lol

You don't have sound at all?  Mine plays fine through the headphones and external speakers, I just can't figure out a way to mute the external speakers.  It seems as if the laptop has an nVidia sound card, and a conexant soundcard??  I'm so confused...

---

### Post by link141 on 2008-02-28
> **timsath said:**
> I just can't figure out a way to mute the external speakers.  It seems as if the laptop has an nVidia sound card, and a conexant soundcard??  I'm so confused...

I have the same exact model laptop as you, and would like to get the headphone jack sense too.  Suspend, widescreen, wireless, the graphics, and everything else works great, this is really the last thing I want get working.

One thing I've noticed is that after suspending the laptop and waking it up, is that the headphone jack doesn't work until I reboot it...

With a sound card/integrated sound, you have two components: the chipset (which is made by nVidia, like the rest of the motherboard), and the audio codec, which is the actual sound chip that does the processing (apparently, this is made by conexant in our laptops).  AFAIK the only part the driver is really needed for is the codec.  I remember having a lot of trouble getting the sound to work on my sister's old thinkpad until I realized the codec wasn't detected correctly...

I remember stumbling upon a couple of different patches for headphone jack sense on conexant chips, but the one I tried on a live cd didn't work, and the other one is known to degrade audio quality...  I hope we can get headphone jack sense working properly.

---

### Post by NeoTaoistTechnoPagan on 2008-03-01
Found a patch for the F755US model - the specs are pretty much the same. I am working on this myself when I have time, but the patch method described fails on my system. I am working on manually applying the patch to the necessary source files.

Link:
[http://mailman.alsa-project.org/pipermail/alsa-devel/2008-January/005507.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-January/005507.html)

NTTP

---

### Post by link141 on 2008-03-16
Hey guys,

Good news, I fixed the problem.  All I did was recompile and install Alsa by following the directions at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) , using the 1.0.16 release of alsa, and then rebooting.  I didn't even have to apply the patch linked to by NTTP (thanks anyway, though), so that probably means you won't have to either.  Recompiling Alsa also added full support for my internal and external microphones.  Apparently, the patch for headphone jack sense is already included in the latest Alsa.  I now have a fully functional laptop, good deal!!

Hope this helps

---

### Post by h4mx0r on 2008-04-11
I followed that compiling guide and then upon reboot have no sound what so ever so I do modprobe snd-hda-intel.

modprobe snd-hda-intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

So I go to dmesg and endless whining about everything but the kitchen sink related to my card.

Now to trust that age old rule "those who write compile guides don't use a **CLEAN** environment without anything not installed by default but rather keep rewriting a half dead system kicking it until it works. Meaning somewhere in those 20 page of make output there is something missing." I think the issue occurs compiling alsa libs. when I do ./configure I get this:
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no     # that's it asking if some unknown thing accepts -g because its not installed LOL

later on I get it saying how python doesn't do a lot of needed stuff and I have no clue why its using python.
Perhaps some audio enthusiast wrote a guide about updating ubuntu 7.10 to .16 alsa which would yield more peer review, wish me luck kk.

---

