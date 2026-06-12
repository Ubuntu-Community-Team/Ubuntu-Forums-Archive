---
title: "Headphone &quot;locks&quot; aound"
date: 2023-08-01
forum: Hardware
---

### Post by john163 on 2023-08-01
I have a Thinkpad X1 running Ubuntu 22.04 and docking station.  If I insert a headphone into the jack, the sound will only come out of the headphones... I can't select the speakers on the monitor.  My last Thinkpad (running RHEL 8 or 9) and docking station did allow me to leave the headphones in and still switch the sound around.

How can I fix this in Ubuntu?

---

### Post by #&amp;thj^% on 2023-08-01
Youv'e not said what you have tried so I'll suggest trying>>  'alsamixer' in the terminal and try out the volume levels for speaker / headphones / master

---

### Post by john163 on 2023-08-01
> **1fallen said:**
> Youv'e not said what you have tried so I'll suggest trying>>  'alsamixer' in the terminal and try out the volume levels for speaker / headphones / master

Settings, Sound is where I go.  I see three output devices... "Speaker - sof-hda-dsp", "Speakers - ThinkPad Hybrid USB-C with USB-A Dock", and "Digital Output (S/PDIF) - ThinkPad Hybrid USB-C with USB-A Dock"

I'm not sure what I'd do in alsamixer.  I can arrow around and see some info, and the up arrow lets me change "Master", but selecting "Headphon" or "Speaker" doesn't do anything.

---

### Post by #&amp;thj^% on 2023-08-01
```
alsamixer --help
Usage: alsamixer [options]
Useful options:
  -h, --help              this help
  -c, --card=NUMBER       sound card number or id
  -D, --device=NAME       mixer device name
  -m, --mouse             enable mouse
  -M, --no-mouse          disable mouse
  -f, --config=FILE       configuration file
  -F, --no-config         do not load configuration file
  -V, --view=MODE         starting view mode: playback/capture/all
Debugging options:
  -g, --no-color          toggle using of colors
  -a, --abstraction=NAME  mixer abstraction level: none/basic

```
Or even
```
man alsamixer
```
You navigate alsamixer with arrows in the right bottom corner of your keyboard.
Some Dock stations don't allow 2 devices, but you said it worked in Redhat right? 
please show me this as well:
```
inxi -Az
Audio:
  Device-1: NVIDIA driver: snd_hda_intel
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  **[COLOR="#FF0000"]Device-4: DisplayLink UOEOS Laptop Dock type: USB[/COLOR]**
    driver: cdc_ncm,snd-usb-audio
  Sound API: ALSA v: k6.2.0-26-generic running: yes
  Sound Server-1: PipeWire v: 0.3.65 running: yes

```
Please Note I'm on Pipwire/Wireplumber Audio:
```
wpctl status
PipeWire 'pipewire-0' [0.3.65, me@me-Lenovo-Legion-5-15ARH05, cookie:<Snip>]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5010]
        33. WirePlumber                         [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5009]
        34. WirePlumber [export]                [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5009]
        40. xdg-desktop-portal                  [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5484]
        42. xfce4-pulseaudio-plugin             [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:6288]
        72. Firefox                             [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:11]
        86. wpctl                               [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:127169]
        92. Strawberry device finder            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:89495]
        93. Strawberry                          [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:89495]

Audio
 &#9500;&#9472; Devices:
 &#9474;      45. HDA NVidia                          [alsa]
 &#9474;      46. UOEOS Laptop Dock                   [alsa]
 &#9474;      47. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;      96. SRS-XB22                            [bluez5]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      51. UOEOS Laptop Dock Analog Surround 5.1 [vol: 0.30]
 &#9474;      53. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.80]
 &#9474;  *   97. SRS-XB22                            [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   52. UOEOS Laptop Dock Analog Stereo     [vol: 1.00]
 &#9474;      54. Family 17h/19h HD Audio Controller Analog Stereo [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        95. Strawberry                                                  
             88. output_FL       > SRS-XB22:playback_FL	[active]
             89. output_FR       > SRS-XB22:playback_FR	[active]

Video
 &#9500;&#9472; Devices:
 &#9474;      43. Integrated Camera                   [v4l2]
 &#9474;      44. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   48. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

[B][COLOR="#FF0000"]Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    bluez_output.F8_DF_15_7F_64_73.1
         1. Audio/Source  alsa_input.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-stereo
[/COLOR][/B]
```

