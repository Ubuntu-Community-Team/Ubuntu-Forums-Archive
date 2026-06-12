---
title: "Ubuntu 10.4 no sound on alienware laptop after windows chipset driver upgrade"
date: 2010-07-20
forum: Hardware
---

### Post by pacanukeha on 2010-07-20
Hi,
I'm using Ubuntu 10.04 (32) on an Alienware m17x with a dual boot into Windows 7 64. I upgraded the nVidia chipset drivers and on my next and subsequents boots in Ubuntu I get no sound. alsamixer detects the embedded controller, but System | Preferences | Sound gives no devices. Sound works find in windows.

```

cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf0880000 irq 17

lspci
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)

cat /proc/asound/card0/codec#0 | grep Codec
Codec: IDT 92HD73C1X5

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I tried the uninstall/reinstall of alsa-base, linux-sound-base and alsa-utils but that didn't work.

My alsa-info is at
[http://www.alsa-project.org/db/?f=5c0a69f11bba686092ae32b1e3bdd373b6854db5](http://www.alsa-project.org/db/?f=5c0a69f11bba686092ae32b1e3bdd373b6854db5)

Interestingly, about half the time when I reboot I get a loud bzzt sound like it's trying to play all the sound it wanted to play for the session all at once.

Any thoughts?

---

### Post by lidex on 2010-07-20
Try booting into windows and setting sound levels there (again even) then boot back into ubuntu.

---

### Post by pacanukeha on 2010-07-20
I tried adjusting the sound from the system tray icon and then again from the control panel just to make sure - did not trigger any change on reboot into linux unfortunately.

---

### Post by lidex on 2010-07-20
Check your mixer settings. Either of these, 2nd is easier to use.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by lidex on 2010-07-20
No help? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by pacanukeha on 2010-07-21
Hi Lidex,
No help yet. alsamixer comes up fine, there are two choices in the <f6> menu:
Default and HDA NVidia - which are the same thing. All the levels look fine, master at 70, others in the 90-100 range.

uname -a

```
Linux oneofthemcomputers 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux

```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

dpkg -l | grep "alsa"

```
ii  alsa-base                                                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                                         1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                                         4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                                    0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                                 0.10.28-1                                       GStreamer plugin for ALSA

```

head -n 1 /proc/asound/card*/codec#*

```
Codec: IDT 92HD73C1X5
```

Where does the System|Preferences|Sound widget pick up its entries from?

---

### Post by lidex on 2010-07-21
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=alienware 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by pacanukeha on 2010-07-22
I did that before trying the uninstall-reinstall thing.

I'm not sure what alsamixer is supposed to show - my device is there and the levels are appropriate, with or without the alsa-base.conf line. I'll put it back in though, and try again.

That's the weird thing - the embedded sound device shows up in all of the right places as far as I can see, with non-mute, non-zero levels except the System | Preferences | Sound widget. And of course I don't get any sound out, with or without headphones.

---

### Post by lidex on 2010-07-22
See if this helps:
```
sudo apt-get install gnome-media gnome-media-common
```
logout/in

What exactly is this 'uninstall-reinstall thing'?

---

### Post by pacanukeha on 2010-07-22
> **lidex said:**
> See if this helps:
```
sudo apt-get install gnome-media gnome-media-common
```
logout/in

What exactly is this 'uninstall-reinstall thing'?

Unfortunately:
gnome-media is already the newest version.
gnome-media-common is already the newest version.

The uninstall/reinstall thing is what you suggested here:
[http://ubuntuforums.org/showthread.php?p=9606362#post9606362](http://ubuntuforums.org/showthread.php?p=9606362#post9606362)

---

### Post by pacanukeha on 2010-07-22
I have also followed the upgrade scripte here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
with no errors observed.

Can you think of a reason why I would get the loud, short bzt noise when shutting down/rebooting?

speaker-test -Dplughw:1,0 -c2
and
aplay -Dplughw:1,0 -fcd /usr/share/sounds/alsa/Front_Center.wav
work, either through the laptop speakers or the headphones if I plug them in.

but vls, quod-libet, rhythmbox have no output, and there is still no device listed in System->Preferences->Sound.

---

### Post by lidex on 2010-07-22
Try re-installing pulse.
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
```
rm -r ~/.pulse 
```
Reboot.

---

### Post by pacanukeha on 2010-07-22
uninstalled/reinstalled pulse (and ubuntu-desktop).  aplay works, but still no device in S->P->S and quod-libet is silent.

Is it possible something is screwed up in /dev or /proc for some reason?

---

### Post by lidex on 2010-07-22
Time for updated info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by pacanukeha on 2010-07-23
Here is the link to the uploaded output of the info script:

[http://www.alsa-project.org/db/?f=391f868207ad31094b51181b06444f7b57858aa8](http://www.alsa-project.org/db/?f=391f868207ad31094b51181b06444f7b57858aa8)

---

### Post by pori.niki on 2010-07-23
Hi!!

I have a same problem!!

I have sony vaio VPCEA16FG laptop and also i have updated UBUNTU 10!!
but also i have no sound at all!!!
I heard some body that the drivers are new and there in no packages for them.
I am new in Linux.
is there any thing to help me!???
PLZ help Me.
tnx.

---

### Post by lidex on 2010-07-23
I see something screwy here. In your alsa-base.conf, you have this:
```
snd-hda-intel: index=-2 model=alienware

