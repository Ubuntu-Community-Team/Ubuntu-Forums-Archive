---
title: "Since Sometime Post 2018"
date: 2023-03-29
forum: Hardware
---

### Post by Mark76 on 2023-03-29
I have not been able to get Pulseaudio to detect and connect to the internal soundcard (the one that drives the headphone and microphone jacks and the internal speakers, not to be confused with the (digital) HDMI output) on my EliteBook 8460P . The only way I can listen to anything is either via an audio interface (the kind used for recording) or bluetooth.  I'd like my analogue audio back.  Please.

I suspect something got screwed up in the Kernel (that's usually where the drivers live, right?).  But I don't want to wait for some developer to notice that the sound doesn't work properly on a 15(?) year old laptop; since I'd probably be waiting forever

---

### Post by TheFu on 2023-03-29
Assuming you've already done this: [https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en](https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en)

Probably best to run the *sound troubleshooter script* in the Multi-media sub-forum, then post the URL or output.  I don't remember the exact name of the script, sorry.  

The Ubuntu Audio Dev team has this: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) with more troubleshooting steps and how to file a bug that they will see and just the triage effort might get a solution.  Be certain to follow each link on the links I've provided.

---

### Post by SeijiSensei on 2023-03-29
I'd start with step four in the piece TheFu cited. Open a terminal and type "lspci". Do you see anything marked as an Audio Device? 

For instance, on this machine which has both standard audio via the 3.5mm jack, and a second output via my NVIDIA graphics card, I get
```

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GP108 High Definition Audio Controller (rev a1)

```
Pretty much every Intel device already has drivers in the kernel since Intel releases all its drivers as open source. For NVIDIA, I needed the proprietary driver for both video and audio. That is my default device, and it sends its audio output via the HDMI cable that connects my card and monitor. (Actually the output goes first to a 3-way HDMI switch. The switch extracts the audio signal and sends it to my desktop speakers via a 3.5mm jack.)

If you see devices there, the next step I would take is to run "ubuntu-drivers" from the terminal prompt and see what happens.

---

### Post by Mark76 on 2023-03-29
I typed ¨ubuntu-drivers¨ into a terminal and got this

> Usage: ubuntu-drivers [OPTIONS] COMMAND [ARGS]...

Options:
  --gpgpu              gpgpu drivers
  --free-only          Only consider free packages
  --package-list PATH  Create file with list of installed packages (in install
                       mode)
  --no-oem             Do not include OEM enablement packages (these enable an
                       external archive)  [default: False]
  -h, --help           Show this message and exit.

Commands:
  autoinstall  Deprecated, please use "install" instead
  debug        Print all available information and debug data about drivers.
  devices      Show all devices which need drivers, and which packages...
  install      Install a driver [driver[:version][,driver[:version]]]
  list         Show all driver packages which apply to the current system.
  list-oem     Show all OEM enablement packages which apply to this system


---

### Post by Mark76 on 2023-03-29
> **TheFu said:**
> Assuming you've already done this: [https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en](https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en)

Probably best to run the *sound troubleshooter script* in the Multi-media sub-forum, then post the URL or output.  I don't remember the exact name of the script, sorry.  

The Ubuntu Audio Dev team has this: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) with more troubleshooting steps and how to file a bug that they will see and just the triage effort might get a solution.  Be certain to follow each link on the links I've provided.

I also cannot find the script

---

### Post by #&amp;thj^% on 2023-03-29
> **Mark76 said:**
> I also cannot find the script

it's here, in the multimedia forum at the "top"
  [B]  Sticky Thread Sticky: [SOLVED] Sound troubleshooting
    Started by mörgæs, November 23rd, 2011 [/B]
URL: [https://ubuntuforums.org/showthread.php?t=1885240](https://ubuntuforums.org/showthread.php?t=1885240)
to use the ubuntu-driver utility:
```
ubuntu-driver autoinstall
```

---

### Post by Mark76 on 2023-03-29
sudo ubuntu-drivers autoinstall   
All the available drivers are already installed.

My soundcard is an Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)

---

### Post by Mark76 on 2023-03-29
Still can't find a script tried this instead

> sudo inxi -SMA
System:
  Host: mark-laptop Kernel: 5.15.0-69-generic x86_64 bits: 64
    Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Hewlett-Packard product: N/A v: A0001C02 serial: N/A
  Mobo: Hewlett-Packard model: 161C v: KBC Version 97.4E serial: N/A
    UEFI: Hewlett-Packard v: 68SCF Ver. F.60 date: 03/12/2015
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-69-generic running: yes
  Sound Server-2: JACK v: 1.9.20 running: yes
  Sound Server-3: PulseAudio v: 15.99.1 running: yes
  Sound Server-4: PipeWire v: 0.3.48 running: yes
mark@mark-laptop:~$ 


---

### Post by #&amp;thj^% on 2023-03-29
I dumped pulseaudio:
```
systemctl status pulseaudio
Unit pulseaudio.service could not be found.

```
Mine:
```
inxi -SMA
[sudo] password for me: 
System:
  Host: me-Lenovo-Legion-5-15ARH05 Kernel: 6.1.0-1007-oem x86_64 bits: 64 
  Desktop: Xfce 4.18.1 Distro: Linux Lite 6.2 LTS 
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05 
  serial: PF29L70E 
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN serial: PF29L70E 
  UEFI: LENOVO v: EUCN37WW date: 04/14/2022 
Audio:
  Device-1: NVIDIA driver: snd_hda_intel 
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A 
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel 
  Device-4: DisplayLink UOEOS Laptop Dock type: USB 
  driver: cdc_ncm,snd-usb-audio 
  Sound Server: ALSA v: k6.1.0-1007-oem 


```
If interested in trying see this: [https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976215](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976215)
```
systemctl --user status wireplumber.service
&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; vendor>
     Active: active (running) since Wed 2023-03-29 12:47:22 MDT; 4h 46min ago
   Main PID: 8457 (wireplumber)
      Tasks: 4 (limit: 9103)
     Memory: 6.1M
        CPU: 4.499s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wirepl>
             &#9492;&#9472;8457 /usr/bin/wireplumber


```