---

### Post by john163 on 2023-08-02
```
joliver@mmjoliver:~$ inxi -Az
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    driver: sof-audio-pci-intel-tgl
  Device-2: DisplayLink ThinkPad Hybrid USB-C with USB-A Dock type: USB
    driver: snd-usb-audio,usbfs
  Device-3: Logitech HD Webcam C615 type: USB
    driver: snd-usb-audio,uvcvideo
  Sound Server-1: ALSA v: k5.19.0-50-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
```

```
joliver@mmjoliver:~$ wpctl statusPipeWire 'pipewire-0' [0.3.48, joliver@mmjoliver, cookie:3508632770]
 &#9492;&#9472; Clients:
        31. pipewire-media-session              [0.3.48, joliver@mmjoliver, pid:5219]
        32. pipewire-media-session              [0.3.48, joliver@mmjoliver, pid:5219]
        37. xdg-desktop-portal                  [0.3.48, joliver@mmjoliver, pid:6094]
        42. wpctl                               [0.3.48, joliver@mmjoliver, pid:148624]


Audio
 &#9500;&#9472; Devices:
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:


Video
 &#9500;&#9472; Devices:
 &#9474;      33. Integrated Camera                   [v4l2]
 &#9474;      34. Integrated Camera                   [v4l2]
 &#9474;      38. HD Webcam C615                      [v4l2]
 &#9474;      39. HD Webcam C615                      [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      35. Integrated Camera                  
 &#9474;      40. HD Webcam C615                     
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:


Settings
 &#9492;&#9472; Default Configured Node Names:

```

---

### Post by #&amp;thj^% on 2023-08-02
My X1 carbon 7th Gen really hates this:
```
Sound Server-2: PulseAudio v: 15.99.1 running: yes
```
I'm pretty sure you was running Piewire on Fedora or Redhat.
And here is why you not able to have both:
```
Audio
 &#9500;&#9472; Devices:
 &#9474;      44. HDA NVidia                          [alsa]
 &#9474;      45. UOEOS Laptop Dock                   [alsa]
 &#9474;      46. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      50. UOEOS Laptop Dock Analog Surround 5.1 [vol: 0.30]
 &#9474;  *   52. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.80]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      51. UOEOS Laptop Dock Analog Stereo     [vol: 1.00]
 &#9474;  *   53. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.95]
 &#9474;  
 &#9500;&#9472; Source endpoints:

```
The above is mine, below is yours:
```
$ wpctl statusPipeWire 'pipewire-0' [0.3.48, joliver@mmjoliver, cookie:3508632770]
 &#9492;&#9472; Clients:
        31. pipewire-media-session              [0.3.48, joliver@mmjoliver, pid:5219]
        32. pipewire-media-session              [0.3.48, joliver@mmjoliver, pid:5219]
        37. xdg-desktop-portal                  [0.3.48, joliver@mmjoliver, pid:6094]
        42. wpctl                               [0.3.48, joliver@mmjoliver, pid:148624]


Audio
 &#9500;&#9472; Devices:
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:


Video
 &#9500;&#9472; Devices:
 &#9474;      33. Integrated Camera                   [v4l2]
 &#9474;      34. Integrated Camera                   [v4l2]
 &#9474;      38. HD Webcam C615                      [v4l2]
 &#9474;      39. HD Webcam C615                      [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      35. Integrated Camera                  
 &#9474;      40. HD Webcam C615                     
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:


Settings
 &#9492;&#9472; Default Configured Node Names:
```

---

### Post by john163 on 2023-08-03
I'm not clear on your response.  Looking at the output doesn't help me... it seems to imply that I have no audio devices, but that is not the case.

If I run this "Pipewire" instead of PulseAudio, will that fix it?  I found [https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)

---

### Post by #&amp;thj^% on 2023-08-03
Yes that link you show is a good method for installing pipewire/wireplumber.
I'll use this for reference for my installs: [https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976215](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976215)
My post your confused on is my X1 has very poor or broken sound with pulseaudio, and it is going to replaced with wireplumber and pipewire. (Sorry for the confusion)

This is the part I don't think you will have "If I run this "Pipewire" instead of PulseAudio, will that fix it? "
While the Carbon X series is a true work horse, I don't think your hardware has that function built in.
Our sound or audio chip is very close to that of a phone's audio chip with nicer speakers and maybe a few extras.
There is a PPA for missing codec's due to license issues. but II still don't think it will help you for this case use. (The PPA is in my link above)

