---
title: "I need a guru! (no joke)"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by ajpr on 2005-08-12
Seriously, this problem is driving me insane.  I just scrapped Debian and installed ubuntu over it, and still my problem exists!  OK here is the problem, follows by my questions:

Sound loads at startup but not all sound applications work.  Gnome sounds seem to work ok, like programs called Robots and the general event sounds (e.g. the sound that happens when you click on an icon that loads a program).  However, xmms refuses to work with OSS or ALSA, but does work with ESD.  Now I dont even know why there are 3 things for sound.  

So I select ESD in the multimedia systems selector, but in Music Player i get the error: "There is no element present to handle the stream's mime type audio/mpeg." 

If i select OSS, then music player says "OSS device "/dev/dsp" is already in use by another program."

If I select ALSA, then music player says "ALSA device "default" is already in use by another program."

I don't know why I get these error messages, but I know that when I do lsof /dev/dsp it comes up with ESD.  I'm not sure what the ALSA device default is, as default isn't exactly descriptive.

My hardware is:
SB16 pci
Hauppage WinTV
I managed to get them to load in Debian by using alsaconf and selecting my sound card and then doing modprobe bttv.  But I didn't like doing this every boot and furthermore i had no desktop sounds, just sounds from programs I configured to use ALSA.

Secondly, I have a tv card that doesn't seem to be loaded correctly...

This is all extremely annoying as I loaded the live cd and my tv card was showing up in the multimedia systems selector and the cd player worked fine etc.  

Currently I have MSS set to ESD and can hear the desktop fine, but not all programs work, e.g. MusicPlayer.

So my questions are:

1."Why are there so many sound systems, and how do they work, and whats the difference between them all?
2. "How do I fix this sound problem.  I basically just want the sound to work in the programs that came with ubuntu.  I don't understand why someprograms can be configured to work, like XMMS, but MusicPlayer doesnt work at all."
3.  "I tried apt-cache search tvtime and xawtv, but no results, even after running aptitude update, so, how do I get these?"
4.  "I'm not sure how much more I can take before i go insane :], do you think I need a padded cell?"

Thanks for ANY responses!

---

### Post by RastaMahata on 2005-08-12
1. [http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)
2. hope this helps: [http://ubuntuforums.org/archive/index.php/t-24586.html](http://ubuntuforums.org/archive/index.php/t-24586.html)
3. Add universe, multiverse, and why not, backports: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
4. Naaw, just have a bit of patience, everything has a solution ;)

---

### Post by ajpr on 2005-08-12
Thanks for the links, but they dont really help.  Ive done what it says and still Music Player does not work!  Where do I go from here?!!!  :-? 

How much time does it take to get the hang of this?  I've spent over 70 hrs probably at least half that on this one problem, which I cant seem to fix!

---

### Post by AgenT on 2005-08-12
It may be that the chip the sound card uses just does not work with Linux the way you want it to. Can't blame anyone but those that made the chip/sound card. The best idea is to do what I did a long time ago when trying to get an ancient and unsupported sound card to work: dump it and get a new one. Not an expensive one, just one that works with Linux. You can get a new sound card that has many features for about $20 shipped these days. $20 is not much for a working system and peace of mind. Just think how much you would have to fork down if you tried using an OS like OSX (you would have to buy a whole new computer!).

---

### Post by ajpr on 2005-08-12
[QUOTE=AgenT]It may be that the chip the sound card uses just does not work with Linux the way you want it to. Can't blame anyone but those that made the chip/sound card. The best idea is to do what I did a long time ago when trying to get an ancient and unsupported sound card to work: dump it and get a new one. Not an expensive one, just one that works with Linux. You can get a new sound card that has many features for about $20 shipped these days. $20 is not much for a working system and peace of mind. Just think how much you would have to fork down if you tried using an OS like OSX (you would have to buy a whole new computer!).[/QUOTE]
 So it may be he hardware that is at fault?  I hadn't considered that yet.  I'm sure things worked better on the Livecd, but I have no idea why....
I would spend some money on a newer sound card, but I am totally broke and cant afford it!  

