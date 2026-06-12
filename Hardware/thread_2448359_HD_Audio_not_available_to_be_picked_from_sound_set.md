---
title: "HD Audio not available to be picked from sound settings"
date: 2020-08-06
forum: Hardware
---

### Post by mscofield2 on 2020-08-06
Hello,
I'm trying to use the headphone jack on my desktop computer, but Ubuntu doesn't let me pick it from the sound settings.

Usually on Windows I would download VIA HD Audio drivers and it would work, but on Ubuntu it doesn't even though I installed one I found online:
[IMG]https://media.discordapp.net/attachments/471740270036385824/740932996890099812/unknown.png[/IMG]

The official VIA drivers page doesn't seem to support anything above Ubuntu 12.04. ([http://download.viatech.com/en/support/driversSelect.jsp](http://download.viatech.com/en/support/driversSelect.jsp))

---

### Post by Yellow Pasque on 2020-08-06
What is that and where did you get it? If it's from 2006, there's no way it's going to work with a modern kernel if it's an actual kernel module.
Anyway, the kernel already contains the correct module/driver ("snd-hda-intel") with code specific to VIA codecs. Proof: [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_via.c](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_via.c)

Get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by mscofield2 on 2020-08-06
Huh, but it doesn't let me choose it. What's the issue here then?

Here's the alsa information: [http://alsa-project.org/db/?f=274cfd6a0ab1bb5033445c62cc6e3327ff5494fc](http://alsa-project.org/db/?f=274cfd6a0ab1bb5033445c62cc6e3327ff5494fc)

---

### Post by Yellow Pasque on 2020-08-06
```
!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:274: no soundcards found...

ARECORD

arecord: device_list:274: no soundcards found...

!!Amixer output
!!-------------

!!-------Mixer controls for card PCH

Invalid card number.
Usage: amixer <options> [command]
```

^This is bad. I have a feeling whatever that via audiopack you installed has messed things up. Again, What is that and where did you get it? How did you install it? Are there any instructions to remove it?

---

### Post by mscofield2 on 2020-08-06
Random driver download site, there's a VIA instruction manual in the .zip file:
(from: [https://www.userdrivers.com/Sound-Card/VIA-VT1708-HD-Audio-Codec-Driver-0-84-for-Linux/](https://www.userdrivers.com/Sound-Card/VIA-VT1708-HD-Audio-Codec-Driver-0-84-for-Linux/))

---

### Post by Yellow Pasque on 2020-08-06
Did you actually make/make install that? Sorry, but I really have no idea what you did there. Also, it seems strange that you're using the original -26 kernel that came with the 20.04 ISO. Do you not update your system?
```
Kernel release:    5.4.0-26-generic
```

---

### Post by mscofield2 on 2020-08-06
Auto updating everything causes my system to freeze because of nvidia's newest driver, that apperently, my system can't support. (Happens on windows too so it's probably the hardware, if you're interested in what I have, it's a gtx1060 3gb)

I followed the manual, it provides a couple of commands to run to install it.

---

### Post by CatKiller on 2020-08-06
> **mscofield2 said:**
> Usually on Windows I would download... 

This is your fundamental problem.

It's why your Nvidia driver can't handle kernel updates, and it's potentially how you've messed up your sound.

Ubuntu already comes with the ability to download and install proprietary drivers, which will be able to handle kernel updates. Installing random things from random websites is a mistake.

You'll need to uninstall the thing that you got from the Nvidia website so that you can use the package manager to install the Nvidia driver.

If you did manage to install that random ancient kernel module that you got from goodness knows where you'll also need to remove that.

Then you'll be in a reasonable position to actually configure your sound. Onboard sound often has weird quirks that need to be accounted for, but it's generally just a tweak to what you already have installed.

---

### Post by mscofield2 on 2020-08-06
I don't think it was a kernel update, when I said update I meant `sudo apt upgrade`.

Any tips on how to remove installed drivers?

---

### Post by mscofield2 on 2020-08-06
I've tried to find where it is in `lsmod`, but I can't find it. Here's the output:

Module                  Size  Used by
lkp_Ubuntu_5_4_0_26_30_generic_69    24576  1
binfmt_misc            24576  1
nls_iso8859_1          16384  1
nvidia_drm             49152  5
nvidia_modeset       1114112  15 nvidia_drm
nvidia              20430848  831 nvidia_modeset
intel_rapl_msr         20480  0
intel_rapl_common      24576  1 intel_rapl_msr
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
kvm_intel             286720  0
input_leds             16384  0
joydev                 24576  0
drm_kms_helper        184320  1 nvidia_drm
ipmi_devintf           20480  0
ipmi_msghandler       106496  2 ipmi_devintf,nvidia
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
mei_hdcp               24576  0
kvm                   663552  1 kvm_intel
mei_me                 40960  1
mei                   106496  3 mei_hdcp,mei_me
eeepc_wmi              16384  0
asus_wmi               32768  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mac_hid                16384  0
wmi_bmof               16384  0
intel_cstate           20480  0
intel_rapl_perf        20480  0
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
drm                   491520  8 drm_kms_helper,nvidia_drm
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
ses                    20480  0
enclosure              16384  1 ses
scsi_transport_sas     36864  1 ses
hid_generic            16384  0
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
uas                    28672  0
usbhid                 57344  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
hid                   131072  2 usbhid,hid_generic
usb_storage            77824  3 uas
i2c_i801               32768  0
lpc_ich                24576  0
pata_acpi              16384  0
r8169                  90112  0
realtek                24576  1
wmi                    32768  2 asus_wmi,wmi_bmof
video                  49152  1 asus_wmi

---

### Post by CatKiller on 2020-08-06
> **mscofield2 said:**
> I don't think it was a kernel update, when I said update I meant `sudo apt upgrade`.

The kernel is just a package, the same as everything else, so normal package updates will include kernel updates. Updates to things that *aren't* the kernel won't generally cause you issues with graphics drivers. Updates to either the graphics driver or the kernel, when done through the package manager, won't generally cause problems either, since the interface between them uses DKMS. Updates to the kernel are known to break Nvidia's .run file, since that doesn't always use DKMS.

> Any tips on how to remove installed drivers?

You'd read the documentation of the thing you installed.

I have no idea if you've actually managed to install that ancient thing or not, nor what state the attempt has left your system in.

If you've used Nvidia's .run file, I understand that there's an option you can run it with again to uninstall those drivers.

Your card is supported by all modern versions of the Nvidia driver; the last to lose Linux support was the 600 series.

---

### Post by mscofield2 on 2020-08-08
Reinstalled ubuntu and now it's a fresh start. The integrated audio card still isn't detected, so what's my next move? @catkiller

---

### Post by CatKiller on 2020-08-08
> **mscofield2 said:**
> Reinstalled ubuntu and now it's a fresh start. The integrated audio card still isn't detected, so what's my next move?

To be more specific in the symptoms you're getting. What do you see in alsamixer, for example? There's a whole audio troubleshooting thread that has useful information.

All of my sound cards over the years have worked out of the box, so I don't have firsthand experience of working around the quirks of onboard sound, I just know that they exist.

---

### Post by mscofield2 on 2020-08-08
alsamixer shows this:

[IMG]https://ibb.co/C18GqCV[/IMG]

---