---

### Post by john163 on 2023-08-03
> **1fallen said:**
> 
This is the part I don't think you will have "If I run this "Pipewire" instead of PulseAudio, will that fix it? "
While the Carbon X series is a true work horse, I don't think your hardware has that function built in.

Would a different docking station work?  If so, how would I know which to get?

---

### Post by #&amp;thj^% on 2023-08-03
> **john163 said:**
> Would a different docking station work?  If so, how would I know which to get?

No it's our hardware limitations..Sorry i hate being the bearer of bad news. (Just not enough bells and whistles on that chip)
What model was your other ThinkPad?
EDIT: Please clarify speakers to headphone around, Do you mean both working at the same time?
If not then the pipewire install will or should take of that. (But not Both at once)

---

### Post by #&amp;thj^% on 2023-08-03
Here is mine, but with Arch, but no matter.
```
 inxi -CFz
System:
  Kernel: 6.1.39-3-lts arch: x86_64 bits: 64 Desktop: Xfce v: 4.18.1
    Distro: Arch Linux
Machine:
  Type: Laptop System: LENOVO product: 20R10010US v: ThinkPad X1 Carbon 7th
    serial: <superuser required>
  Mobo: LENOVO model: 20R10010US v: SDK0J40697 WIN
    serial: <superuser required> UEFI: LENOVO v: N2QET51W(1.45 )
    date: 11/30/2022
Battery:
  ID-1: BAT0 charge: 51.7 Wh (99.4%) condition: 52.0/51.0 Wh (101.9%)
CPU:
  Info: quad core model: Intel Core i5-10210U bits: 64 type: MT MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 2001 min/max: 400/4200 cores: 1: 2100 2: 2100 3: 2100
    4: 2100 5: 2100 6: 2100 7: 1308 8: 2100
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] driver: i915 v: kernel
  Device-2: IMC Networks Integrated Camera driver: uvcvideo type: USB
  Display: x11 server: X.org v: 1.21.1.8 driver: X: loaded: intel
    unloaded: modesetting dri: i965 gpu: i915
    resolution: <missing: xdpyinfo/xrandr> resolution: 1920x1080
  API: OpenGL Message: Unable to show GL data. Required tool glxinfo
    missing.
Audio:
  Device-1: Intel Comet Lake PCH-LP cAVS driver: sof-audio-pci-intel-cnl
  API: ALSA v: k6.1.39-3-lts status: kernel-api
  Server-1: PipeWire v: 0.3.76 status: active
Network:
  Device-1: Intel Comet Lake PCH-LP CNVi WiFi driver: iwlwifi
  IF: wlp0s20f3 state: up mac: <filter>
  Device-2: Intel Ethernet I219-V driver: e1000e
  IF: enp0s31f6 state: down mac: <filter>
  IF-ID-1: surfshark_wg state: unknown speed: N/A duplex: N/A mac: N/A
Bluetooth:
  Device-1: Intel Bluetooth 9460/9560 Jefferson Peak (JfP) driver: btusb
    type: USB
  Report: rfkill ID: hci0 state: up address: see --recommends
Drives:
  Local Storage: total: 465.76 GiB used: 46.47 GiB (10.0%)
  ID-1: /dev/nvme0n1 vendor: Western Digital model: WD Blue SN570 500GB
    size: 465.76 GiB
Partition:
  ID-1: / size: 457.15 GiB used: 46.27 GiB (10.1%) fs: btrfs
    dev: /dev/nvme0n1p3
  ID-2: /boot size: 1022 MiB used: 202.7 MiB (19.8%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 7.61 GiB used: 0 KiB (0.0%)
    dev: /dev/nvme0n1p2
Sensors:
  System Temperatures: cpu: 47.0 C pch: 52.0 C mobo: N/A
  Fan Speeds (RPM): fan-1: 0
Info:
  Processes: 286 Uptime: 5m Memory: total: 8 GiB note: est.
  available: 7.43 GiB used: 1.77 GiB (23.8%) Shell: Bash inxi: 3.3.28

```
and i see the same as you as well with *working* sound.
I'll filter it to here:
```
Audio
 &#9500;&#9472; Devices:
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   47. Dummy Output                        [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;      38. Integrated Camera                   [v4l2]
 &#9474;      39. Integrated Camera                   [v4l2]
 &#9474;      40. Integrated Camera: Integrated C     [libcamera]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   41. Integrated Camera (V4L2)           
 &#9474;      43. Built-in Front Camera              
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings

```
Just one output at a time.