I just created a new account and logged out of this one and into the new one.  I had zero sound and couldnt get any sound to come up with any amount of playing with the commands or gui.  I guess linux is just too complicated for me. I wish I was more intelligent, but most of this oss/alsa/esd makes very little sense to me.  and then theres the tv card problem, which i could get to work in debian by modprobe bttv and worked on the live cd, but for some reason doesnt work in ubuntu install!   

its frustrating as I don't know what to do still!  what should I have in the multimedia systems selector?  OSS/ESD or ALSA.  and why doesnt my tv card work in this install but it does on the livecd? 

p.s. I've read a lot, but still can't work it out, so I'm left with repeatedly asking on here until I get an idiots guide or i just give up and use windows!

---

### Post by AgenT on 2005-08-12
The problem is that people from Windows have this wacky expectation that every single piece of hardware must work with Linux or it's "crap". Much more hardware works with Linux than with Apple, yet no one says that Apple is crap because Windows-only hardware does not work with it. Same for Linux. Most of the Windows-only hardware *does* work on Linux, but some of it does not.

My point in suggesting to you that you should buy a new card is not that your card can't be made to work in Ubuntu because it probably can. My point is that your card is probably so badly handled that it's not worth the trouble in trying to get it to work and you should just buy a new one for $20.

Linux is *not* hard if you don't expect every single piece of hardware to work. No different than if you would try to use OSX.

That said, maybe someone here can help you with your card and get it to work. You said that your TV card worked before in Debian. Did you do anything to make it work? Because Ubuntu is based on Debian my guess would be that to make it work in Ubuntu should be simple. The problem is trying to find this simple solution (or having somone who knows the solution help you, see my tip part for help on this issue).

As far as the sound card not working. My initial guess as to what may be going on is that your sound card modules are not loaded. Maybe. What is the output of lsmod? Type this in the console/terminal: ```
lsmod
``` 

That may give someone a hint as to what is going on.

And a big tip: always use a relevent topic title!! Your "I need a guru! (no joke)" says nothing to anyone who may know the answer to your problem. Do you really expect everyone to click on your post because you ask for help and give no indication as to what you need help in? Most will just go to the next post. Someone that may know the answer will never even read your topic because of your title. Use a good title. Change it to something like "SoundBlaster 16 does not work: ESD works, ALSA & OSS does not".

And per your ALSA & OSS not working: this could be because ESD is "hogging" your sound card. This could either be ESD's fault or your sound card's (sound card not supporting more than one program using it - at least in Linux, although old sound cards were crippled like this in hardware). But ESD is known to be a pain sometimes and is actually scheduled to be replaced by something better in the next release of Ubuntu.

And just so you know: OSS was replaced by ALSA but it's still there for backward compatibility with programs. You should always try ALSA first in programs as it's usually better.

---

### Post by ajpr on 2005-08-12
[QUOTE=AgenT]The problem is that people from Windows have this wacky expectation that every single piece of hardware must work with Linux or it's "crap". Much more hardware works with Linux than with Apple, yet no one says that Apple is crap because Windows-only hardware does not work with it. Same for Linux. Most of the Windows-only hardware *does* work on Linux, but some of it does not.

My point in suggesting to you that you should buy a new card is not that your card can't be made to work in Ubuntu because it probably can. My point is that your card is probably so badly handled that it's not worth the trouble in trying to get it to work and you should just buy a new one for $20.

Linux is *not* hard if you don't expect every single piece of hardware to work. No different than if you would try to use OSX.

That said, maybe someone here can help you with your card and get it to work. You said that your TV card worked before in Debian. Did you do anything to make it work? Because Ubuntu is based on Debian my guess would be that to make it work in Ubuntu should be simple. The problem is trying to find this simple solution (or having somone who knows the solution help you, see my tip part for help on this issue).

As far as the sound card not working. My initial guess as to what may be going on is that your sound card modules are not loaded. Maybe. What is the output of lsmod? Type this in the console/terminal: ```
lsmod
``` 

That may give someone a hint as to what is going on.

