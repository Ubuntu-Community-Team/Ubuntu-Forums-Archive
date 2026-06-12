---
title: "No sound in Kubuntu 22.04 lts - both cards are shown as &quot;inactive&quot;"
date: 2023-01-26
forum: Hardware
---

### Post by Danchik on 2023-01-26
Good day, 
 recently i've installed a fresh Kubuntu 22.04 lts on my new desktop system. 
After a small tweaking all worked well (nvidia card, etc.) except for the sound
- i've got two monitors with HDMI cabled to and nvidia RTX GPU. But both have to speakers, 
so as before i hoped to use the usual 3.5 mm jack. 
But it gives no sound. More over, i've got a webcamera and the built-in microphone does work and it is seen by the system, but the sound cards of the motherboard of of the nvidia GPU and put to inactive. 
I tried to dig around for similar problems on the web, but i don't see any similarities. 
Maybe someone could help me out with this? 

Here are the basic commands output:

  

      $ aplay -l | grep HDMI
    
    card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
    
    card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
    
    card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
    
    card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
    
    card 2: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
    
    card 2: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
    
    card 2: NVidia [HDA NVidia], device 12: HDMI 6 [HDMI 6]
    
        $ lspci | grep -i Audio
    
    00:1f.3 Audio device: Intel Corporation Tiger Lake-H HD Audio Controller (rev 11)
    01:00.1 Audio device: NVIDIA Corporation Device 228e (rev a1)
    (base) daniilk@daniilk-nova:~$ lsmod | grep -i snd
    snd_sof_pci_intel_tgl    16384  0
    snd_sof_intel_hda_common   102400  1 snd_sof_pci_intel_tgl
    soundwire_intel        40960  1 snd_sof_intel_hda_common
    snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
    snd_sof_pci            20480  2 snd_sof_intel_hda_common,snd_sof_pci_intel_tgl
    snd_sof_xtensa_dsp     16384  1 snd_sof_intel_hda_common
    snd_sof               147456  2 snd_sof_pci,snd_sof_intel_hda_common
    snd_hda_codec_realtek   159744  1
    snd_soc_hdac_hda       24576  1 snd_sof_intel_hda_common
    snd_hda_codec_generic   102400  1 snd_hda_codec_realtek
    snd_hda_ext_core       32768  3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
    snd_soc_acpi_intel_match    61440  2 snd_sof_intel_hda_common,snd_sof_pci_intel_tgl
    snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_sof_intel_hda_common
    ledtrig_audio          16384  2 snd_hda_codec_generic,snd_sof
    snd_soc_core          339968  4 soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda
    snd_hda_codec_hdmi     77824  1
    snd_compress           24576  1 snd_soc_core
    ac97_bus               16384  1 snd_soc_core
    snd_pcm_dmaengine      16384  1 snd_soc_core
    snd_hda_intel          53248  2
    snd_intel_dspcfg       28672  2 snd_hda_intel,snd_sof_intel_hda_common
    snd_intel_sdw_acpi     20480  2 snd_sof_intel_hda_common,snd_intel_dspcfg
    snd_hda_codec         163840  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
    snd_usb_audio         356352  1
    snd_hda_core          110592  9 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
    snd_usbmidi_lib        45056  1 snd_usb_audio
    snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
    snd_pcm               143360  11 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
    snd_seq_midi           20480  0
    snd_seq_midi_event     16384  1 snd_seq_midi
    snd_rawmidi            49152  2 snd_seq_midi,snd_usbmidi_lib
    snd_seq                77824  2 snd_seq_midi,snd_seq_midi_event
    snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
    snd_timer              40960  2 snd_seq,snd_pcm
    snd                   106496  21 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
    mc                     65536  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
    soundcore              16384  1 snd


    systemctl --user status pipewire-session-manager.service

    pipewire-media-session.service - PipeWire Media Session Manager
         Loaded: loaded (/usr/lib/systemd/user/pipewire-media-session.service; enabled; vendor preset: enabled)
         Active: active (running) since Tue 2022-12-20 17:00:44 +07; 1h 18min ago
       Main PID: 1305 (pipewire-media-)
          Tasks: 2 (limit: 38233)
         Memory: 1.4M
            CPU: 62ms
         CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire-media-session.service
                 &#9492;&#9472;1305 /usr/bin/pipewire-media-session
    
    &#1076;&#1077;&#1082; 20 17:00:44 daniilk-nova systemd[1297]: Started PipeWire Media Session Manager.
    &#1076;&#1077;&#1082; 20 17:00:44 daniilk-nova pipewire-media-session[1305]: ms.core: error id:66 seq:266 res:-5 (Input/output error): enum params id>

    lspci -v | grep -A7 -i "audio"

    00:1f.3 Audio device: Intel Corporation Tiger Lake-H HD Audio Controller (rev 11)
            DeviceName: Onboard - Sound
            Subsystem: Gigabyte Technology Co., Ltd Tiger Lake-H HD Audio Controller
            Flags: bus master, fast devsel, latency 32, IRQ 140
            Memory at 53330000 (64-bit, non-prefetchable) [size=16K]
            Memory at 53100000 (64-bit, non-prefetchable) [size=1M]
            Capabilities: [50] Power Management version 3
            Capabilities: [80] Vendor Specific Information: Len=14 <?>
            Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Kernel driver in use: snd_hda_intel
    --
    01:00.1 Audio device: NVIDIA Corporation Device 228e (rev a1)
            Subsystem: Micro-Star International Co., Ltd. [MSI] Device c979
            Flags: bus master, fast devsel, latency 0, IRQ 17
            Memory at 53080000 (32-bit, non-prefetchable) [size=16K]
            Capabilities: [60] Power Management version 3
            Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
            Capabilities: [78] Express Endpoint, MSI 00
            Capabilities: [100] Advanced Error Reporting


    cat /proc/asound/modules
     0 snd_hda_intel
     1 snd_usb_audio
     2 snd_hda_intel


    aplay -l 
    **** List of PLAYBACK Hardware Devices ****
    card 0: PCH [HDA Intel PCH], device 0: ALC897 Analog [ALC897 Analog]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 2: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 2: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 2: NVidia [HDA NVidia], device 12: HDMI 6 [HDMI 6]
      Subdevices: 1/1
      Subdevice #0: subdevice #0

    inxi -A
    Audio:
      Device-1: Intel Tiger Lake-H HD Audio driver: snd_hda_intel
      Device-2: NVIDIA driver: snd_hda_intel
      Device-3: Sunplus Innovation HD 720P webcam type: USB
        driver: snd-usb-audio,uvcvideo
      Sound Server-1: ALSA v: k5.15.0-56-generic running: yes
      Sound Server-2: PulseAudio v: 15.99.1 running: yes
      Sound Server-3: PipeWire v: 0.3.48 running: yes
  