---

### Post by #&amp;thj^% on 2023-03-29
> **Mark76 said:**
> Still can't find a script tried this instead

I just noticed this:
make sure "alsa-utils" are installed first then run:
```
/usr/sbin/alsa-info --with-devices

```
upload to a pastebin include a link to view here.

---

### Post by Mark76 on 2023-03-30
> **1fallen said:**
> I just noticed this:
make sure "alsa-utils" are installed first then run:
```
/usr/sbin/alsa-info --with-devices

```
upload to a pastebin include a link to view here.

Ran that.  Got

> /usr/sbin/alsa-info --with-devices
ALSA Information Script v 0.5.1
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  aplay
  amixer
  alsactl
  rpm, dpkg
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '/usr/sbin/alsa-info --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ... Done!

Your ALSA information is located at 
Please inform the person helping you.

Not really much help to anyone.

---

### Post by #&amp;thj^% on 2023-03-30
Mark76, sound has been a problem for Ubuntu 22.04 on some hardware, including yours.
I'm at a loss to advise you further, if you followed that link exactly and fully and ran *all* commands listed there, you should in theory have working sound.(and a reboot)
And without seeing the alsa report>> well I got nothing more to add.
Good Luck though. ;)
No one seems interested in filling bug reports on this.

---

### Post by Mark76 on 2023-03-30
Okay, I don't understand how to run that command.  Is it ¨/usr/sbin/alsa-info --with-devices¨ or ¨/usr/sbin/alsa-info --?¨

---

### Post by #&amp;thj^% on 2023-03-30
For me it's:
```
~$ /usr/sbin/alsa-info --with-devices
ALSA Information Script v 0.5.1
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  aplay
  amixer
  alsactl
  rpm, dpkg
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '/usr/sbin/alsa-info --help' for command line options.

pgrep: pattern that searches for process name longer than 15 characters will result in zero matches
Try `pgrep -f' option to match against the complete command line.
cat: '/sys/module/snd_soc_skl_hda_dsp/parameters/*': No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : 

```
This is where you will get a link to paste back here:
```
Automatically upload ALSA information to www.alsa-project.org? [y/N] : 
```
It defaults to No so choose Yes, Also you will have a copy for yourself in "/tmp/alsa-info.txt.rB19q57Lqb"
Mark76, this is a part I would love to see:
```

!!Sound Servers on this system
!!----------------------------

PipeWire:
      Installed - Yes (/usr/bin/pipewire)
      Running - Yes

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd1000000 irq 87
 1 [Dock           ]: USB-Audio - UOEOS Laptop Dock
                      DisplayLink UOEOS Laptop Dock at usb-0000:05:00.4-1.2.1, super speed
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xd1540000 irq 88
```
EDIT: I'm going into work for a few hours, I'll check back to see how your making out.

---

### Post by Mark76 on 2023-07-01
Ran it again without the --with devices part

[http://alsa-project.org/db/?f=51d94d36f51e77c974a2a00c3f025f29f3881f9b](http://alsa-project.org/db/?f=51d94d36f51e77c974a2a00c3f025f29f3881f9b)

---

### Post by Mark76 on 2023-07-01
I know there's a lot there but that was the only way I could get it to work.  Not knowing exactly what devices to specify

---

### Post by Mark76 on 2023-07-01
PipeWire:
      Installed - Yes (/usr/bin/pipewire)
      Running - Yes

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xd4820000 irq 39


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
	Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family High Definition Audio Controller [103c:161c]

I think HDA Intel PCH is the one that drives the HDMI audio output,

---

### Post by #&amp;thj^% on 2023-07-03
Still somethings are amiss here:
Mine shows "!!Soundcards recognised by ALSA"
```
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd1000000 irq 94
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xd1540000 irq 95
 2 [Dock           ]: USB-Audio - UOEOS Laptop Dock
                      DisplayLink UOEOS Laptop Dock at usb-0000:05:00.3-1.1, super speed


!!PCI Soundcards installed in the system
!!--------------------------------------

01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10fa] (rev a1)
	Subsystem: NVIDIA Corporation Device [10de:10fa]
05:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller [1022:15e3]
	Subsystem: Lenovo Family 17h/19h HD Audio Controller [17aa:381b]


```
I'm not sure anything has been fixed on your current running kernel:
Yours:
```
!!Kernel Information
!!------------------

Kernel release:    5.15.0-76-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k5.15.0-76-generic
Library version:    1.2.6.1
Utilities version:  1.2.6


!!Loaded ALSA modules
!!-------------------

snd_hda_intel (card 0)
```
So close but no sound still?
For myself I couldn't dump kernel 5.15 fast enough...lol
Your quote:
> I suspect something got screwed up in the Kernel (that's usually where the drivers live, right?). But I don't want to wait for some developer to notice that the sound doesn't work properly on a 15(?) year old laptop; since I'd probably be waiting forever 
They need to know about this or it will NEVER be fixed.
My last suggestion is to try a different kernel.
Good Luck

---

### Post by Mark76 on 2023-07-03
Well, I submitted a bug report.  Let's wait and see what happens

---

### Post by Mark76 on 2023-07-10
[http://alsa-project.org/db/?f=92e4001b5a5cd6473481cf3b81e6ddd7f76d9296](http://alsa-project.org/db/?f=92e4001b5a5cd6473481cf3b81e6ddd7f76d9296)

---