And a big tip: always use a relevent topic title!! Your "I need a guru! (no joke)" says nothing to anyone who may know the answer to your problem. Do you really expect everyone to click on your post because you ask for help and give no indication as to what you need help in? Most will just go to the next post. Someone that may know the answer will never even read your topic because of your title. Use a good title. Change it to something like "SoundBlaster 16 does not work: ESD works, ALSA & OSS does not".

And per your ALSA & OSS not working: this could be because ESD is "hogging" your sound card. This could either be ESD's fault or your sound card's (sound card not supporting more than one program using it - at least in Linux, although old sound cards were crippled like this in hardware). But ESD is known to be a pain sometimes and is actually scheduled to be replaced by something better in the next release of Ubuntu.

And just so you know: OSS was replaced by ALSA but it's still there for backward compatibility with programs. You should always try ALSA first in programs as it's usually better.[/QUOTE]
 ok well, ive got some more info.  I realised I had to add the new user to the audio group, and for some reason that user could use OSS, even tho my current user cant.  Also, I did not realise that a SoundBlaster 16 PCI was out of the ordinary, in fact I thought it was a pretty basic card that's been a standard for many years.  

Ive tried killing all the sound things that were in the first link you gave me, but it did not help, so I assume ESD isn't hogging my card.  I also had similar problems in Debian which had no ESD installed.  

I don't expect windows hardware to simply work in Linux, but I do expect some sort of functionality when using a mainstream piece of hardware.  

Finally, alsa doesn't work in anything. I installed alsaplayer and this is the output:  alsaplayer
Failed to load output plugin "alsa". Trying defaults.

I am greatful for a free OS and I would be very willing to drop windows and work around the programs i wouldn't have using alternatives and things like Wine.  However, if my basic hardware isn't functioning i.e. Sound and Tv card, when I know it can work (livecd showed it working and I could get it working in Debian but it required me typing in commands after every boot), then I can't see how the OS is functioning.  And then I get annoyed.  Simply having things work is what counts.  I don't need a nice gui, I don't need things to work perfectly, I just need them to work.  Maybe I'm not human...

---