```

Whatever you added, please remove and as a completely separate line add this (do not edit):
```
options snd-hda-intel model=alienware
```

---

### Post by pacanukeha on 2010-07-26
Right - so with the correct options line, I get the ubuntu log in sound - but still no devices in System/Pref/Sound, and still no sound from gnome players like quod-libet, vlc or rhythmbox. aplay still works.

But - youtube videos embedded in Firefox works.

---

### Post by lidex on 2010-07-26
Seems alsa is working. My best guess is that pulseaudio is the culprit. Click the Pulse Audio link in my sig and have a go at 'Part A'.

---

### Post by pacanukeha on 2010-07-27
*baleted*

---

### Post by pacanukeha on 2010-07-27
OK, doing that now:

1) Backing up the pulse and asound files:
cp: cannot stat `/home/username/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory

but the pulse directories are done.

2) rm the files
done.

3) installing the PA files,
done.

4) running pavucontrol
Nope -- no devices in input or output (except the Dummy).

5) running padevchooser shows similar things (no devices)

6) aplay -Dplughw:0,0 -fcd /usr/share/sounds/alsa/Front_Center.wav
works.

---

### Post by lidex on 2010-07-27
Can you post these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by pacanukeha on 2010-07-28
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

```

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  me     19966 F.... plugin-containe
/dev/snd/pcmC0D0p:   me     19966 F...m plugin-containe
/dev/snd/timer:      me     19966 F.... plugin-containe

```

dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

[    3.106512] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[    3.213323] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.213368] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.213627] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
--
[    3.213632]   alloc kstat_irqs on node -1
[    3.213637] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 17 (level, low) -> IRQ 17
[    3.213639] hda_intel: Disable MSI for Nvidia chipset
[    3.213667] HDA Intel 0000:00:08.0: setting latency timer to 64
[    3.273733] Console: switching to colour frame buffer device 80x30
--
[    4.125373] generic-usb 0003:413C:8158.0006: input,hidraw5: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:04.0-4.2/input0
[    4.128242] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input14
[    4.524246] input: HDA NVidia Mic at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input15
[    4.524370] input: HDA NVidia Line Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input16
[    4.524481] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input17
[    4.524584] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input18
[   13.920019] vmnet8: no IPv6 routers present
--
[   60.816060] Memory corruption detected in low memory
[   60.816062] Modules linked in: michael_mic arc4 nls_utf8 nfs lockd nfs_acl auth_rpcgss sunrpc cifs snd_hda_codec_idt binfmt_misc snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss vmnet ppdev parport_pc lib80211_crypt_tkip fbcon tileblit font bitblit softcursor joydev uvcvideo videodev v4l1_compat sdhci_pci sdhci led_class snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device video output snd vmblock vsock vmci vmmon psmouse serio_raw i2c_nforce2 nvidia(P) agpgart vga16fb vgastate wl(P) lib80211 soundcore snd_page_alloc lp parport hid_logitech ff_memless usbhid hid ohci1394 ieee1394 ahci forcedeth
[   60.816136] Pid: 9, comm: events/0 Tainted: P           2.6.32-24-generic-pae #38-Ubuntu



