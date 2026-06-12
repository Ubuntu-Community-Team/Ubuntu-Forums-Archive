---
title: "HDMI nvidia 310m"
date: 2010-12-22
forum: Hardware
---

### Post by robalrr on 2010-12-22
Hi, I have a Dell Vostro 3400 laptop with a nvidia GeForce 310M I have no achieved that the hdmi audio works.

I have an Ubuntu 64 10.10 with alsa 1.0.23+dfsg-1ubuntu4.

I have audio from the laptop speakers but not for the hdmi output when I connect it to my tv, when I select the High Definition Audio Controller from the list in the sound preferences. I tested the computer with win 7 and the hdmi audio worked.

Also with aplay -Dplughw:1,7 -t raw -f cd song.raw I can hear the music in the tv. But with other applications I can't listened nothing. I tried selecting the output module for Alsa in VLC properties and selecting the HDA NVidia:NVIDIA HDMI (hw:1,7) but I didn't get audio from my tv.

lspci -v gave me this output
[FONT="Courier New"]01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Dell Device 0440
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fb080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel[/FONT]

aplay -l
[FONT="Courier New"]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 [/FONT]

I read a many forums about audio hdmi, but I have not could configure my audio.

I changed the file /etc/modprobe.d/alsa-base.conf and look that:
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
#options snd-hda-intel enable_msi=0
# Audio over HDMI
options snd-hda-intel model=6stack-dig
```

Also I tried with several options:
[FONT="Courier New"]options snd-hda-intel 
options snd-hda-intel enable_msi=0
options snd-hda-intel enable_msi=0 index=-2
options snd-hda-intel enable_msi=0 index=1
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2[/FONT]

My /etc/asound.conf
```
#third tried
pcm.!hdmi-remap {
  type asym
  playback.pcm {
    type plug
    slave.pcm "remap-surround71"
  }
}
 
pcm.!remap-surround71 {
  type route
  slave.pcm "hw:1,7"
  ttable {
    0.0= 1
    1.1= 1
    2.4= 1
    3.5= 1
    4.2= 1
    5.3= 1
    6.6= 1
    7.7= 1
  }
}

#Second tried
#pcm.hdmi17 {
#    type hw
#    card 1
#    device 7
#}
#pcm.!default hdmi17

#first tried
#pcm.!default hdmi:NVidia
#pcm:iec958 hdmi:NVidia
```

my /home/foo/.asoundrc
```
pcm.dmixer {
   type dmix
   ipc_key 1024
   ipc_key_add_uid false
   ipc_perm 0660
   slave {
      pcm "hw:1,7"
      rate 48000
      channels 2
      format S32_LE
      period_time 0
      period_size 1024
      buffer_time 0
      buffer_size 4096
   }
}
 
pcm.!default {
   type plug
   slave.pcm "dmixer"
}
```

I don't know what other thing I can tried, I have read several posts from Ubuntu forums and tried several solutions but I can't get one for my case.

I really appreciate any suggestion.

---

### Post by robalrr on 2010-12-25
I almost forget, I am using the Nvidia driver 260.19.06 from the Additional Drivers auto installer.

---

### Post by robalrr on 2010-12-27
With all the changes I was made to alsa conf files I lost tha audio from the browsers I didn't have audio nor firefox neither chromium, so I have to return my computer to the original configuration, that is delete /etc/asound.conf, ~/.asoundrc, erase the line I added to /etc/modprobe.d/alsa-base.conf and return to the original version the file /usr/share/alsa/cards/HDA-Intel.conf instead the one I download from  "http://pastebin.com/download.php?i=f2e38265".

I followed the solutions from ubuntu forums and from [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller")

I recovered the audio int the browsers and still I continue without hdmi audio.

Does anybody have successfully configured the hdmi sound with a NVidia 310M? I really appreciate any suggestion.

---