### Post by ajpr on 2005-08-12
heres my output:
```

antony@deepblue:~$ lsmod
Module                  Size  Used by
isofs                  33720  0
udf                    77060  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
snd_bt87x              12612  0
tuner                  20388  0
tvaudio                20512  0
bttv                  142928  0
af_packet              20744  2
video_buf              20484  1 bttv
firmware_class          9728  1 bttv
i2c_algo_bit            9224  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4744  1 bttv
snd_ens1371            22624  2
tsdev                   7488  0
snd_rawmidi            22944  1 snd_ens1371
snd_seq_device          8332  1 snd_rawmidi
snd_ac97_codec         64608  1 snd_ens1371
usbhid                 29376  0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_bt87x,snd_ens1371,snd_ac97_codec,snd_pcm_osssnd_timer              23300  1 snd_pcm
snd                    50276  9 snd_bt87x,snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_bt87x,snd_pcm
gameport                4608  1 snd_ens1371
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too
ohci1394               31876  0
i2c_i801                8076  0
i2c_core               21264  5 tuner,tvaudio,bttv,i2c_algo_bit,i2c_i801
ata_piix                8836  0
libata                 44548  1 ata_piix
ehci_hcd               29444  0
ov511                  73120  0
videodev                9728  2 bttv,ov511
uhci_hcd               30224  0
usbcore               107384  5 usbhid,ehci_hcd,ov511,uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_mch_agp          10000  0
intel_agp              20636  1
agpgart                31784  2 intel_mch_agp,intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  3 libata,sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  2
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  5
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  635
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

---

### Post by wvslkr on 2005-08-13
It appears your card uses the snd-ens1371module  look here  [http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=ens1371](http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=ens1371) for setup instructions.  At the bottom of the page it mentions the sb card. 

If you are lucky you may get away with a simple   sudo modprobe snd-ens1371   

Hope that helps you out.  Good Luck.

---

### Post by cobelloy on 2005-08-13
hi, don't know if you've worked it out yet, but I had an idea re: a new sound card - what about ebay, surely a second hand soundcard couldn't cost more than $5?

I have a pretty old yamaha card (DSXG) that never misses a beat, windows or linux, I got cheaply it off ebay a couple of years ago and it was old then.

sorry I can't actually help :(

---

### Post by ajpr on 2005-08-13
[QUOTE=cobelloy]hi, don't know if you've worked it out yet, but I had an idea re: a new sound card - what about ebay, surely a second hand soundcard couldn't cost more than $5?

I have a pretty old yamaha card (DSXG) that never misses a beat, windows or linux, I got cheaply it off ebay a couple of years ago and it was old then.

sorry I can't actually help :([/QUOTE]
 Well I tried the steps on alsa-project.org but I don't think it helped at all :(

And cobelloy I don't even have £5!  Also, I don't see how throwing money at the problem would help as soundblaster have been the most common sound card for a long time.

I guess if it doesn't work then there's not much left I can do.  Any recommendations for a different linux distro?  I'm thinking of SuSE, as I have redhat8.0 on my laptop (and yes that has sound problems aswell!).

---

### Post by AgenT on 2005-08-13
> I did not realise that a SoundBlaster 16 PCI was out of the ordinary, in fact I thought it was a pretty basic card that's been a standard for many years. 

You still don't get it. Just because it is standard on Windows does not mean it is standard on Linux. Go to the soundblaster website and look for Linux drivers. See any? What's that you say, "no"? Look, the company that made your card most likely not only does not support Linux but also refused to help anyone that was willing to create Linux support. And because it is an old card programmers have not slaved over it trying to get it to work (they have better things to worry about). You also have to realize that different hardware may have the same name. You may have some weird version of the SoundBlaster 16 PCI. It happens sometimes (this is actually pretty common in ethernet cards).

And seriously, you can't afford $8? You havethe luxury of a computer and an internet connection and you can't afford $8?

Also, when you paste, please use the code tags around when pasting results/code (there is a button to do this for you).

What is the result of:
```
lspci -v
```
This will show what hardware you have. Also the result of:
```
lspci -n
```
This will show the hardware ID numbers.

You still have not changed your topic to something meaningful. I guess you really don't really want others to help you.

---

### Post by ajpr on 2005-08-13
Seriously I can't afford $8, I have just come back from an expensive trip and having just finished uni i'm totally broke.  My total funds avaiable are £3.88 and then I  hit the limit of my overdraft.  I'm currently looking for work, which is why I have had the time to spend on linux.

```

Heres the lspci -v output:

0000:00:00.0 Host bridge: Intel Corp. 82875P Memory Controller Hub (rev 02)
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82875P Processor to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at bc00 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at b000 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at b400 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at b800 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at eb201000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: eb000000-eb0fffff
        Prefetchable memory behind bridge: eb100000-eb1fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at f000 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at c000 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c800 [size=8]
        I/O ports at cc00 [size=4]
        I/O ports at d000 [size=16]

0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: medium devsel, IRQ 11
        I/O ports at 0500 [size=32]

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0045 (rev a1) (prog-if 00 [VGA])
        Subsystem: LeadTek Research Inc.: Unknown device 2996
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 12
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1022
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at eb004000 (32-bit, non-prefetchable) [size=2K]
        Memory at eb000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at a000 [size=256]
        Memory at eb005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:06.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 22
        I/O ports at a400 [size=64]
        Capabilities: <available only to root>

0000:02:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: bus master, medium devsel, latency 32, IRQ 23
        Memory at eb100000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: medium devsel, IRQ 23
        Memory at eb101000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

```

And heres the lspci -n bit
```