---

### Post by #&amp;thj^% on 2023-08-03
@jhon 163 Do you by chance have this installed?
```
apt policy firmware-sof-signed
firmware-sof-signed:
  Installed: 2.2.4-1
  Candidate: 2.2.4-1
  Version table:
 *** 2.2.4-1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```
Your version will be different but worth a shot.
If all goes well I'll add a setting for boot. 
Still waiting for an answer if your speaking of having both Head Set And Monitor Speakers, if so the it's still a no.
But this changes here:
```
Audio
 &#9500;&#9472; Devices:
 &#9474;      44. Built-in Audio                      [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   56. Built-in Audio Analog Stereo        [vol: 0.83]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      57. Built-in Audio Analog Stereo        [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        60. Strawberry                                                  
             62. output_FL       > ALC285 Analog:playback_FL	[active]
             64. output_FR       > ALC285 Analog:playback_FR	[active]


```
if it will work at all it will show as:
```
wpctl status
PipeWire 'pipewire-0' [0.3.65, me@me-Lenovo-Legion-5-15ARH05, cookie:641879173]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5331]
        33. WirePlumber                         [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5326]
        34. WirePlumber [export]                [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5326]
        40. xdg-desktop-portal                  [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5878]
        77. pipewire                            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5331]
        78. pipewire                            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5331]
        87. pipewire                            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5331]
        88. xfce4-pulseaudio-plugin             [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:22145]
        92. pipewire                            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:5331]
       130. PulseAudio Volume Control           [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:34209]
       262. mpv                                 [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:42546]
       265. wpctl                               [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:150801]

Audio
 &#9500;&#9472; Devices:
 &#9474;      49. UOEOS Laptop Dock                   [alsa]
 &#9474;      50. HDA NVidia                          [alsa]
 &#9474;      85. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      32. UOEOS Laptop Dock Analog Surround 5.1 [vol: 0.70]
 &#9474;      54. Family 17h/19h HD Audio Controller Pro [vol: 0.80]
 &#9474;  *   79. combined                            [vol: 1.00]
 &#9474;      91. combined                            [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      63. Family 17h/19h HD Audio Controller Pro [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        58. output.combined_alsa_output.pci-0000_05_00.6.pro-output-0   
             94. output_FL       > ALC257 Analog:playback_AUX0	[active]
             95. output_FR       > ALC257 Analog:playback_AUX1	[active]
        60. output.combined_combined                                    
             81. output_FL       > combined:playback_FL	[active]
             93. output_FR       > combined:playback_FR	[active]
        61. output.combined_alsa_output.pci-0000_05_00.6.pro-output-0   
             46. output_FL       > ALC257 Analog:playback_AUX0	[active]
             64. output_FR       > ALC257 Analog:playback_AUX1	[active]
        70. output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-51
             41. output_FL       > UOEOS Laptop Dock:playback_FL	[active]
             42. output_RL       > UOEOS Laptop Dock:playback_RL	[active]
            101. output_FR       > UOEOS Laptop Dock:playback_FR	[active]
            109. output_RR       > UOEOS Laptop Dock:playback_RR	[active]
            110. output_FC       > UOEOS Laptop Dock:playback_FC	[active]
            111. output_LFE      > UOEOS Laptop Dock:playback_LFE	[active]
        97. output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-51
            112. output_FL       > UOEOS Laptop Dock:playback_FL	[active]
            113. output_FR       > UOEOS Laptop Dock:playback_FR	[active]
            114. output_RL       > UOEOS Laptop Dock:playback_RL	[active]
            115. output_RR       > UOEOS Laptop Dock:playback_RR	[active]
            116. output_FC       > UOEOS Laptop Dock:playback_FC	[active]
            117. output_LFE      > UOEOS Laptop Dock:playback_LFE	[active]
       131. PulseAudio Volume Control                                   
            142. input_FL        < combined:monitor_FL	[active]
            143. monitor_FL     
            144. input_FR        < combined:monitor_FR	[active]
            145. monitor_FR     
       132. PulseAudio Volume Control                                   
            146. input_FL        < ALC257 Analog:monitor_AUX0	[active]
            147. monitor_FL     
            148. input_FR        < ALC257 Analog:monitor_AUX1	[active]
            149. monitor_FR     
       133. PulseAudio Volume Control                                   
            170. input_FL        < combined output:output_FL	[active]
            171. monitor_FL     
            172. input_FR        < combined output:output_FR	[active]
            173. monitor_FR     
       134. PulseAudio Volume Control                                   
            158. input_FL        < UOEOS Laptop Dock:monitor_FL	[active]
            159. monitor_FL     
            160. input_FR        < UOEOS Laptop Dock:monitor_FR	[active]
            161. monitor_FR     
            162. input_RL        < UOEOS Laptop Dock:monitor_RL	[active]
            163. monitor_RL     
            164. input_RR        < UOEOS Laptop Dock:monitor_RR	[active]
            165. monitor_RR     
            166. input_FC        < UOEOS Laptop Dock:monitor_FC	[active]
            167. monitor_FC     
            168. input_LFE       < UOEOS Laptop Dock:monitor_LFE	[active]
            169. monitor_LFE    
       135. PulseAudio Volume Control                                   
            154. input_FL        < combined:monitor_FL	[active]
            155. monitor_FL     
            156. input_FR        < combined:monitor_FR	[active]
            157. monitor_FR     
       136. PulseAudio Volume Control                                   
            150. input_FL        < ALC257 Analog:capture_AUX0	[active]
            151. monitor_FL     
            152. input_FR        < ALC257 Analog:capture_AUX1	[active]
            153. monitor_FR     
       137. PulseAudio Volume Control                                   
            174. input_FL        < combined output:output_FL	[active]
            175. monitor_FL     
            176. input_FR        < combined output:output_FR	[active]
            177. monitor_FR     
       138. PulseAudio Volume Control                                   
            178. input_FL        < combined output:output_FL	[active]
            179. monitor_FL     
            180. input_FR        < combined output:output_FR	[active]
            181. monitor_FR     
       140. PulseAudio Volume Control                                   
            186. input_FL        < combined output:output_FL	[active]
            187. monitor_FL     
            188. input_FR        < combined output:output_FR	[active]
            189. monitor_FR     
            190. input_RL        < combined output:output_RL	[active]
            191. monitor_RL     
            192. input_RR        < combined output:output_RR	[active]
            193. monitor_RR     
            194. input_FC        < combined output:output_FC	[active]
            195. monitor_FC     
            196. input_LFE       < combined output:output_LFE	[active]
            197. monitor_LFE    
       141. PulseAudio Volume Control                                   
            198. input_FL        < combined output:output_FL	[active]
            199. monitor_FL     
            200. input_FR        < combined output:output_FR	[active]
            201. monitor_FR     
            202. input_RL        < combined output:output_RL	[active]
            203. monitor_RL     
            204. input_RR        < combined output:output_RR	[active]
            205. monitor_RR     
            206. input_FC        < combined output:output_FC	[active]
            207. monitor_FC     
            208. input_LFE       < combined output:output_LFE	[active]
            209. monitor_LFE    
       258. mpv                                                         
            184. output_FL       > combined:playback_FL	[active]
            257. output_FR       > combined:playback_FR	[active]
       276. PulseAudio Volume Control                                   
            139. input_FL        < mpv:output_FL	[active]
            267. monitor_FL     
            271. input_FR        < mpv:output_FR	[active]
            275. monitor_FR     

Video
 &#9500;&#9472; Devices:
 &#9474;      80. Integrated Camera                   [v4l2]
 &#9474;      86. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   44. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    combined
         1. Audio/Source  combined

```