```

---

### Post by lidex on 2010-07-30
> **pacanukeha said:**
> sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

```

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  me     19966 F.... plugin-containe
/dev/snd/pcmC0D0p:   me     19966 F...m plugin-containe
/dev/snd/timer:      me     19966 F.... plugin-containe

```

dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

[    3.106512] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[    3.213323] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.213368] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.213627] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
--
[    3.213632]   alloc kstat_irqs on node -1
[    3.213637] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 17 (level, low) -> IRQ 17
[    3.213639] hda_intel: Disable MSI for Nvidia chipset
[    3.213667] HDA Intel 0000:00:08.0: setting latency timer to 64
[    3.273733] Console: switching to colour frame buffer device 80x30
--
[    4.125373] generic-usb 0003:413C:8158.0006: input,hidraw5: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:04.0-4.2/input0
[    4.128242] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input14
[    4.524246] input: HDA NVidia Mic at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input15
[    4.524370] input: HDA NVidia Line Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input16
[    4.524481] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input17
[    4.524584] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input18
[   13.920019] vmnet8: no IPv6 routers present
--
[   60.816060] Memory corruption detected in low memory
[   60.816062] Modules linked in: michael_mic arc4 nls_utf8 nfs lockd nfs_acl auth_rpcgss sunrpc cifs snd_hda_codec_idt binfmt_misc snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss vmnet ppdev parport_pc lib80211_crypt_tkip fbcon tileblit font bitblit softcursor joydev uvcvideo videodev v4l1_compat sdhci_pci sdhci led_class snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device video output snd vmblock vsock vmci vmmon psmouse serio_raw i2c_nforce2 nvidia(P) agpgart vga16fb vgastate wl(P) lib80211 soundcore snd_page_alloc lp parport hid_logitech ff_memless usbhid hid ohci1394 ieee1394 ahci forcedeth
[   60.816136] Pid: 9, comm: events/0 Tainted: P           2.6.32-24-generic-pae #38-Ubuntu



```

Not sure it's related, but you should check your memory sticks.

---

### Post by pacanukeha on 2010-07-30
Yeah, memtest shows it as fine. Not sure why that is there.

So where does PA look for devices? Can I put it in debug mode for more comprehensive logging to see why it isn't picking up the sound card?

---