0000:00:00.0 0600: 8086:2578 (rev 02)
0000:00:01.0 0604: 8086:2579 (rev 02)
0000:00:1d.0 0c03: 8086:24d2 (rev 02)
0000:00:1d.1 0c03: 8086:24d4 (rev 02)
0000:00:1d.2 0c03: 8086:24d7 (rev 02)
0000:00:1d.3 0c03: 8086:24de (rev 02)
0000:00:1d.7 0c03: 8086:24dd (rev 02)
0000:00:1e.0 0604: 8086:244e (rev c2)
0000:00:1f.0 0601: 8086:24d0 (rev 02)
0000:00:1f.1 0101: 8086:24db (rev 02)
0000:00:1f.2 0101: 8086:24d1 (rev 02)
0000:00:1f.3 0c05: 8086:24d3 (rev 02)
0000:01:00.0 0300: 10de:0045 (rev a1)
0000:02:02.0 0c00: 104c:8024
0000:02:05.0 0200: 10ec:8139 (rev 10)
0000:02:06.0 0401: 1274:5880 (rev 02)
0000:02:07.0 0400: 109e:036e (rev 11)
0000:02:07.1 0480: 109e:0878 (rev 11)

```

And I did try changing the topic, but it only changed the topic of the post and not the thread.  Not sure how to do that, couldn't figure it out.

---

### Post by varunus on 2005-08-13
Like someone else said, it looks like your card uses the snd-ens1371 driver.  Did "sudo modprobe snd-ens1371" in a terminal work?  After you try this command, can you give us the output of "lspci | grep snd" in a terminal?

To me, it looks like your hauppauge card is being seen as a sound card.  What you should do is first type the above commands and give us the output.  Then, follow this howto:
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

It describes how to set up two sound cards.

Your sound card is linux compatible!  It just needs some fiddling to get it to work...I can help you set up the correct asound.conf as described in the howto I linked you to if you need help.  After doing the modprobe, can you post the output of "cat /proc/asound/cards" in a terminal?  This will give you info on the number of sound cards you have and if they are being detected.

---

### Post by AgenT on 2005-08-13
Well, we found your first problem. You don't have a SoundBlaster PCI 16. Your soundcard is actually a Creative Sound Blaster Audio PCI 128 (it actually says "Ensoniq Creative Sound Blaster Audio PCI 128, which is probably the same thing). How did you learn that it was PCI 16? From what Windows told you? If so, never trust Windows. It says a lot of false/stupid things about your hardware. 

See [this links]("http://pciids.sourceforge.net/iii/?i=12745880") for details. (your hardware ID numbers are 1274:5880)

This means that you should go about trying to get your soundcard working as a PCI 128.

First thing is first. Rip out your TV card. It may be acting as your sound card instead of the SB.

You seem to be using the correct driver according to these two ALSA pages [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Ensoniq&card=.&chip=ES1371%2C+ES1372%2C+ES1373%2C+CT5880+%28ES1373%29&module=ens1371"). and [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Ensoniq+AudioPCI.&chip=ES1371&module=ens1371"). (one was found under Creative the other Ensoniq)

My guess would be the TV card is stealing your sound card duties.

EDIT: see varunus' post above.

---

### Post by ajpr on 2005-08-13
Well I did sudo modprobe snd-ens1371 in a terminal and then ran music player but i still had no luck.

The output of lspci | grep snd is nothing! It just goes onto the next line.

```

This is the output of cat /proc/asound/cards
0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xa400, irq 22