---

### Post by john163 on 2023-08-06
> **1fallen said:**
> No it's our hardware limitations..Sorry i hate being the bearer of bad news. (Just not enough bells and whistles on that chip)
What model was your other ThinkPad?

No idea.  I sent it back when I changed jobs.

> EDIT: Please clarify speakers to headphone around, Do you mean both working at the same time?
If not then the pipewire install will or should take of that. (But not Both at once)

No, I don't want them working at the same time.  I want to leave the headphones plugged in but be able to switch the sound to HDMI and use the speakers, and switch back and forth as I want to.

---

### Post by john163 on 2023-08-06
> **1fallen said:**
> @jhon 163 Do you by chance have this installed?
```
apt policy firmware-sof-signed
firmware-sof-signed:
  Installed: 2.2.4-1
  Candidate: 2.2.4-1
  Version table:
 *** 2.2.4-1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```

```
joliver@mmjoliver:~$ apt policy firmware-sof-signed
firmware-sof-signed:
  Installed: 2.0-1ubuntu4.1
  Candidate: 2.0-1ubuntu4.1
  Version table:
 *** 2.0-1ubuntu4.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages
        100 /var/lib/dpkg/status
     2.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/restricted amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/restricted i386 Packages
```

---

### Post by #&amp;thj^% on 2023-08-08
> **john163 said:**
> 
No, I don't want them working at the same time.  I want to leave the headphones plugged in but be able to switch the sound to HDMI and use the speakers, and switch back and forth as I want to.
Thanks for that clarity, and yes you should then be able to do that.
John163 can you run the system-info script with "--details" it is in my signature it will allow me to see what I need to help you.
After the script runs post the Link given to you here in this thread.