### Post by lidex on 2010-07-30
Try this. Go to this page:
[http://www.linlap.com/wiki/audio+tester]("http://www.linlap.com/wiki/audio+tester") and download the two files necessary to run the test. You'll find the instructions there. Report your results.

Also post the output of these commands:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by pacanukeha on 2010-08-01
audiotester.sh
```
sudo bash ./audiotester.sh 
[sudo] password for username: 
Audio Tester - V0.1
Copyright 2009 Bill Giannikos
  
For best results you should ensure you have the latest version
of this utility from:
http://www.linlap.com/wiki/audio+tester

When running this script you may see occasional error messages
from 'amixer', these can be ignored.

Adjusting sound levels to 100%...

amixer: Invalid command!
Testing sound...
Did you hear a sound [N/y]?
y
For sound to work on this system you just need to adjust the Master and PCM volume levels in your mixer program.

```

sudo dmidecode -t bios

```

# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0001, DMI type 0, 24 bytes
BIOS Information
	Vendor: Alienware
	Version: A02
	Release Date: 08/21/2009
	Address: 0xE3820
	Runtime Size: 116704 bytes
	ROM Size: 2048 kB
	Characteristics:
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported

```

sudo dmidecode -t baseboard
```

# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0003, DMI type 2, 9 bytes
Base Board Information
	Manufacturer: Alienware
	Product Name:       
	Version: A02


```

---

### Post by lidex on 2010-08-01
> For sound to work on this system you just need to adjust the Master and PCM volume levels in your mixer program.
Did you do that?

---

### Post by pacanukeha on 2010-08-02
Master was at 95%, PCM was at 100. Neither was muted. This what appeared in gnome-alsamixer. I did not change any setting.s

---

### Post by lidex on 2010-08-02
Was that it for audiotester? No other output? Did you hear the sound?

---

### Post by pacanukeha on 2010-08-03
Correct, no other output. Yes, I heard the little drum sound. The sound that *should* play when GDM displays the session login but doesn't.

---

### Post by lidex on 2010-08-05
Have you installed realplayer? If so remove it and reboot. No help? Post this output please:
```
dpkg -l | grep "OSS"
```

---

### Post by pacanukeha on 2010-08-05
Realplayer is not installed, nor is helix.

```
dpkg -l | grep "OSS"
ii  alsa-oss                                                           1.0.17-3                                        ALSA wrapper for OSS applications
ii  libossp-uuid-perl                                                  1.6.2-1ubuntu1                                  perl OSSP::UUID - OSSP uuid Perl Binding
ii  libossp-uuid16                                                     1.6.2-1ubuntu1                                  OSSP uuid ISO-C and C++ - shared library
ii  linux-sound-base                                                   1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems

```

Should I remove alsa-oss?

---

### Post by lidex on 2010-08-05
No, but try removing these:
```
ii  libossp-uuid-perl                                                  1.6.2-1ubuntu1                                  perl OSSP::UUID - OSSP uuid Perl Binding
ii  libossp-uuid16                                                     1.6.2-1ubuntu1                                  OSSP uuid ISO-C and C++ - shared library

```
Then run this:
```
gstreamer-properties
```
And set your defaults to pulseaudio.
Reboot.

---

### Post by pacanukeha on 2010-08-05
OK, they were removed. When I run gstreamer-properties and choose ALSA I get three output devices:
Default
STAC92xx Analog
STAC92xx Digital

Clicking test on the Analog gives me the tone.

Choosing PulseAudio Sound Server as the plugin gives only Default for output devices and no sound when I click on test.

In neither case does VLC give any audio.

---

### Post by lidex on 2010-08-05
I' m not sure why pulse isn't working for you. Looks like this process is locking the soundcard:
```
      USER        PID ACCESS COMMAND
/dev/snd/controlC0:  me     19966 F.... plugin-containe
/dev/snd/pcmC0D0p:   me     19966 F...m plugin-containe
/dev/snd/timer:      me     19966 F.... plugin-containe
```

If not realplayer, what else did you install around the time of this problem beginning? Apparently plugin container is related to firefox. In another thread the issue was realplayer plugin in firefox and was fixed on its removal.
Try killing firefox, then search system monitor for 'plugin container' and kill any instances of that as well then try this:
```
 pulseaudio & pavucontrol
```

---

### Post by pacanukeha on 2010-08-05
I uninstalled rhythmbox and quod-libet. I deleted all the plugins (( except flash )) from my firefox install. With firefox off, I ran the fuser command on the devices - nothing, so I imagine that means no process using any of the devices.

running pulseaudio gave me the Daemon already running error message.
running pavucontrol again listed no devices except the dummy.

gstreamer-properties gave test tones for both ALSA and OSS (which is pretty strange since I thought we uninstalled all of that, from the dpkg -l | grep OSS bit) but again nothing from pulseaudio.

---

### Post by lidex on 2010-08-05
Can you post the fuser output please?

---

### Post by pacanukeha on 2010-08-05
hmmm.

sudo lsof /dev/snd/*
gives
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/username/.gvfs
      Output information may be incomplete.

Not sure if that has anything to do with it.

---

### Post by pacanukeha on 2010-08-05
The fuser command has no output:

user@system: $ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
user@system: $

---

### Post by pacanukeha on 2010-08-05
Should I try forcing the module in /etc/pulse/default.pa?

---

### Post by lidex on 2010-08-05
No, I think you should re-install alsa.
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

BTW, my ~/.gvfs is empty

---

### Post by pacanukeha on 2010-08-05
If I start my vmplayer I get
sudo fuser /dev/snd/*
/dev/snd/controlC0:   3571
/dev/snd/pcmC0D0p:    3571m
/dev/snd/timer:       3571

---

### Post by pacanukeha on 2010-08-05
OK. Update and upgrade gave me
base-files libpcsclite1

Purging and reinstalling got me
alsa-base alsa-utils linux-sound-base rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store totem-mozilla ubuntu-desktop

And the same problem. No drum-roll on gdm login screen. Ubuntu welcome sound does play. aplay works. Test tone works for ALSA in gstreamer-properties, does not work for pulseaudio. System|Preferences|Sound has no devices.

---

### Post by pacanukeha on 2010-08-05
Did I mention that I get audio from flash? Using the adobe flash plugin. When that happens, fuser shows the plugin-container using the snd devices.

---

### Post by lidex on 2010-08-05
Looks like alsa works, pulse doesn't. Pulse worked for you before didn't it?
What is vmplayer?
Do you have this file:
```
cat /etc/asound.conf
```

---

### Post by lidex on 2010-08-05
Let's see the output of this as well:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by pacanukeha on 2010-08-05
vmplayer is vmware player.

Interesting - I don't have such a file:

```
cat: /etc/asound.conf: No such file or directory
```

pkill pulseaudio; sleep 2; pulseaudio -vv
```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in Valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is f2c25c96acc431de6eba44504baed735.
I: main.c: Session ID is f2c25c96acc431de6eba44504baed735-1281060853.871074-2014520184.
I: main.c: Using runtime directory /home/user/.pulse/f2c25c96acc431de6eba44504baed735-runtime.
I: main.c: Using state directory /home/user/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: database-tdb.c: Opened TDB database '/home/user/.pulse/f2c25c96acc431de6eba44504baed735-device-volumes.tdb'
I: module-device-restore.c: Sucessfully opened database file '/home/user/.pulse/f2c25c96acc431de6eba44504baed735-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: database-tdb.c: Opened TDB database '/home/user/.pulse/f2c25c96acc431de6eba44504baed735-stream-volumes.tdb'
I: module-stream-restore.c: Sucessfully opened database file '/home/user/.pulse/f2c25c96acc431de6eba44504baed735-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: database-tdb.c: Opened TDB database '/home/user/.pulse/f2c25c96acc431de6eba44504baed735-card-database.tdb'
I: module-card-restore.c: Sucessfully opened database file '/home/user/.pulse/f2c25c96acc431de6eba44504baed735-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-udev-detect.so': success
I: module-udev-detect.c: Found 0 cards.
I: module.c: Loaded "module-udev-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus cbcd5360980475fdac6e009b4c5b6fe5 as :1.55
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: bluetooth-util.c: Bluetooth daemon is apparently not available.
I: module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
I: module-default-device-restore.c: Saved default sink 'auto_null' not existant, not restoring default sink setting.
I: module-default-device-restore.c: Saved default source 'auto_null.monitor' not existant, not restoring default source setting.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     device.description = "Dummy Output"
I: sink.c:     device.class = "abstract"
I: sink.c:     device.icon_name = "audio-card"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Dummy Output"
I: source.c:     device.class = "monitor"
I: source.c:     device.icon_name = "audio-input-microphone"
D: module-null-sink.c: Thread starting up
I: module.c: Loaded "module-null-sink" (index: #11; argument: "sink_name=auto_null sink_properties='device.description="Dummy Output"'").
I: module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #13; argument: "").
D: module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session2
I: module.c: Loaded "module-console-kit" (index: #15; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #16; argument: "").
D: dbus-util.c: Successfully connected to D-Bus session bus 368819ece1a3b95742483dde4c5b6ff5 as :1.149
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
I: client.c: Created 1 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
D: sink.c: Suspend cause of sink auto_null is 0x0004, suspending
```

It doesn't return to the command prompt, btw. Just sits there after the last *suspending* line.

I don't see anything in there about the hda-intel card, just the dummy.

---

### Post by lidex on 2010-08-05
Are you running this in a VM?

EDIT: got to the pulse link in my sig and follow part a, then appendix for troubleshooting.
Check this page for reported bugs:
[http://www.pulseaudio.org/report/1](http://www.pulseaudio.org/report/1)

---

### Post by pacanukeha on 2010-08-05
No, that was just a little tid-bit to show that normally nothing was using /dev/snd/* but when I started a program that was supposed to, then fuser would report something. The sound didn't *work* in the vm, mind you. It used to.

---

### Post by lidex on 2010-08-05
Here is my output with no sound apps running:
```
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  lidex      6702 F.... pulseaudio
/dev/snd/controlC1:  lidex      6702 F.... pulseaudio

```

If pulseaudio is configured properly that's what you should see.

---

### Post by lidex on 2010-08-05
Looks like something between udev and pulse. I suspect it's related to this:
```
[   60.816060] Memory corruption detected in low memory
[   60.816062] Modules linked in: michael_mic arc4 nls_utf8 nfs lockd nfs_acl auth_rpcgss sunrpc cifs snd_hda_codec_idt binfmt_misc snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss vmnet ppdev parport_pc lib80211_crypt_tkip fbcon tileblit font bitblit softcursor joydev uvcvideo videodev v4l1_compat sdhci_pci sdhci led_class snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device video output snd vmblock vsock vmci vmmon psmouse serio_raw i2c_nforce2 nvidia(P) agpgart vga16fb vgastate wl(P) lib80211 soundcore snd_page_alloc lp parport hid_logitech ff_memless usbhid hid ohci1394 ieee1394 ahci forcedeth
[   60.816136] Pid: 9, comm: events/0 Tainted: P           2.6.32-24-generic-pae #38-Ubuntu
```

**Have you tried using a different kernel - non-pae preferably?**

---

### Post by pacanukeha on 2010-08-06
OK, so launching VLC and trying to play an mp3 gives me:

C. The application does not play audio and does list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.

There is no muting seen in gnome-alsamixer and test tones play. So the two possibilities are - bug in PA, or possibly an ALSA kernel bug.

Rolling back to 2.6.32-22 from 2.6.32.24 did not help so I'll file a bug at the PA site.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/614453](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/614453)

I forgot to add the
options snd-hda-intel model=alienware
line to the end of /etc/modprobe.d/alsa-base.conf.
Adding it back in and erunning
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'

```
[    3.216108] generic-usb 0003:413C:3012.0003: input,hidraw2: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:06.0-1/input0
[    3.255892] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.255953] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[    3.256246] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
--
[    3.256250]   alloc kstat_irqs on node -1
[    3.256255] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 17 (level, low) -> IRQ 17
[    3.256257] hda_intel: Disable MSI for Nvidia chipset
[    3.256293] HDA Intel 0000:00:08.0: setting latency timer to 64
[    3.296365] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x25c0b1, caps: 0xd04711/0xa00000
--
[    3.937135] usb 3-4.1: configuration #1 chosen from 1 choice
[    3.940115] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input12
[    3.946266] input: HID 413c:8157 as /devices/pci0000:00/0000:00:04.0/usb3/3-4/3-4.1/3-4.1:1.0/input/input13
--
[    4.249541] /dev/vmnet: port on hub 8 successfully opened
[    4.336115] input: HDA NVidia Mic at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input15
[    4.336178] input: HDA NVidia Line Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input16
[    4.336224] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input17
[    4.336266] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input18
[    4.368576] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 19


```
So the memory thing is gone, and the taint line as well.

---

### Post by lidex on 2010-08-06
That dmesg looks good to me - still no sound though?

---

### Post by pacanukeha on 2010-08-06
Unfortunately not, not via Pulse anyway. I don't even get any error messages when I start PA with -vvv. It is just silently ignoring the sound card for some reason. Grrrr.

---

### Post by ravisghosh on 2010-08-11
Even I got sound issue recently after upgrade. Mine is Dell Studio 1555.

---

### Post by lidex on 2010-08-11
> **ravisghosh said:**
> Even I got sound issue recently after upgrade. Mine is Dell Studio 1555.

Please start a new thread.

---

### Post by tpapastylianou on 2010-12-05
Hi pacanukeha

I have an alienware laptop too (albeit an older one - Aurora m9700) and I've always had to tweak the sound settings a bit for sound to prop up, but it never involved installing extra things or messing with configuration files or any of the above mentioned. You might wanna try this (assuming you haven't broken anything from trying the things earlier :p )

I never have sound, because the default output setting is 'Analog Output / Amplifier'.  If I change that to 'Analog Output / No Amplifier' sound works like a charm and that's all that's needed. You can either do that from the default sound properties -> Output tab -> Connector dropmenu. Or you can use gnome-alsamixer (it's in the options I think), or good old alsamixer from a terminal, (Find 'External Amplifier' towards the far right and toggle it to 'off' using the 'm' key or '.' key -- press 'h' for keyboard shortcuts in general)

Hopefully this was the problem with your alienware lappy too and that's all it took to get sound working.

The other tweak I usually have to do on my alienware is to enable my microphone, and this involves the following in alsamixer
[LIST]
[*]Toggle 'Surround Jack Mode' from 'Shared' which is the default to 'Independent'
[*]Change 'V_REFOUT' to either 3.7V or 2.25V (or in any case, play around and see which works). The default value for me disabled any microphone input.
[/LIST]Obviously, set microphone capture as well etc etc, but the above two were the things that were obscure enough and non-intuitive to me, to only have gotten to after lots of experimenting, so I thought it's worth mentioning.

---