```


As I said before I have some sounds working, using ESD, within Gnome.  I also think its confusing my TV Card for a sound card as it lists it in the devices in the Volume Control.  To get this working in Debian, I would run alsaconf which unloaded all the sound drivers and only load the ones for my sound card.  Then I could modprobe bttv and use my tv card.  However, I did not have any desktop sounds in Gnome and I wanted things to work from bootup without me having to go through those steps after every reboot!

---

### Post by ajpr on 2005-08-13
[QUOTE=AgenT]Well, we found your first problem. You don't have a SoundBlaster PCI 16. Your soundcard is actually a Creative Sound Blaster Audio PCI 128 (it actually says "Ensoniq Creative Sound Blaster Audio PCI 128, which is probably the same thing). How did you learn that it was PCI 16? From what Windows told you? If so, never trust Windows. It says a lot of false/stupid things about your hardware. 

See [this links]("http://pciids.sourceforge.net/iii/?i=12745880") for details. (your hardware ID numbers are 1274:5880)

This means that you should go about trying to get your soundcard working as a PCI 128.

First thing is first. Rip out your TV card. It may be acting as your sound card instead of the SB.

You seem to be using the correct driver according to these two ALSA pages [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Ensoniq&card=.&chip=ES1371%2C+ES1372%2C+ES1373%2C+CT5880+%28ES1373%29&module=ens1371"). and [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Ensoniq+AudioPCI.&chip=ES1371&module=ens1371"). (one was found under Creative the other Ensoniq)

My guess would be the TV card is stealing your sound card duties.

EDIT: see varunus' post above.[/QUOTE]
 I'm not convinced I have a SB PCI 128, and I'd rather not take my tv card out, if that's possible!  But hmm maybe I do have a SB 128, hmm :]

---

### Post by AgenT on 2005-08-13
[QUOTE=ajpr]I'm not convinced I have a SB PCI 128, and I'd rather not take my tv card out, if that's possible! But hmm maybe I do have a SB 128, hmm :][/QUOTE] Well your hardware says you have a PCI 128 by the #'s it gives. What else do you need to be convinced? But right now that does not matter because it seems like you are supposed to use the same ALSA driver for both 128 and 16. Although you should always keep in mind that you have a 128 just incase.

Can you please edit your post with the module list and put the list in code tags because right now the longer lines run into each other and it's hard to figure out what is what. And the longer lines deal with your sound card.

And why don't you wan't to take out your TV card? It's not that hard. You are just making it hard on those that are trying to help you by not taking it out.

---

### Post by ajpr on 2005-08-13
Ok I just did Varunus's ideas, and followed the thread he posted.  Now ESD doesnt work, but OSS does and ALSA doesnt (withint the multimedia system selector).  I have no Gnome sounds! Although I can get XMMS to output to OSS and get sound !

So maybe musicplayer is screwed? Or is everything messed up as I kept my /home/ partition from Debian?

Surely I want ALSA to work, isn't it strange that OSS works?  Although it's annoying that the Gnome sounds have gone!


p.s. I now have sounds in flash !  IS there a way to get gnome to use OSS?

---

### Post by AgenT on 2005-08-13
[QUOTE=ajpr]So maybe musicplayer is screwed? Or is everything messed up as I kept my /home/ partition from Debian?[/QUOTE]

Your problem seems to be your sound configuration, not the music player. And yes, keeping your /home/ partition could be the couse of it. Actually, not really your home partition, but the left-over config files you may have in your home partition that may be overwritting all your sound settings.

One thing you can do before you go out on a config deletion hunt is to create a new user (give this user admin rights!) and login as that user from now on until you get your sound working.

---

### Post by ajpr on 2005-08-13
Yes well, I just reinstalled ubuntu, wiping all my old stuff!

I now have ESD working, but ALSA and OSS dont.  However the good news, is that my tv card is being picked up in the MSS.  Also when i logged in, an update manager popped up and installed a load of updates.  

I think I am just going to keep it as it is, and use ESD, as that seems to work ok, even though I have not heard much of it!

Thanks for all your help guys.  I guess in the future, I will buy hardware that is compatible for linux and go from there :]

Anyway, I'm gonna try and leave it alone for a bit, I've spent way too much time this last week trying to understand linux!

---

### Post by AgenT on 2005-08-13
Just so you know, it may be possible to have every program use ESD: even ones that do not support it. There is some esd program in the repositories that does this but it takes some extra (maybe too much) processor power to use. I have used it before but do not remember the name. If you have all official repositories enabled (not counting backports) just type esd and check the description of everything that comes up.

You start it like so:
<this esd program> <maybe an argument/option or two> <the program you want to use esd>

Not very descriptive but it should help if you want to try that route (it was actually very easy to use).

---

### Post by varunus on 2005-08-15
If you've got ESD working, you can get OSS and/or ALSA working.  Try installing libesd-alsa0 from synaptic (or libesd0-alsa, i can't remember what its called) and then reboot; does your sound still work?

If it does, I can show you how to get ALSA running...

---

### Post by ajpr on 2005-08-16
Hi varunus.  I did what you said and installed that package.  I still have sound, but only ESD makes any sound in MSS.  So how do I get ALSA working? :]


**Update**
After installing that package, Music Player now works!  So I think it helped a lot!

---

### Post by varunus on 2005-08-16
So you have the Multimedia Systems Selector working with ESD but not with ALSA or OSS.

OK, this is a fixable problem.

First, open up synaptic.  Do you have the "gstreamer0.8-alsa" package installed?  If not, you should install it.  Also, install the "alsa-oss" package if you don't have it.  Also the "esound-clients" package.

Neither of these should affect your sound output.

Next, open up a terminal.  Type the following command:
```
esdplay /usr/share/sounds/login.wav
``` 
You should hear the ubuntu login sound.

Next, try the following:
```
aplay /usr/share/sounds/login.wav
``` 
This tries to play the sound through ALSA.  Do you hear anything?  Or does the program freeze, and wait for you to CTRL-C out of it?

Post back here with your results from those two commands.

---

### Post by Movikun on 2005-08-16
ok, let me lay down this for you, since i had the excact same card when i was just starting with Linux, just the ISA version. Ive also been using alsa, since the 0.9. days, in hopes of getting my then flakey card to work. 

You problem is : your card can't do more than one stream at a time. See, it works like this:

OSS is the OLD Sound system for linux. you shouldn't be even using it. Under it, you sound card creates some nodes, mainly /dev/dsp, and /dev/mixer (/dev/sequencer for midi if you actually got around using/setting it up). The problem with that was : one application controlled one node. If your card only supported ONE stream, there would only be one node. 

Youll probably say now : "But in windows this wan't a problem". Yes, youre correct. Ever wondered what DirectSound was for? Bingo - software mixing. Your CPU was mixing all of the applications and then laying it to the card.

Linux people got around this problem, by creating software mixers. KDE had aRts, Gnome had esd (or maybe it was E16 derived - i don't remember), and there were some others. Problem was - all of them sucked. This hasn't changed pretty much today.

Also, one more thing. Ubuntu by default comes with esd installed and running. This means that the esd deamon is already taking up your soundcard TOTALLY. Only esd has access to the soundcard while it's running soo in order to get sound from applications you need to get them to talk to esd.

You can also kill the esd deamon

sudo killall esd

Or turn it off in the gnome preference (somewhere in sound i believe, since it's been a while since i used Gnome)

After this, your alsa/oss stuff will automagically start to work - but under one condition - only one at a time. If let's say xmms is playing, then another app that tries to use your soundcard will either fail or hang until you give it your soundcard

So came Alsa. The all brand new Sound System. Under it, there no longer is a /dev/dsp and programs talk to libao (Library Alsa Output) which then gives the sound to the hardware. But it DOESN'T mix the sound. Well, not by default. The fact that we're streaming the sound thru thru a library, which then gives it to the kernel, enables us to do many wacky stuff along, like changing the Hz rate (there are cards which support ONLY 48kHz, and everything that goes to them has to be mixed to that kHz),

So there is a plugin in libao called dmix. Yes, it IS a software mixer, but different in nature than the rest. Appplications don't need to support ANYTHING except output to alsa (i believe OSS thru alsawrapper should work perfectly also, at least the docs say so, but again - you shouldn't be using OSS). 

There's this one thing about dmix though - i can't help you set it up. Why you ask?

I had enough waiting and frustration about software mixing. Got my butt up, bought a SB Live! (paid only 20Eur for it - cheap!) which has hardware mixing up to 32 channels ! (more than youre ever going to need!) and some extra goodie-goodies. And from that point on, i didn't EVER have to worry about mixing. I could run esd (2 channels) aRts (2channels ) JACK (2 channels) an IM client(2 channles - for a sound bell!) and an alsa media player (2 channels) = that's 10 channels and you still have 22 reserve! No more sound problems for me.

So my final advice (hope you got to this point) - you can if you want to play, but it's just damn easier getting a decent card. Theyre cheap nowadays! You can get the Live! for a price of a McDonalds Meal ;)

Best of Luck

P.S. : now if someone would answer my questions as good as this.... ;P

---

