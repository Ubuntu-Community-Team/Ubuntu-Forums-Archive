---
title: "yet another sound complication with ThinkPad R51"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by stardotstar on 2006-01-02
I have read and searched here and seen many similar issues but can't fathom the sound subsystem yet at all.

This all came up from trying to switch from Sound Juicer to GRIP and amaroK.

All the system sounds work fine, interact with the hardware  volume buttons and system tray master volumes etc.  I can play audio CDs using Totem, Sound Juicer and RealPlayer works too.  Video from VLC and various media players work fine.

However I find that I am unable to get amaroK or Audacity to recognise the sound system.  This led me to start playing with the settings and doing some reading.

amaroK does something very wierd when I try to play a playlist - it seems to skip through the tracks one after another as if it has played them but is not actually producing any output.

I went into my multimedia settings to check my sound system values and began to get out of my depth...

Multimedia Systems Selector behaves the following way:

OSS fails to construct test pipeline for OSS as Default Sink when clicking test
ESD produces a continuous tone when clicking test
ALSA produces a higher pitched continuous tone when selected and tested

Default Source settings produce confusing results
Silence when testing all options and hangs when attempting to OK the test window

I then get > The window "Testing Pipeline" is not responding.

Forcing this application to quit will cause you to lose any unsaved changes.

So I don't know if it is all properly configured - obviously it is working somewhat - system sound and sound through some apps but I can;t work out how it all ties together and am researching as you read this (if not sleeping or working for the family ;) )

output:

```
wparker@gecko:/usr/share/pixmaps $ lsmod
Module                  Size  Used by
af_packet              20232  0
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
radeon                 68352  1
drm                    58004  2 radeon
ipv6                  217408  12
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
ibm_acpi               17908  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
floppy                 52692  0
rtc                    11832  0
pcspkr                  3652  0
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ohci1394               30644  0
ieee1394               90936  1 ohci1394
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
hw_random               5268  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
nls_iso8859_1           4224  1
vfat                   12288  1
fat                    46492  1 vfat
nls_cp437               5888  2
ntfs                   92016  1
dm_mod                 50364  0
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
mousedev               10912  1
psmouse                26116  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
e1000                  89780  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  3 ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  1168
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon



wparker@gecko:/usr/share/pixmaps $ cat /proc/interrupts
           CPU0
  0:    1078372          XT-PIC  timer
  1:        987          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          0          XT-PIC  parport0
  8:          0          XT-PIC  rtc
  9:       1149          XT-PIC  acpi
 11:      93184          XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, Intel 82801DB-ICH4, yenta, ohci1394, ipw2200, eth0, radeon@pci:0000:01:00.0
 12:     220307          XT-PIC  i8042
 14:      16772          XT-PIC  ide0
 15:       9273          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0
wparker@gecko:/usr/share/pixmaps $ cat /proc/asound/card
cat: /proc/asound/card: No such file or directory


wparker@gecko:/usr/share/pixmaps $ lsmod | grep snd
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

```

Perhaps some kind Ubuntu expert could help me grok this stuff :)

Will

---

### Post by encompass on 2006-01-03
I am no expert and it has been a while since I have used amarok but...
have you checked which sound device you are using with amarok... there are packages for everything from oss, to arts sound... check which one you are using... if you are in gnome.. try using the esd driver to save memory and not start up a buch of kde stuff... kde uses arts.
did it help?

---

### Post by stardotstar on 2006-01-03
I have actually set amarok to ESDSINK Output Plugin in the prefs and it makes no diff.  The playlist still jumps from one to the next one after the other and the stats for the tracks show that for example the track has been played 7 times but all it has done is go through that hilight and not play anything 7 times as part of the list.

Thanks for the reply :)

---

### Post by stardotstar on 2006-01-03
OK I have done some reading and according to some Ubuntu help I have set ALSA as the default sound card thus:

```
wparker@gecko:/etc/esound $ cat esd.conf
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

also

```

wparker@gecko:/etc $ cat asound.conf
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

```

which funnily enough did not exist.

I rebooted and sound is working as normal but when I go to the multimedia test settings I find that the default source and the default sink work when set to ALSA

however I find that there is no difference in the performance of amaroK when I try to play a cd with it i get:

> Could not start process Unable to create io-slave:
klauncher said: Unknown protocol 'audiocd'.

more and more looks like a major gnome vs kde thingo.

Also I was still able to play the audio cd via Sound Juicer but when I launched CDPlayer I get:

> 
/dev/cdrom does not appear to point to a valid CD device. This may be because:
a) CD support is not present in your machine
b) You do not have the correct permissions to access the CD drive
c) /dev/cdrom is not the CD drive.

and "drive error" in the main display - and yet in prefs there is nowhere to set the device...

Will

---

