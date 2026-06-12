---
title: "Sound out of BOTH headphone jack and built-in speakers on HP Pavilion dv6700"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by sevensevens on 2008-01-24
I just purchased an HP pavilion dv6700 and put Gusty on it.  Almost everything worked out of the box, but when I plug in a headphone to listen to music, the built in speakers don't mute.  I've installed ALSA 1.0.15 (from source from the alsa site), and fiddled with the blacklist to allow all the alsa drivers.  Its an nVidia sound card - here's the lspci output

lspci | grep 'Audio'
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

I've read in other topics that there is suppose to be a "jack sense" option in alsamixer, but I don't have that button.  I also don't have separate volume controls for headphone jack and built in speakers.

Here's my alsa-base file
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# I've also tried "laptop" and "lenovo"
options snd-hda-intel model=snd-intel8x0

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by cdtech on 2008-01-24
Everyone with "nVidia Corporation MCP67 High Definition Audio (rev a1)" seem to have the same issues. I as well have the same setup 

If the switch their talking about is this:

[ATTACH]57387[/ATTACH]

then that doesn't work.

I've heard by building the alsa-driver-hg20080124.tar.bz2 using the --with-cards=intelxxxx flag from : [[COLOR="DarkRed"]hg project[/COLOR]]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/") corrects the problem but I haven't had a chance to experiment with this.

I do know that typing ./configure --help will give you a list of options to use.

If anyone has, let me know. When I have some time I'll try and let you know, or you can let us know.

---

### Post by sevensevens on 2008-01-24
I tried compiling the link (normal ./configure, make), but I got some errors.  Among them was "c:96: error: ‘system_utsname’ undeclared (first use in this function)", is thes uname -r for suse?

---

### Post by sevensevens on 2008-01-24
BTW, has anyone submitted a bug report on this?

---

### Post by cdtech on 2008-01-24
Good question!

I'll have a look see.

---

### Post by ugm6hr on 2008-01-24
> I've read in other topics that there is suppose to be a "jack sense" option in alsamixer, but I don't have that button. I also don't have separate volume controls for headphone jack and built in speakers.

This is an issue for lots of Linux users.  I don't seem to have a jack sense on my Acer5051AWXMi laptop either.

However, you generally *can* independently adjust volumes in:
```
alsamixer
```

There is an alsamixer gui package in the repo if you prefer - I used to have that in my panel to allow easy swaps.

If you get the jack sense thing sorted - let me know!

---

### Post by sucker on 2008-01-24
sup sevensevens i just want to ask you something about other stuff sorry, i have a dv6458 and i was wondering if did you fixed the problem with the suspend and hibernation settings, did you? and could yoiu tell me how if u did it? thanks

---

### Post by sevensevens on 2008-01-25
@Sucker
Haven't bothered fixing the hibernation bug yet - my first goal is getting the sound issues worked out.

@ugm6hr
I only have 3 sliders in alsamixer (text & gui) master, pcm, and capture.  I think its an issue that the nVidia sound driver is not reporting to alsa correctly - I'm just not that familiar with the alsa system.

---

### Post by cdtech on 2008-01-29
After lengthy searches and howto's I finally have my headphones working correctly. I have an HP Pavilion dv9608nr, dual hard drives (one specifically for Ubuntu). I tried to keep records of my procedures as I went along.

These are the steps that I took ::

Find your Subsystem Id::
```

cat /proc/asound/card0/codec#0
```

Results ::
```

Codec: Conexant CX20549 (Venice)
Address: 0
Vendor Id: 0x14f15045
**Subsystem Id: 0x103c30cf**
Revision Id: 0x100100
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x10 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x9f 0x9f]
  Pincap 0x0810014: OUT EAPD Detect
  Pin Default 0x95170110: [Fixed] Speaker at Int Top
    Conn = Analog, Color = Unknown
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 2
     0x19* 0x17
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
  Pin-ctls: 0xc0: OUT HP
  Power: 0x0
  Connection: 2
     0x19* 0x17
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
  Amp-Out vals:  [0xab 0xab]
  Pincap 0x08113c: IN OUT HP Detect
  Pin Default 0x40a190f0: [N/A] Mic at Ext N/A
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x20: IN
  Power: 0x0
  Connection: 2
     0x19* 0x17
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x22451130: [Jack] SPDIF Out at Sep Front
    Conn = Optical, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x081124: IN Detect
  Pin Default 0x02a79120: [Jack] Mic at Ext Front
    Conn = Analog, Color = Pink
  Pin-ctls: 0x24: IN
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
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

```

sudo /etc/init.d/alsasound stop

sudo gedit /usr/src/alsa/**$YOUR ALSA-DRIVER DIRECTORY**/alsa-kernel/pci/hda/patch_conexant.c

Find the line that looks like this and insert your Subsytem ID as I did here :: 
**SND_PCI_QUIRK(0x103c, 0x30cf, "HP DV9608nr", CXT5045_LAPTOP),**

cd /usr/src/alsa/**$YOUR ALSA-DRIVER DIRECTORY**/alsa-kernel and compile with ./configure --with-cards=hda-intel --with-card-options=hda-codec-conexant

I also installed ::
```

sudo apt-get install modconf

sudo modconf

Find the line ::
**kernel/sound/pci/hda**
and install snd-hda-intel
in the options put **model=laptop**

```

Check the alsa-base file and make sure its ok (/etc/modprobe.d/alsa-base). I had to comment out the old line I had in there, making sure to leave the new line modconf inserted.

Reboot.

Hope this helps......

EDIT----This is a bit off topic ::  I still have a problem with my alsasound. When I boot I have to alsasound restart in order to get video's to work or even Skype for that mater. Does anyone have any issues with this as well?

---

### Post by 3dOptics on 2008-01-29
I posted this in another thread. This might work for you too.

I was having the same problem with my sager np2090 in Ubuntu Gusty. I fixed it by going to System, Preferences, Sound, and under "Default mixer tracks" click PCM. (The reason to do this is so that PCM will control the volume for both front and headphones.) Then close the window. Now double click on the sound icon in the system tray, then from the edit menu, click on preferences, check "off-hook", then close. Now a tab labelled "switches" will be displayed, click it and check "off-hook". On the "playback" tab, max out the volume on headphones and front. Pressing the volume keys on your keyboard should slide up and down the PCM slider. Now if you plug in your headphones your system speakers will mute, unplug them and your system speakers will turn back on. Dont move the front slider up or down when you have headphones plugged in because it will turn on the system speakers while you are using your headphones. Only control volume with the PCM slider or the volume keys on your keyboard.

Oh almost forgot, if you had your headphones plugged in when you did those steps above, then unplug them now, and replug them in.

By the way my laptop uses Intel HD audio

---

