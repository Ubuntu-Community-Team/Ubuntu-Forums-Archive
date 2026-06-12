---
title: "No sound Intel Tiger Lake Smart on U23.04"
date: 2023-10-03
forum: Hardware
---

### Post by info-lagocciadisole on 2023-10-03
Hello everyone, please help me!!!
Here's the problem: I purchased a Huawei matebook 14" I5-1135G7 the code is KLVD-WXX9. On ms windows everything is fine, the audio works but by installing Ubuntu 23.04 in dual boot, you can't hear anything from the internal speakers. I looked around various solutions but nothing seems to work, below is some info. Thanks in advance.

```
inxi -Fxxz
System:
  Kernel: 6.2.0-33-generic arch: x86_64 bits: 64 compiler: N/A Desktop: GNOME
    v: 44.3 tk: GTK v: 3.24.37 wm: gnome-shell dm: GDM3 Distro: Ubuntu 23.04
    (Lunar Lobster)
Machine:
  Type: Laptop System: HUAWEI product: KLVD-WXX9 v: M1010
    serial: <superuser required>
  Mobo: HUAWEI model: KLVD-WXX9-PCB-B4-PGF v: M1010
    serial: <superuser required> UEFI: HUAWEI v: 3.19 date: 07/12/2022
Battery:
  ID-1: BAT1 charge: 25.8 Wh (46.2%) condition: 55.8/54.9 Wh (101.6%)
    volts: 7.6 min: 7.6 model: SUNWODA HB4593R1ECW-22S serial: <filter>
    status: discharging
CPU:
  Info: quad core model: 11th Gen Intel Core i5-1135G7 bits: 64 type: MT MCP
    arch: Tiger Lake rev: 1 cache: L1: 320 KiB L2: 5 MiB L3: 8 MiB
  Speed (MHz): avg: 2247 high: 2400 min/max: 400/4200 cores: 1: 2400 2: 1182
    3: 2400 4: 2400 5: 2400 6: 2400 7: 2400 8: 2400 bogomips: 38707
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel TigerLake-LP GT2 [Iris Xe Graphics] vendor: QUANTA
    driver: i915 v: kernel arch: Gen-12.1 ports: active: eDP-1
    empty: DP-1,HDMI-A-1,HDMI-A-2 bus-ID: 00:02.0 chip-ID: 8086:9a49
  Device-2: IMC Networks ov9734_azurewave_camera type: USB driver: uvcvideo
    bus-ID: 1-6:2 chip-ID: 13d3:56f8
  Display: wayland server: X.org v: 1.21.1.7 with: Xwayland v: 22.1.8
    compositor: gnome-shell driver: gpu: i915 display-ID: 0
  Monitor-1: eDP-1 model: BOE Display 0x0893 res: 2160x1440 dpi: 185
    diag: 356mm (14")
  API: OpenGL v: 4.6 Mesa 23.0.4-0ubuntu1~23.04.1 renderer: Mesa Intel Xe
    Graphics (TGL GT2) direct-render: Yes
Audio:
  Device-1: Intel Tiger Lake-LP Smart Sound Audio vendor: QUANTA
    driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3 chip-ID: 8086:a0c8
  Sound API: ALSA v: k6.2.0-33-generic running: yes
  Sound Server-1: PipeWire v: 0.3.65 running: yes
Network:
  Device-1: Intel Wi-Fi 6 AX201 driver: iwlwifi v: kernel bus-ID: 00:14.3
    chip-ID: 8086:a0f0
  IF: wlp0s20f3 state: up mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth type: USB driver: btusb v: 0.8
    bus-ID: 1-10:4 chip-ID: 8087:0026
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 3.0
    lmp-v: 5.2 sub-v: 200f
Drives:
  Local Storage: total: 476.94 GiB used: 13.52 GiB (2.8%)
  ID-1: /dev/nvme0n1 model: 511BS0512HB size: 476.94 GiB speed: 31.6 Gb/s
    lanes: 4 serial: <filter> temp: 25.9 C
Partition:
  ID-1: / size: 330.87 GiB used: 13.42 GiB (4.1%) fs: ext4 dev: /dev/nvme0n1p7
  ID-2: /boot/efi size: 196 MiB used: 102.2 MiB (52.1%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 4 GiB used: 0 KiB (0.0%) priority: -2
    file: /swap.img
Sensors:
  System Temperatures: cpu: 35.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 276 Uptime: 14m Memory: 15.41 GiB used: 2.41 GiB (15.6%)
  Init: systemd v: 252 target: graphical (5) default: graphical Compilers:
  gcc: N/A Packages: 1739 pm: dpkg pkgs: 1730 pm: snap pkgs: 9 Shell: Bash
  v: 5.2.15 running-in: gnome-terminal inxi: 3.3.25

```