---

### Post by john163 on 2023-08-09
> **1fallen said:**
> Thanks for that clarity, and yes you should then be able to do that.
John163 can you run the system-info script with "--details" it is in my signature it will allow me to see what I need to help you.
After the script runs post the Link given to you here in this thread.

[https://paste.ubuntu.com/p/zkRSSpnFhr/](https://paste.ubuntu.com/p/zkRSSpnFhr/)

---

### Post by #&amp;thj^% on 2023-08-09
> **john163 said:**
> [https://paste.ubuntu.com/p/zkRSSpnFhr/](https://paste.ubuntu.com/p/zkRSSpnFhr/)

Thank You Sir, and this may come in to bite us>>>" wayland "
Anyway, I'm still looking at the report be back soon.

---

### Post by #&amp;thj^% on 2023-08-09
Well It don't look as if you ran the script with the "--details" flag, but for now I want you to try this:
Please close any media player you might have now and In your terminal run:
```
pactl load-module module-combine-sink
```
Now Remember Alsamixer? You control volumes there along with making sure any devices are not Muted.
Also be sure PAV is set to use the "combined" switch.
then show me this with a player working for the HDMI:
```
pw-link --links | grep combined
combined:monitor_FL
combined:monitor_FR
combined:playback_FL
combined:playback_FR
  |<- output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-stereo:output_FL
  |<- output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-stereo:output_FR
output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-stereo:output_FL
output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-stereo:output_FR
  |<- output.combined_alsa_output.pci-0000_05_00.6.analog-stereo:output_FL
  |<- output.combined_alsa_output.pci-0000_05_00.6.analog-stereo:output_FR
output.combined_alsa_output.pci-0000_05_00.6.analog-stereo:output_FL
output.combined_alsa_output.pci-0000_05_00.6.analog-stereo:output_FR
  |-> combined:playback_FL
  |-> combined:playback_FR
  |<- combined:monitor_FL
  |<- combined:monitor_FR
  |<- output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-stereo:output_FL
  |<- output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-stereo:output_FR
  |<- output.combined_alsa_output.pci-0000_05_00.6.analog-stereo:output_FL
  |<- output.combined_alsa_output.pci-0000_05_00.6.analog-stereo:output_FR

```

---

### Post by john163 on 2023-08-11
> **1fallen said:**
> Well It don't look as if you ran the script with the "--details" flag, but for now I want you to try this:
Please close any media player you might have now and In your terminal run:
```
pactl load-module module-combine-sink
```
Now Remember Alsamixer? You control volumes there along with making sure any devices are not Muted.
Also be sure PAV is set to use the "combined" switch.
then show me this with a player working for the HDMI:
```
pw-link --links | grep combined
```

While I have sound coming from HDMI:

```

joliver@mmjoliver:~$ pactl load-module module-combine-sink
536870913
joliver@mmjoliver:~$ pw-link --links | grep combined
joliver@mmjoliver:~$ pw-link --links
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:playback_FL
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:output_FL
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:playback_FR
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:output_FR
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:playback_FL
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:output_FL
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:playback_FR
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:output_FR
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:playback_FL
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:output_FL
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:playback_FR
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:output_FR
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:playback_FL
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:output_FL
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:playback_FR
  |<- combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:output_FR
alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:playback_FL
  |<- combine_output.sink-536870913.alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:output_FL
  |<- Google Chrome:output_FL
alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:playback_FR
  |<- combine_output.sink-536870913.alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:output_FR
  |<- Google Chrome:output_FR
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:output_FL
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:playback_FL
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:output_FR
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink:playback_FR
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:output_FL
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:playback_FL
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:output_FR
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink:playback_FR
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:output_FL
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:playback_FL
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:output_FR
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink:playback_FR
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:output_FL
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:playback_FL
combine_output.sink-536870913.alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:output_FR
  |-> alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink:playback_FR
combine_output.sink-536870913.alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:output_FL
  |-> alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:playback_FL
combine_output.sink-536870913.alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:output_FR
  |-> alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:playback_FR
Google Chrome:output_FL
  |-> alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:playback_FL
Google Chrome:output_FR
  |-> alsa_output.usb-DisplayLink_ThinkPad_Hybrid_USB-C_with_USB-A_Dock_10085535-02.analog-stereo:playback_FR
joliver@mmjoliver:~$

```

---

### Post by john163 on 2023-08-11
> **1fallen said:**
> Well It don't look as if you ran the script with the "--details" flag

Sorry!

[https://paste.ubuntu.com/p/vc3MRSD6N4/](https://paste.ubuntu.com/p/vc3MRSD6N4/)

---

### Post by #&amp;thj^% on 2023-08-11
Looks to be working, What settings are now in the Audio mixer? Do you see a "combined" option now?

---

### Post by john163 on 2023-08-12
> **1fallen said:**
> Looks to be working, What settings are now in the Audio mixer? Do you see a "combined" option now?

I do, but with the headphones inserted, sound comes out the laptop speakers, not the HDMI.

---

### Post by john163 on 2023-08-12
[https://ibb.co/ykccsJM](https://ibb.co/ykccsJM)

---

### Post by john163 on 2023-08-12
[https://ibb.co/nw00Zww](https://ibb.co/nw00Zww)

---

### Post by #&amp;thj^% on 2023-08-12
> **john163 said:**
> I do, but with the headphones inserted, sound comes out the laptop speakers, not the HDMI.

Is the HDMI on the Dock, or are you using the HDMI port from the laptop.
And alsamixer is a good place to see if the HDMI device is muted.
BTW They have improved that Audio Chip for your laptop. (That's a Good thing )

---

### Post by john163 on 2023-08-13
> **1fallen said:**
> Is the HDMI on the Dock, or are you using the HDMI port from the laptop.
And alsamixer is a good place to see if the HDMI device is muted.
BTW They have improved that Audio Chip for your laptop. (That's a Good thing )

On the dock.  And there's no sign that HDMI is muted.  I cannot find an output I can select that will let me hear from the speakers on my HDMI connected monitor when the headphone jack is inserted.

[https://ibb.co/Qn9nfCX](https://ibb.co/Qn9nfCX)

[https://ibb.co/Q9M9g8q](https://ibb.co/Q9M9g8q)

---

### Post by #&amp;thj^% on 2023-08-13
> **john163 said:**
> On the dock.  And there's no sign that HDMI is muted.  I cannot find an output I can select that will let me hear from the speakers on my HDMI connected monitor when the headphone jack is inserted.

[https://ibb.co/Qn9nfCX](https://ibb.co/Qn9nfCX)

[https://ibb.co/Q9M9g8q](https://ibb.co/Q9M9g8q)

Ok all that looks good, now from the Volume control>>>Select HDMI from the Dock or even just point Audio to the Dock.
Keep in mind I have no wayland for a session and I warned this might keep us form setting combined outputs but IJDKFS 
BTW you did know that "pactl load-module module-combine-sink" only lasts for the Session.
You can add that command to your Auto-Start-up to have on each boot up, or persistent.

---

### Post by john163 on 2023-08-14
> **1fallen said:**
> Ok all that looks good, now from the Volume control>>>Select HDMI from the Dock or even just point Audio to the Dock.

I don't know what/where this is.

> BTW you did know that "pactl load-module module-combine-sink" only lasts for the Session.
You can add that command to your Auto-Start-up to have on each boot up, or persistent.

"Auto-Start-up"???  Somewhere in default.pa?

---

### Post by #&amp;thj^% on 2023-08-14
> **john163 said:**
> I don't know what/where this is.
The Volume Control, See Screenshot


> **john163 said:**
> 
"Auto-Start-up"???  Somewhere in default.pa?

No not in default.pa but here for all sessions and applications that Auto Start.
```
gnome-session-properties
```

---

### Post by john163 on 2023-08-14
I don't have anything that looks anything like your screen shot.

[https://ibb.co/VmmPD98](https://ibb.co/VmmPD98)

[https://ibb.co/cbZN1xS](https://ibb.co/cbZN1xS)

---

### Post by john163 on 2023-08-14
> **1fallen said:**
> 
No not in default.pa but here for all sessions and applications that Auto Start.
```
gnome-session-properties
```

/usr/bin/gnome-session-properties ?  Add a shell script to run that pactl command?

---

### Post by #&amp;thj^% on 2023-08-14
Gnome, I'll save my thought on that, but john163 just use this to pull-up the application needed here:
```
pavucontrol

```
The Playback Tab is the best source to change your audio devices.
See Screenshot

---

### Post by #&amp;thj^% on 2023-08-14
> **john163 said:**
> /usr/bin/gnome-session-properties ?  Add a shell script to run that pactl command?

No just throw this command to a NEW Auto start.
```
pactl load-module module-combine-sink
```
Name it anything that you will remember it by.
 But the Command portion has to read just like i posted

---

### Post by #&amp;thj^% on 2023-08-14
john163 I have found out that you may need to install this:
```
sudo apt install gnome-startup-applications
```
And after its installed, search for "startup" to launch that option,  there you can then add the Start-up.
I just don't use Gnome so all that stuff is dependent on Desktop Environments.
Good Luck I'm off to a Meeting.

---

### Post by john163 on 2023-08-14
> **1fallen said:**
> Gnome, I'll save my thought on that, but john163 just use this to pull-up the application needed here:
```
pavucontrol

```
The Playback Tab is the best source to change your audio devices.
See Screenshot

I seem to be completely missing something.  There is no option I can find anywhere that switches the sound from the headphones to the HDMI output.

As for gnome, that's what Ubuntu ships with.  It isn't like I decided to install something different.

---

### Post by tea for one on 2023-08-14
> **john163 said:**
> I seem to be completely missing something.  There is no option I can find anywhere that switches the sound from the headphones to the HDMI output.
Using Ubuntu 22.04 with Gnome 42.9
Applications > Settings > Sound > Output Device
I have HDMI HD Audio & Headphones & JVC Headset Bluetooth.
Play a song from Rhythmbox and toggle dynamically between all three output devices.

Edit: I've just read post no. 3 where you mention your laptop and docking station. My output results are probably not useful. Apologies

---

### Post by #&amp;thj^% on 2023-08-15
> **john163 said:**
> I seem to be completely missing something.  There is no option I can find anywhere that switches the sound from the headphones to the HDMI output.



@john163 can you run this command for me, and take a screenshot:
```
pavucontrol
```
Attach it to your next reply.
> **john163 said:**
> As for gnome, that's what Ubuntu ships with. It isn't like I decided to install something different. 
We each have different Environments that we either just become used to or prefer, Gnome is just not my cup of tea, and I have not used it since Gnome2.
That's all there is to that story. If your happy with Gnome then just use it.

---

### Post by #&amp;thj^% on 2023-08-16
Please don't take this as a bad thing, but this post is over 2 weeks old now, and i have to think all this related to the Session in use.
I have 3 Linux OS's (Ubuntu Debian and Arch) installed here, and all work with combined sinks, and from your system-info yours should work as well, I'm just not sure Gnome on Wayland is helping here. (Of course I could be wrong)
Here is one part of the recipe that will be needed across all restart's, and it is important to place in "/home/your_username/.config/autostart/" 
and inside that file copy this:
```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Combined Audio
Comment=
Exec=pactl load-module module-combine-sink
OnlyShowIn=GNOME;
RunHook=0
StartupNotify=false
Terminal=false
Hidden=false
```
I've named mine **"Combined Audio"** for an easy look.
```
ls /home/me/.config/autostart | grep 'Combined Audio'
Combined Audio.desktop

```
```
wpctl status | grep active
             73. output_FL       > UOEOS Laptop Dock:playback_FL	[active]
             74. output_FR       > UOEOS Laptop Dock:playback_FR	[active]
             75. output_FL       > ALC257 Analog:playback_FL	[active]
             76. output_FR       > ALC257 Analog:playback_FR	[active]
             90. output_FL       > SRS-XB22:playback_FL	[active]
             91. output_FR       > SRS-XB22:playback_FR	[active]
             98. output_FR       > combined:playback_FR	[active]
             99. output_FL       > combined:playback_FL	[active]

```
This Thread should have been fixed if fixable in about 10 minutes, and not 2 weeks later.
maybe someone else is better suited to help you going forward.

---

