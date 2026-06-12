---
title: "Thinklight control on T530"
date: 2013-11-02
forum: Hardware
---

### Post by novalu2 on 2013-11-02
Hello,

I can't get to work manual control of Thinklight on my Lenovo Thinkpad T530. I have Ubuntu 13.10.

I've tried to enable it according to instructions here - [http://www.thinkwiki.org/wiki/ThinkLight]("http://www.thinkwiki.org/wiki/ThinkLight:")

```
# echo 255 > /sys/class/leds/tpacpi\:\:thinklight/brightness
# cat /sys/class/leds/tpacpi\:\:thinklight/brightness
0
```

but it doesn't work. When I press Fn+Space to turn ThinkLight on, then it says

```
# cat /sys/class/leds/tpacpi\:\:thinklight/brightness 
255
```

I've tried legacy /proc interface too, but with no success

```
# cat /proc/acpi/ibm/light 
status: off
commands: on, off

# echo "on" > /proc/acpi/ibm/light
# cat /proc/acpi/ibm/light 
status: off
commands: on, off
```

With ThinkLight enabled by hotkeys it says "status: on"

I've tried control leds with /proc/acpi/ibm/led too, but with

```
# echo "0 blink" > /proc/acpi/ibm/led
```

i can only control power button. Other (1-15) numbers says Operation not permitted or nothing (for led #7 and #12)

Do somebody know how to get it to work?

Thank you in advance.

---

### Post by tgalati4 on 2013-11-02
What modules are loaded?

```
lsmod
```

You should see something like:


thinkpad_acpi          66560  0 
led_class              12036  1 thinkpad_acpi
nvram                  16396  1 thinkpad_acpi

This is on a T43p, but your machine would have something similar.  On my machine Fn+Space is Zoom, Fn+PageUp is the thinklight.  

Run *xev* in a terminal and go through all of your FN keys.  Ones that show up in *xev* can be programmed with shortcuts.  Ones that don't are either handled by the ACPI subsystem or are not supported (which is rare for Thinkpads).

It's also possible that your thinklight is defective.  Has it ever worked?  Does it work under Windows?

---

### Post by novalu2 on 2013-11-02
Thank you, lsmod is here: 

```
Module                  Size  Used by
usb_storage            48294  0 
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               295678  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  16 
bnep                   18893  2 
binfmt_misc            13140  1 
joydev                 17097  0 
x86_pkg_temp_thermal    13810  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm                   364766  0 
crc32_pclmul           12967  0 
aesni_intel            18156  2 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15577  1 ablk_helper
arc4                   12536  2 
btusb                  23443  0 
bluetooth             323622  22 bnep,btusb,rfcomm
iwldvm                219934  0 
mac80211              513247  1 iwldvm
snd_hda_codec_realtek    45592  1 
microcode              18830  0 
iwlwifi               143578  1 iwldvm
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
thinkpad_acpi          68941  0 
cfg80211              401436  3 iwlwifi,mac80211,iwldvm
nvram                  13986  2 thinkpad_acpi
lpc_ich                16864  0 
psmouse                90642  0 
serio_raw              13189  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
mei_me                 13933  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
mei                    66411  1 mei_me
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
tpm_tis                18563  0 
soundcore              12600  1 snd
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
i915                  589697  4 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46867  1 i915
sdhci_pci              18481  0 
ahci                   25579  5 
libahci                26554  1 ahci
drm                   242354  5 i915,drm_kms_helper
sdhci                  37468  1 sdhci_pci
e1000e                222921  0 
ptp                    18156  1 e1000e
pps_core               18546  1 ptp
wmi                    18590  0 
video                  18777  1 i915
```

Thinklight is working when I enable it using the hotkey Fn+Space. But I want to manually control it by shell commands. (on R61 I'm using it for IM notifications)

---

### Post by tgalati4 on 2013-11-02
I have a few blinking scripts set up for various notifications.  It's quite handy and somehow less iritating than dialog boxes.

Take a look at:

```
modinfo thinkpad_acpi
```

There is a switch for LEDs:

parm:           led:Simulates thinkpad-acpi procfs command at module load, see documentation

You are missing the module led_class, but it doesn't exist on 12.10, so it must have morphed into another module.  My thinkpad has 9.10 on it and is overdue for an upgrade.

If you search for documentation on thinkpad_acpi, you might be able to find the value for the switches.

---