Also 

    pacmd list-cards
    3 card(s) available.
        index: 0
            name: <alsa_card.pci-0000_01_00.1>
            driver: <module-alsa-card.c>
            owner module: 7
            properties:
                    alsa.card = "2"
                    alsa.card_name = "HDA NVidia"
                    alsa.long_card_name = "HDA NVidia at 0x53080000 irq 17"
                    alsa.driver_name = "snd_hda_intel"
                    device.bus_path = "pci-0000:01:00.1"
                    sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2"
                    device.bus = "pci"
                    device.vendor.id = "10de"
                    device.vendor.name = "NVIDIA Corporation"
                    device.product.id = "228e"
                    device.string = "2"
                    device.description = "HDA NVidia"
                    module-udev-detect.discovered = "1"
                    device.icon_name = "audio-card-pci"
            profiles:
                    output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5900, available: no)
                    output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 800, available: no)
                    output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 800, available: no)
                    output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5700, available: no)
                    output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 600, available: no)
                    output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 600, available: no)
                    output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5700, available: no)
                    output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 600, available: no)
                    output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 600, available: no)
                    output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 5700, available: no)
                    output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Output (priority 600, available: no)
                    output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Output (priority 600, available: no)
                    output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Output (priority 5700, available: no)
                    output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Output (priority 600, available: no)
                    output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Output (priority 600, available: no)
                    output:hdmi-stereo-extra5: Digital Stereo (HDMI 6) Output (priority 5700, available: no)
                    output:hdmi-surround-extra5: Digital Surround 5.1 (HDMI 6) Output (priority 600, available: no)
                    output:hdmi-surround71-extra5: Digital Surround 7.1 (HDMI 6) Output (priority 600, available: no)
                    output:hdmi-stereo-extra6: Digital Stereo (HDMI 7) Output (priority 5700, available: no)
                    output:hdmi-surround-extra6: Digital Surround 5.1 (HDMI 7) Output (priority 600, available: no)
                    output:hdmi-surround71-extra6: Digital Surround 7.1 (HDMI 7) Output (priority 600, available: no)
                    off: Off (priority 0, available: unknown)
            active profile: <off>
            ports:
                    hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "video-display"
                    hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "video-display"
                    hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "video-display"
                    hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "video-display"
                    hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "video-display"
                    hdmi-output-5: HDMI / DisplayPort 6 (priority 5400, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "video-display"
                    hdmi-output-6: HDMI / DisplayPort 7 (priority 5300, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "video-display"
        index: 1
            name: <alsa_card.usb-Sunplus_IT_Co_HD_720P_webcam_AN20200706001-02>
            driver: <module-alsa-card.c>
            owner module: 8
            properties:
                    alsa.card = "1"
                    alsa.card_name = "HD 720P webcam"
                    alsa.long_card_name = "Sunplus IT Co HD 720P webcam at usb-0000:00:14.0-4, high speed"
                    alsa.driver_name = "snd_usb_audio"
                    device.bus_path = "pci-0000:00:14.0-usb-0:4:1.2"
                    sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/sound/card1"
                    udev.id = "usb-Sunplus_IT_Co_HD_720P_webcam_AN20200706001-02"
                    device.bus = "usb"
                    device.vendor.id = "1bcf"
                    device.vendor.name = "Sunplus Innovation Technology Inc."
                    device.product.id = "2701"
                    device.product.name = "HD 720P webcam"
                    device.serial = "Sunplus_IT_Co_HD_720P_webcam_AN20200706001"
                    device.form_factor = "webcam"
                    device.string = "1"
                    device.description = "HD 720P webcam"
                    module-udev-detect.discovered = "1"
                    device.icon_name = "camera-web-usb"
            profiles:
                    input:mono-fallback: Mono Input (priority 1, available: unknown)
                    off: Off (priority 0, available: unknown)
            active profile: <input:mono-fallback>
            sources:
                    alsa_input.usb-Sunplus_IT_Co_HD_720P_webcam_AN20200706001-02.mono-fallback/#0: HD 720P webcam Mono
            ports:
                    analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
                            properties:
                                    device.icon_name = "audio-input-microphone"
        index: 2
            name: <alsa_card.pci-0000_00_1f.3>
            driver: <module-alsa-card.c>
            owner module: 9
            properties:
                    alsa.card = "0"
                    alsa.card_name = "HDA Intel PCH"
                    alsa.long_card_name = "HDA Intel PCH at 0x53330000 irq 140"
                    alsa.driver_name = "snd_hda_intel"
                    device.bus_path = "pci-0000:00:1f.3"
                    sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
                    device.bus = "pci"
                    device.vendor.id = "8086"
                    device.vendor.name = "Intel Corporation"
                    device.product.id = "43c8"
                    device.product.name = "Tiger Lake-H HD Audio Controller"
                    device.form_factor = "internal"
                    device.string = "0"
                    device.description = "Built-in Audio"
                    module-udev-detect.discovered = "1"
                    device.icon_name = "audio-card-pci"
            profiles:
                    input:analog-stereo: Analog Stereo Input (priority 65, available: no)
                    output:analog-stereo: Analog Stereo Output (priority 6500, available: no)
                    output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6565, available: no)
                    output:analog-surround-21: Analog Surround 2.1 Output (priority 1300, available: no)
                    output:analog-surround-21+input:analog-stereo: Analog Surround 2.1 Output + Analog Stereo Input (priority 1365, available: no)
                    output:analog-surround-40: Analog Surround 4.0 Output (priority 1200, available: no)
                    output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (priority 1265, available: no)
                    output:analog-surround-41: Analog Surround 4.1 Output (priority 1300, available: no)
                    output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (priority 1365, available: no)
                    output:analog-surround-50: Analog Surround 5.0 Output (priority 1200, available: no)
                    output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (priority 1265, available: no)
                    output:analog-surround-51: Analog Surround 5.1 Output (priority 1300, available: no)
                    output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 1365, available: no)
                    output:analog-surround-71: Analog Surround 7.1 Output (priority 1200, available: no)
                    output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 Output + Analog Stereo Input (priority 1265, available: no)
                    off: Off (priority 0, available: unknown)
            active profile: <off>
            ports:
                    analog-input-front-mic: Front Microphone (priority 8500, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "audio-input-microphone"
                    analog-input-rear-mic: Rear Microphone (priority 8200, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "audio-input-microphone"
                    analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: no)
                            properties:
    
                    analog-output-lineout: Line Out (priority 9000, latency offset 0 usec, available: no)
                            properties:
    
                    analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: no)
                            properties:
                                    device.icon_name = "audio-headphones"

This command shows that all profiles are "OFF". But i've have to clue to get switch then "ON"

---

