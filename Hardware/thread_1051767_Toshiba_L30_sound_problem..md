---
title: "Toshiba L30 sound problem."
date: 2009-01-27
forum: Hardware
---

### Post by andy12345 on 2009-01-27
First of all Hello,
I have just migrated from windows to xubuntu (The reason being that its so good damn faster), But just to hear my songs I have windows, I want to completely change to xubuntu and hope you will help me :D
My Problem,
There is no sound output whatsoever, the last time I used 8.04 LTS there was no sound but I could pump the volume, this time I am using 8.10 but As soon as i increase the volume (From Master) it defaults to 0% again =(
What I have done so far,
First I googled my problem found a lot of solutions, mostly tried all of them, Problem wasn't solved so I went over IRC, a kind hearted soul called **lc2** helped me there, I got kmix (it shows 100% volume but the master is still at 0%), I also tried everything mentioned here [http://www.acomelectronics.com/GeorgeVita/L30_sound.html](http://www.acomelectronics.com/GeorgeVita/L30_sound.html)
But in vain my laptop seems to like me fuming over the idea of logging in windows just to play my songs,
Hope I have covered everything without breaking any rules (And If I have done so I am really very sorry it was unintended).
Regards,
Andy


EDIT- I did this [http://ubuntuforums.org/showthread.php?t=817179&highlight=toshiba+L30+sound](http://ubuntuforums.org/showthread.php?t=817179&highlight=toshiba+L30+sound) and now I can adjust the volume bar, but still no sound.

---

### Post by andy12345 on 2009-01-27
Some stuff you  might need

lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My Alsa-Base Config.


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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
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
options snd-hda-intel probe_mask=1 model=3stack 
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

---

### Post by andy12345 on 2009-01-27
BUMP! I really need to hear music on xubuntu please help! =|

---

### Post by GeorgeVita on 2009-03-22
Hi,
a little bit late but a week ago I installed 8.10 to my L30-113 and following your link above I ... found my solution written some months ago!

I tried the **lspci** and **aplay -l** commands and found that in my case the L30-113 uses ALC861VD chip instead of ALC861 in yours. So from the ALSA-Configuration.txt you should check the following parameters:

[B]3stack
3stack-dig
6stack-dig
3stack-660
uniwill-m31
toshiba
asus
asus-laptop
auto[/B]

for the **options snd-hda-intel model=xxxxx** line of /etc/modprobe.d/alsa-base file (xxxxx replaced by one of the above parameters). See [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Although painful you have to test all possibilities starting with the **toshiba** one whih was not included in the ALC861VD list. Test with **shut down** and full restart to be sure that the h/w is fully initialized.

Also note that I am using Ubuntu 8.10 and not Xubuntu.

Regards,
George

---

