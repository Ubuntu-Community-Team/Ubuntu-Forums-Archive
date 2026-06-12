---
title: "Mic capture problems"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by sindrejh on 2008-04-21
Hello,
I know that I'm not the first person asking for this. But I have (for some years) been trying to get my microphone working, no one of the other solutions in other threads have worked for me.  As mostly of the other people posting about such problems, I can get the sound from the mic on the speakers. But I'm not able to capture the sound.

I've tried a lot of different options in the sound-controller, but nothing works. Nothing really happens when I push the record button.

My computer is an Acer Ferrari 1000, and I'm running Hardy RC, but the problem has been the same both in Feisty and Gutsy. I'm imaging that I got the capture to work at an live CD one time, but I'm not sure at all.

Lspci | grep Audio gives:
```
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

```

aplay -l gives:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And my alsa-base file looks like this:
```
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
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

I've also attached some screenshots; sound-control and alsamixer. Sorry that the words in the screenshots are in norwegian, but I didn't manage to find out how to easily change that before making the shots. I can try to translate if thats necessary.

Thanks in advance, for any help and advices you can give me.

---

### Post by alex941021 on 2008-05-09
Same exact problem with a ferrari 5000.  When I booted 7.10 from live CD, the microphone worked like a charm.  I compared everything  (versions, loaded modules, and even kernel boot parameters, alsa parameters), and everything seems to be similar.  There has to be something else going on.  Maybe the kernel from Live CD was compiled with different options.

---

### Post by sindrejh on 2008-05-12
Good to hear that it isn't just me. But can somebody help?

---

### Post by mitya89 on 2008-05-17
I'm having a similar problem to this. I'm using 8.04 (Hardy) on an Acer Aspire 5100 series (5100-5840) notebook. It has the same sound card you listed.

---

### Post by alex941021 on 2008-06-29
Has anyone had any luck with this problem?

---

### Post by sindrejh on 2008-06-29
I'havent. Hopefully some others have...

---

### Post by alex941021 on 2008-06-29
Today I was looking at this thread:

[http://209.85.141.104/search?q=cache:77EE4QaivZMJ:ubuntuforums.org/showthread.php%3Ft%3D616845+ubuntu+ati+sound+card+microphone+not+working&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://209.85.141.104/search?q=cache:77EE4QaivZMJ:ubuntuforums.org/showthread.php%3Ft%3D616845+ubuntu+ati+sound+card+microphone+not+working&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a)

and tried different "options snd-hda-intel model=..." variations,
specifically those indicated under the "ALC883/888" section.  I've even tried commenting out other unrelated drivers (i thought that maybe there was a conflict of some sort), but no luck.  The test program I've used is skype.  Well it is so frustrating, as I think it has to be something very simple that keeps the capture from working.  I can definitely hear my voice through the speakers, or headset, so this tells me that the hardware is recognized correctly and it works fine.  However, the applications fail to grab that input somehow.  Skype allows you to select the input source, and I've tried all possible combinations with no avail.  Also, I've made sure that the mixer's properties were set correctly, capture sources, and volume levels....

---

### Post by alex941021 on 2008-06-29
I was also reading these threads:

Approach 1:
[http://www.linuxquestions.org/questions/linux-hardware-18/realtek-alc883-record-sound-wont-work-597317/](http://www.linuxquestions.org/questions/linux-hardware-18/realtek-alc883-record-sound-wont-work-597317/)

or approach 2:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/80531](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/80531)


does any of the stuff works for anyone?

---