```
cat /proc/asound/cards
--- no soundcards ---

```


```
sudo aplay -l
aplay: device_list:274: no sound card detected...

```


```
lsmod | grep snd_hda_intel
snd_hda_intel          61440  0
snd_intel_dspcfg       36864  3 snd_hda_intel,snd_sof,snd_sof_intel_hda_common
snd_hda_codec         204800  5 snd_hda_codec_hdmi,snd_hda_intel,snd_soc_intel_hda_dsp_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_hda_core          139264  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_intel_hda_dsp_common,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_pcm               192512  12 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_sof_utils,snd_soc_es8316,snd_hda_core,snd_pcm_dmaengine
snd                   135168  15 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_soc_sof_es8336,snd_pcm,snd_rawmidi

```

P.s.: HW-PROBE says sound card "DETECTED" and not "WORKS"
[IMG]https://i.imgur.com/4Zln8VV.png[/IMG]


If I add this line at the config file /etc/modprobe.d/alsa-base.conf something changes:

```
 
options snd-hda-intel model=huawei-mbx-stereo

```

I get a first step, which is that in the audio tab of the settings the word "Dummy output" no longer appears but "Tiger Lake-LP smart speakers..." appears, the same if I insert headphones.
Now recognizes the sound card: 

```

 cat /proc/asound/cards
 
 0 [sofessx8336    ]: sof-essx8336 - sof-essx8336
                      HUAWEI-KLVD_WXX9-M1010-KLVD_WXX9_PCB_B4_PGF


```

```

sudo lspci -nnk | grep -A2 Audio
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller [8086:a0c8] (rev 20)
    Subsystem: QUANTA Computer Inc Tiger Lake-LP Smart Sound Technology Audio Controller [152d:1307]
    Kernel driver in use: sof-audio-pci-intel-tgl
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl


```



...but considering that it doesn't produce any sound either with headphones or speakers, I didn't get much!
What do I have to do?

---

### Post by readableauthor on 2023-10-03
Could you share your HW-PROBE link?

---

### Post by info-lagocciadisole on 2023-10-03
I inform you that also video and audio on HDMI port don't work! (on windows it works)

---

### Post by info-lagocciadisole on 2023-10-03
[https://linux-hardware.org/?probe=b4dc684d6a](https://linux-hardware.org/?probe=b4dc684d6a)

---

### Post by info-lagocciadisole on 2023-10-03
[https://linux-hardware.org/?probe=b4dc684d6a](https://linux-hardware.org/?probe=b4dc684d6a)

---

### Post by info-lagocciadisole on 2023-10-04
I tried also Ubuntu Studio but doesn't work. With openSuse all works. There's something that I can do to see what are the differences between Ubuntu and Suse and why the Suse works and Ubuntu not?

---

### Post by amonato on 2024-06-02
Got my sound working on Linux Mint 21.3 on my Matebook 14 2021 (KLVD-WXX9) :o

Had the same problem with Dummy Outpout and no sound even after my sound card got detected.

Here's what I did:

Open alsamixer in terminal and unmute (by pressing "M") Headphone, Headphone Mixer, Right Headphone Mixer Right DAC, Left Headphone Mixer Left DAC.
Then mute Right Headphone Mixer RLIN and Left Headphone Mixer LLIN.
Also try turning every option to 100, while you have a song running.

[URL="https://github.com/Smoren/huawei-ubuntu-sound-fix"][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293834&stc=1[/IMG]
[/URL][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293835&stc=1[/IMG]


You can further increase your volume in Pulseaudio.

If this doesn't work, try the following:

0. Delete your line in /etc/modprobe.d/alsa-base.conf/: options snd-hda-intel model=huawei-mbx-stereo
1. Edit grub file:

```

sudo nano /etc/default/grub 

```


2. Change:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

   to:

```

   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash snd_intel_dspcfg.dsp_driver=3"

```


3. Update GRUB:

```

   sudo update-grub

```


4. Install necessary packages:

```

   sudo apt install pipewire pipewire-pulse wireplumber pavucontrol alsa-base alsa-utils

```


5. Reboot:

```

   sudo reboot

```


After the reboot your system should be able to recognize the sound card.
Remember, if this solultion doesn't work for you, delete the "snd_intel_dspcfg.dsp_driver=3" from /etc/default/grub.

For Matebook 14s/16s, refer to Smoren's solution: [https://github.com/Smoren/huawei-ubuntu-sound-fix](https://github.com/Smoren/huawei-ubuntu-sound-fix)

Hope this helps

---

