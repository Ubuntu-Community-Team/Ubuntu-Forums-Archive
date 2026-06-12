---
title: "Upgrade from 8.04 to 8.10 ate my sound on P5Q3 mobo?"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by brianpatrick on 2009-01-28
Hi,
My audio was fine in 8.04. I upgraded to 8.10 to see if it fixed the problem of suspend/hibernate not working. It ate my floppy in VirtualBox and ate my sound. 

With /usr/bin/asoundconf-gtk, I selected Intel which is built into my Asus P5Q3 motherboard. I have a dual boot to xp and the sound works there so I know the hardware is working. I have tried system -> control_center -> hardware -> sound and tried every item in Sound_playback (autodetect, alsa, hda intel ad198x, oss, pulse_audio and Plantronics). My plantronics headset gives me the test tone. Everything else is silent. 

I have checked the volume level with the speaker icon on the top right tools bar and it is on max. My speaker control is set to medium. 

I have tried various commands I have seen mentioned in the forums:
root@godzilla2:/home/brianp# lsmod | grep audio
snd_usb_audio         107776  2 
snd_usb_lib            27264  1 snd_usb_audio
snd_hwdep              16904  1 snd_usb_audio
snd_pcm                99208  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd                    79432  22 snd_hda_intel,snd_usb_audio,snd_seq_oss,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
usbcore               175376  8 usb_storage,libusual,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

root@godzilla2:/home/brianp# lsmod | grep sound
soundcore              16800  1 snd

$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [CS50/CS60-USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Asus publishes a linux audio driver in source code but it fails to compile complaining about too many arguments to a function:
[email]brianp@godzilla2:~/download/asus/p5q3.linux.driver[/email]s/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16$ make | grep error
In file included from /home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/include/adriver.h:940,
                 from /home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/acore/hwdep.c:1:
include/linux/pci.h:621: error: expected identifier or ‘(’ before numeric constant
In file included from include/asm/pci.h:4,
                 from include/linux/pci.h:983,
                 from /home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/include/adriver.h:940,
                 from /home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/acore/hwdep.c:1:
include/linux/mm.h:261: error: conflicting types for ‘snd_compat_vmalloc_to_page’
/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/include/adriver.h:744: error: previous declaration of ‘snd_compat_vmalloc_to_page’ was here
In file included from /home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/acore/hwdep.c:1:
/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/include/adriver.h:1182: error: too many arguments to function ‘pci_save_state’
/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/include/adriver.h:1186: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/acore/hwdep.o] Error 1
make[2]: *** [/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16/acore] Error 2
make[1]: *** [_module_/home/brianp/download/asus/p5q3.linux.drivers/LinuxDrivers/LinuxDrivers/Audio/alsa-driver-1.0.16] Error 2
make: *** [compile] Error 2


On xp, I would do a control_panel, system, hardware, device_mangler, find the sound card and update the driver. Is there such a step by step procedure to reinstall a sound driver on Ubuntu?

At least I can still listen to my music with one ear with my headset. ;-)

Thank you,
    BrianP

---

