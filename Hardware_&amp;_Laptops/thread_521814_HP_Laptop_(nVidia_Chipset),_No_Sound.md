---
title: "HP Laptop (nVidia Chipset), No Sound"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by idrailgag on 2007-08-09
I just installed Feisty on my new *HP Pavilion 2125nr* (dv2000 series) laptop.  The laptop has an nVidia chipset with what is listed as a "*MCP51 High Definition Audio*" sound card in the Device Manager.

I have tried many suggestions from different threads such as updating the *alsa software/drivers*, trying different random combinations under the Sound Preferences, and *muting/umuting things in alsamixer*.

It appears as if everything is fine.  I can adjust the volume, press play in my different audio players but no sound ever comes out.  I have also tried the headphone jack, no luck.  Any guesses as to what I can do?

---

### Post by EXCiD3 on 2007-08-09
Hmm, thats odd as almost all the other HP laptops have audio working out of the box. You could give Gutsy a try and see if it works in that.

However you may want to try checking out this link first: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by fredj on 2007-08-10
First check the name of your soundchip and see if it has a driver loaded. Open a terminal
and type cat /proc/asound/card0/codec\#*
The first line of the output from that should tell you the name of the soundchip. Then also in a
terminal type sudo lshw -class sound and post the output from that here.

---

### Post by camini on 2007-08-13
Same problem here - and here's the output of suggested commands:

```
pmvdv@pmvdv-laptop:~$ cat /proc/asound/card0/codec\#*
Codec: Conexant CX20549 (Venice)
Address: 0
Vendor Id: 0x14f15045
Subsystem Id: 0x103c30b2
Revision Id: 0x100100
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x10 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0810014: OUT EAPD Detect
  Pin Default 0x95170110: [Fixed] Speaker at Int Top
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x2b 0x2b]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x62a1902e: [N/A] Mic at Sep Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
  Power: 0x0
  Connection: 2
     0x19 0x17*
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x21451130: [Jack] SPDIF Out at Sep Rear
    Conn = Optical, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x081124: IN Detect
  Pin Default 0x97a701f0: [Fixed] Mic at Int Riser
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x24: IN
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x54330121: [N/A] CD at Int Right
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x00:
Node 0x16 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x06]
Node 0x17 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x14, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-In vals:  [0x94 0x94] [0x94 0x94] [0x94 0x94] [0x94 0x94] [0x94 0x94]
  Power: 0x0
  Connection: 5
     0x19 0x14 0x12 0x11 0x15
Node 0x18 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x40]: 48000
    bits [0x6]: 16 20
    formats [0x5]: PCM AC3
Node 0x19 [Audio Output] wcaps 0xc11: Stereo
  PCM:
    rates [0x540]: 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: 0x0
Node 0x1a [Audio Input] wcaps 0x100d0b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x17, stepsize=0x05, mute=1
  Amp-In vals:  [0x17 0x17] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Power: 0x0
  Connection: 5
     0x17 0x14 0x12* 0x11 0x15
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
pmvdv@pmvdv-laptop:~$ sudo lshw -class sound
Password:
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: iomemory:d6400000-d6403fff irq:23
  *-usb
       description: Video
       product: USB 2.0 Camera
       vendor: Sonix Technology Co., Ltd.
       physical id: 5
       bus info: usb@5:5
       version: 2.10
       serial: SN0001
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480.0MB/s
pmvdv@pmvdv-laptop:~$
```

---

### Post by joshuachad on 2007-08-15
This fix works for most folks. It was posted by someone else on the forums. It worked on my HP DV2000 laptop. The alsa recompile didnt work for me. Follow the instructions below and let me know if it worked. Also when you go to the snapshot link download the latest version. There should be one for today since it is updated dialy.

downloaded the latest SUSE alsa snapshot driver from
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)
then execute the following commands in the terminal
$cd /directory where you downloaded the files to 
$tar xvf alsa-driver.tar.bz2
$./configure
$sudo make
$sudo make install

Cheers

--------------------------------------------------------------------------------------------------------------------

---

### Post by vsanghvi on 2007-08-22
I have the exact same problem and output from those commands as camini. I tried joshuachad's instructions but without any luck. Still get no sound, but buttons on my laptop seem to work fine. Playing around with alsamixer shows that everything should be working properly. If anyone here finds a solution, please let me know, and I'll do the same. Any and all help would be appreciated.

---

