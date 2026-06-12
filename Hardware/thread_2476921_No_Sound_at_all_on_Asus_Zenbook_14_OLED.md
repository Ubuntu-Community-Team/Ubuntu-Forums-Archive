---
title: "No Sound at all on Asus Zenbook 14 OLED"
date: 2022-07-12
forum: Hardware
---

### Post by jack9389 on 2022-07-12
Hello,

I just bought an Asus Zenbook 14 OLED (UX3402ZA), installed Ubuntu 22.04 LTS and there's absolutely no sound from the Speakers. This doesn't only happen on Ubuntu, but on all Linux distros. It works perfectly fine with Windows 11.

uname -a:

```
Linux zenbook 5.15.0-41-generic #44-Ubuntu SMP Wed Jun 22 14:20:53 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

aplay -l

```
card 0: sofhdadsp [sof-hda-dsp], device 0: HDA Analog (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 1: HDA Digital (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 4: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 5: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In alsamixer, everything is "OO" meaning it's unmuted. 

Inxi -a:

```
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    driver: sof-audio-pci-intel-tgl
  Sound Server-1: ALSA v: k5.15.0-41-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```

Any help is appreciated and I desperately need to get sound working.

---

### Post by Yellow Pasque on 2022-07-12
My suggestions:
1. Make sure you have the 'firmware-sof-signed' package installed: [https://askubuntu.com/questions/1404894/firmware-sof-signed-was-in-21-10-impish-but-is-not-found-in-22-04-lts-jammy](https://askubuntu.com/questions/1404894/firmware-sof-signed-was-in-21-10-impish-but-is-not-found-in-22-04-lts-jammy)
2. Try a newer kernel as there have been some fixes since 5.15: [https://github.com/torvalds/linux/commits/master/sound/soc/sof/intel/pci-tgl.c](https://github.com/torvalds/linux/commits/master/sound/soc/sof/intel/pci-tgl.c)

---

### Post by #&amp;thj^% on 2022-07-12
Yellow Pasque has offered some good advice, just to check with this work-around, would you try this first:
```
sudo rmmod snd_sof_pci_intel_tgl
sudo modprobe snd_sof_pci_intel_tgl
```
Those commands just reloads the Driver.
Let us know if this works, also this is supposed to be fixed in kernels 5.16 and newer, however kernel 5.18 seems to bring back the problem.

---

### Post by tommc11 on 2022-07-19
Hi 1fallen,

I'm not the OP but have the same Zenbook 14 and the same problem.  I tried your two sudo commands above and they didn't help.  I should note that I am running the Live version from USB.  I want to make sure everything works ok before I move forward.  I'm having the same problem on this laptop with other Ubuntu distros (e.g. ZorinOS) and I have even tried Fedora 36 and it has the sound issue too.  Please advise... I'm willing to try other steps.  I don't want to use Windows 11.  thanks.

---

### Post by tommc11 on 2022-07-19
Hi again 1fallen,

I went ahead and installed 22.04 alongside Win 11.  I tried the two sudo commands again and still no luck.  Please let me know if I should try something else before trying what Yellow Pasque suggested.  thx

---

### Post by sridel on 2022-07-30
Try this: [https://askubuntu.com/questions/1225954/no-sound-with-ubuntu-20-04-on-asus-zenbook-ux533ftc/1263676#1263676](https://askubuntu.com/questions/1225954/no-sound-with-ubuntu-20-04-on-asus-zenbook-ux533ftc/1263676#1263676)

---

### Post by #&amp;thj^% on 2022-07-30
> **tommc11 said:**
> Hi again 1fallen,

I went ahead and installed 22.04 alongside Win 11.  I tried the two sudo commands again and still no luck.  Please let me know if I should try something else before trying what Yellow Pasque suggested.  thx

Sorry I'm late replying back, but have a look here as well as posted by sridel : [https://www.linux.org/threads/solved-asus-zenbook-15-ux534f-realtek-hd-audio-problem.27384/#post-94194](https://www.linux.org/threads/solved-asus-zenbook-15-ux534f-realtek-hd-audio-problem.27384/#post-94194)

I had a friend with a setup like you both on Arch though but shouldn't matter here (Audio)
I used:
```
hda-verb /dev/snd/hwC0D0 0x20 0x500 0x1b
hda-verb /dev/snd/hwC0D0 0x20 0x477 0x4a4b
hda-verb /dev/snd/hwC0D0 0x20 0x500 0xf
hda-verb /dev/snd/hwC0D0 0x20 0x477 0x74
```I'll try and be more mindful on this thread..

---

### Post by youliang on 2022-08-06
Hi 1fallen, 

I also have the same issue with my newly bought zenbook ux3402. Audio works on windows but not on ubunu22.04. I updated the kernel 5.19, but with no luck. I also tried the `hda-verb ... ` approach but the audio still isn't working. 

Not sure if this thread will provide more clues? [https://github.com/thesofproject/sof/issues/5867](https://github.com/thesofproject/sof/issues/5867)

---

### Post by nikola-jandik-seznam on 2022-08-22
im on um3402 with dolby from cirrus logic? cs35l41 audio works perfect on Bluetooth, 3.5mm j4ck or HDMI¨

maybe in kernel 6.X will be fixed/added [URL="https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/diff/sound/pci/hda/cs35l41_hda.c?id=v6.0-rc2&id2=v6.0-rc1"]https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/diff/sound/pci/hda/cs35l41_hda.c?id=v6.0-rc2&id2=v6.0-rc1
[/URL]
5.19.3-051903-generic #202208211442 SMP PREEMPT_DYNAMIC Sun Aug 21 14:54:49 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

[    2.661357] Serial bus multi instantiate pseudo device driver CSC3551:00: Instantiated 2 I2C devices.
[    2.673436] cs35l41-hda i2c-CSC3551:00-cs35l41-hda.0: error -EINVAL: Platform not supported -22
[    2.673540] cs35l41-hda: probe of i2c-CSC3551:00-cs35l41-hda.0 failed with error -22
[    2.673615] cs35l41-hda i2c-CSC3551:00-cs35l41-hda.1: error -EINVAL: Platform not supported -22
[    2.673693] cs35l41-hda: probe of i2c-CSC3551:00-cs35l41-hda.1 failed with error -22
[    2.690065] ccp 0000:04:00.2: enabling device (0000 -> 0002)
[    2.690344] ccp 0000:04:00.2: ccp: unable to access the device: you might be running a broken BIOS.
[    2.699598] snd_rn_pci_acp3x 0000:04:00.5: enabling device (0000 -> 0002)
[    2.700495] ccp 0000:04:00.2: tee enabled
[    2.700498] ccp 0000:04:00.2: psp enabled

---

### Post by tctimmeh on 2022-08-29
I believe I am having the same problem on a ZenBook UP6502ZD. I get no sound from the internal speakers, though they work ok in windows.

I've verified that nothing is muted in both system settings and alsamixer. I upgraded firmware-sof-signed to the latest version (2.1.1). I've tried different kernels (5.16 and 5.19). I even tried the weird hda-verb commands from an old bug report. Nothing works so far.

Any help would be really appreciated. This is the last thing that doesn't work perfectly on this machine and I'd really love to get it fixed.

```
$ inxi -SMA
System:
  Host: jaguar Kernel: 5.15.0-46-generic x86_64 bits: 64 Desktop: GNOME 42.2
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Convertible System: ASUSTeK product: Zenbook UP6502ZD_UP6502ZD v: 1.0
    serial: <superuser required>
  Mobo: ASUSTeK model: UP6502ZD v: 1.0 serial: <superuser required>
    UEFI: American Megatrends LLC. v: UP6502ZD.303 date: 05/16/2022
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    driver: sof-audio-pci-intel-tgl
  Sound Server-1: ALSA v: k5.15.0-46-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

$ lspci -v | grep -i audio
0000:00:1f.3 Multimedia audio controller: Intel Corporation Alder Lake PCH-P High Definition Audio Controller (rev 01)
	Kernel driver in use: sof-audio-pci-intel-tgl

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: sofhdadsp [sof-hda-dsp], device 0: HDA Analog (*) []
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 1: HDA Digital (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 4: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 5: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by hypho on 2022-09-10
sound speakers works but with kernel > 5.19.3

```

~$ uname -r
5.19.3-test2+

$ cat /sys/class/dmi/id/product_name 
Zenbook UM5302TA_UM5302TA


```

---

### Post by hypho on 2022-09-10
sound speakers works but with kernel > 5.19.3

```
~$ uname -r 5.19.3-test2+

$ cat /sys/class/dmi/id/product_name 
Zenbook UM5302TA_UM5302TA 

```

---

### Post by hypho on 2022-09-10
speaker sound same dint works with kernel  5.15.0-47

---

### Post by mkenny28 on 2022-09-15
> **hypho said:**
> sound speakers works but with kernel > 5.19.3

```
~$ uname -r 5.19.3-test2+

$ cat /sys/class/dmi/id/product_name 
Zenbook UM5302TA_UM5302TA 

```


How did you get it to work? I have a Zenbook UM5302TA running Ubuntu 22.0.4.1 and I have tried every kernel from 5.15 to 6.0 rc3 and cannot get sound through speakers at all. I have seen some Arch patches out there but I am not having any success patching kernels.

---

### Post by pokhrelashok2 on 2022-09-28
Has anyone managed to fix the issue? I am using the latest 6.0.0-060000rc7-generic kernel and there is still no sound.

---

### Post by nikola-jandik-seznam on 2022-10-25
no sound for UM3402YA-UM3402YA 6.0.1-060001-generic #202210120833 SMP PREEMPT_DYNAMIC Wed Oct 12 08:37:06 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
[B][URL="https://patchwork.kernel.org/"]

https://patchwork.kernel.org/[/URL] ALSA development[/B]

[v1] ALSA: hda/realtek: Add quirk for ASUS Zenbook using CS35L41

[https://patchwork.kernel.org/project/alsa-devel/patch/20221018121506.2561397-1-sbinding@opensource.cirrus.com/](https://patchwork.kernel.org/project/alsa-devel/patch/20221018121506.2561397-1-sbinding@opensource.cirrus.com/)

diff --git a/sound/pci/hda/patch_realtek.c b/sound/pci/hda/patch_realtek.c
index 7c177426bf303..79acd2a2caf20 100644
--- a/sound/pci/hda/patch_realtek.c
+++ b/sound/pci/hda/patch_realtek.c
@@ -9395,6 +9395,7 @@  static const struct snd_pci_quirk alc269_fixup_tbl[] = {
     SND_PCI_QUIRK(0x1043, 0x1ccd, "ASUS X555UB", ALC256_FIXUP_ASUS_MIC),
     SND_PCI_QUIRK(0x1043, 0x1d42, "ASUS Zephyrus G14 2022", ALC289_FIXUP_ASUS_GA401),
     SND_PCI_QUIRK(0x1043, 0x1d4e, "ASUS TM420", ALC256_FIXUP_ASUS_HPE),
+    SND_PCI_QUIRK(0x1043, 0x1e02, "ASUS UX3402", ALC245_FIXUP_CS35L41_SPI_2),
     SND_PCI_QUIRK(0x1043, 0x1e11, "ASUS Zephyrus G15", ALC289_FIXUP_ASUS_GA502),
     SND_PCI_QUIRK(0x1043, 0x1e51, "ASUS Zephyrus M15", ALC294_FIXUP_ASUS_GU502_PINS),
     SND_PCI_QUIRK(0x1043, 0x1e5e, "ASUS ROG Strix G513", ALC294_FIXUP_ASUS_G513_PINS),

[COLOR=#ff0000]**how add quirk for UM3402 zenbook ?! **[/COLOR]

---

### Post by siial on 2022-11-03
Any update on this? Just got my UM3402 and really want to remove Windows and go full Linux..

---

### Post by nikola-jandik-seznam on 2022-11-03
no sound

Zenbook-UM3402YA-UM3402YA 6.1.0-060100rc3-generic #202210301931 SMP PREEMPT_DYNAMIC Sun Oct 30 23:40:22 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```


winfo | grep CSC3551
Serial bus multi instantiate pseudo device driver: /devices/platform/AMDI0010:03/CSC3551:00
  platform device: name = CSC3551:00
    path = /devices/platform/AMDI0010:03/CSC3551:00
    type = "", modalias = "acpi:CSC3551:", driver = "Serial bus multi instantiate pseudo device driver"
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/AMDI0010:03/CSC3551:00
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/AMDI0010:03/CSC3551:00
  E: MODALIAS=acpi:CSC3551:
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/AMDI0010:03/CSC3551:00/wakeup/wakeup50
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/AMDI0010:03/CSC3551:00/wakeup/wakeup50
  P: /devices/platform/AMDI0010:03/CSC3551:00
  E: DEVPATH=/devices/platform/AMDI0010:03/CSC3551:00
  E: MODALIAS=acpi:CSC3551:
  E: ID_PATH=platform-CSC3551:00
  E: ID_PATH_TAG=platform-CSC3551_00
  P: /devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.0
  E: DEVPATH=/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.0
  P: /devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.1
  E: DEVPATH=/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.1
/devices/LNXSYSTM:00/LNXSYBUS:00/AMDI0010:03/CSC3551:00
/devices/LNXSYSTM:00/LNXSYBUS:00/AMDI0010:03/CSC3551:00/wakeup/wakeup50
/devices/platform/AMDI0010:03/CSC3551:00
/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.0
/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.1




```

```

hwinfo | grep cs35l41
     cs35l41-hda: module = snd_hda_scodec_cs35l41_spi
     cs35l41-hda: module = snd_hda_scodec_cs35l41_i2c
  P: /devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.0
  E: DEVPATH=/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.0
  E: MODALIAS=i2c:cs35l41-hda
  P: /devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.1
  E: DEVPATH=/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.1
  E: MODALIAS=i2c:cs35l41-hda
/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.0
/devices/platform/AMDI0010:03/i2c-1/i2c-CSC3551:00-cs35l41-hda.1
  snd_hda_scodec_cs35l41_spi 16384 0 - Live 0x0000000000000000
  snd_hda_scodec_cs35l41_i2c 16384 0 - Live 0x0000000000000000
  snd_hda_scodec_cs35l41 45056 2 snd_hda_scodec_cs35l41_spi,snd_hda_scodec_cs35l41_i2c, Live 0x0000000000000000
  snd_hda_cs_dsp_ctls 20480 1 snd_hda_scodec_cs35l41, Live 0x0000000000000000
  cs_dsp 57344 2 snd_hda_scodec_cs35l41,snd_hda_cs_dsp_ctls, Live 0x0000000000000000
  snd_soc_cs35l41_lib 36864 3 snd_hda_scodec_cs35l41_spi,snd_hda_scodec_cs35l41_i2c,snd_hda_scodec_cs35l41, Live 0x0000000000000000
  snd 114688 33 snd_ctl_led,snd_sof,snd_soc_core,snd_compress,snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hda_scodec_cs35l41,snd_hwdep,snd_hda_cs_dsp_ctls,snd_seq,snd_pcm,snd_seq_device,snd_timer, Live 0x0000000000000000




```

---

### Post by Yellow Pasque on 2022-11-05
> **nikola-jandik-seznam said:**
> [COLOR=#ff0000]**how add quirk for UM3402 zenbook ?! **[/COLOR]

You'll need the subsystem PCI ID for the device. The vendor ID should be 1043 (Asus)
```
lspci -nn -v | grep -i audio
```

Note: if lspci command does not return anything, run this and try it again.
```
sudo update-pciids
```

E-mail [email]alsa-devel@alsa-project.org[/email] (make sure e-mail is plain text) with the ID and ask them to add it to the quirk list.

---

### Post by Sidster on 2022-11-08
> **Yellow Pasque said:**
> You'll need the subsystem PCI ID for the device. The vendor ID should be 1043 (Asus)
```
lspci -nn -v | grep -i audio
```

Note: if lspci command does not return anything, run this and try it again.
```
sudo update-pciids
```

E-mail [email]alsa-devel@alsa-project.org[/email] (make sure e-mail is plain text) with the ID and ask them to add it to the quirk list.


I don't think this is correct because when I run this on my UM3402 I get:
```
lspci -nn -v | grep -i audio
04:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Renoir Radeon High Definition Audio Controller [1002:1637]
04:00.5 Multimedia controller [0480]: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor [1022:15e2] (rev 01)
04:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller [1022:15e3]
	DeviceName: HD Audio Controller
```

And when I run it on my UM425 with working audio I get the exact same results:

```
lspci -nn -v | grep -i audio
04:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Renoir Radeon High Definition Audio Controller [1002:1637]
04:00.5 Multimedia controller [0480]: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor [1022:15e2] (rev 01)
04:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller [1022:15e3]
	DeviceName: HD Audio Controller
```

---

### Post by nikola-jandik-seznam on 2022-12-11
it works! :-D

[https://superuser.com/questions/1719920/no-sound-from-internal-speakers-on-laptop-but-headphone-jack-and-hdmi-works/1754954#1754954](https://superuser.com/questions/1719920/no-sound-from-internal-speakers-on-laptop-but-headphone-jack-and-hdmi-works/1754954#1754954)

```

                                   []("https://superuser.com/posts/1754954/timeline")  
          
                       I got sound via loud speakers to work on my Asus Zenbook UM3402YA. Here are the steps:
 
[LIST=1]
[*]Downloaded and installed linux kernel 6.1-rc6 from [www.kernel.org]("http://www.kernel.org")

[*]Installed firmware (debian: firmware-amd-graphics.deb) and Cirrus firmware: [https://github.com/CirrusLogic/linux-firmware/tree/main/cirrus](https://github.com/CirrusLogic/linux-firmware/tree/main/cirrus)

[*]Applied this patch (may not be necessary): [https://www.spinics.net/lists/platform-driver-x86/msg35828.html](https://www.spinics.net/lists/platform-driver-x86/msg35828.html)

[*]Added the following lines to file linux/sound/pci/hda/cs35l42.c, line 1237:
  } else if (strncmp(hid, "CSC3551", 7) == 0) {
     hw_cfg->bst_type = CS35L41_INT_BOOST;
     hw_cfg->gpio1.func = CS35l41_VSPK_SWITCH;
     hw_cfg->gpio1.valid = true;
 } else {

[*]Built kernel, reboot. You should see the driver load in /var/log/syslog:
  debian kernel: [8.049401] cs35l41-hda i2c-CSC3551:00-cs35l41-hda.0: Cirrus Logic CS35L41 (35a40), Revision: B2
 debian kernel: [8.049544] cs35l41-hda i2c-CSC3551:00-cs35l41-hda.1: Reset line busy, assuming shared reset
 debian kernel: [8.083870] cs35l41-hda i2c-CSC3551:00-cs35l41-hda.1: Cirrus Logic CS35L41 (35a40), Revision: B2

[*]Still no sound. Made a half-educated guess about a quirk. Add the following line to file linux/sound/pci/hda/patch_realtek.c, line 9406:
  SND_PCI_QUIRK(0x1043, 0x1e12, "ASUS UM3402", ALC287_FIXUP_CS35L41_I2C_2),
 Built kernel, reboot. You should find that firmware was loaded:
  debian kernel: [8.582376] cs35l41-hda i2c-CSC3551:00-cs35l41-hda.0: DSP1: Firmware version: 3
 debian kernel: [8.582382] cs35l41-hda i2c-CSC3551:00-cs35l41-hda.0: DSP1: cirrus/cs35l41-dsp1-spk-prot.wmfw: Fri 24 Ju

[*]Test sound via loudspeakers.
[/LIST]
     
                                                                                                

```

---

### Post by pobudi on 2022-12-20
Could you explain how you installed firmware? especially the cirrus one, i do not understand which file should i download.

---

### Post by docker-decompose on 2023-02-16
We had a similar issue with Asus Zenbook S OLED recently, no sound from speakers when using Ubuntu, while the sound from headphones worked fine.
Managed to resolve it by adding a custom ACPI image to grub. Browsing led us to the following resources:

[https://github.com/latin-1/um5302ta](https://github.com/latin-1/um5302ta) - submitted patches for this model (if you are reading it, THANK YOU, you saved our life)
[https://github.com/lbschenkel/acer-sf314_43-acpi-patch](https://github.com/lbschenkel/acer-sf314_43-acpi-patch) - this repo description (in spite of being unrelated to our issue) gave us a clue on how to patch and recompile DSDT (sorry, I'm a Linux noob).

So we did the following:

- Updated to the latest kernel (the patch requires kernel version &#8805; 6.0.9, we are using 6.1.12-060112-generic now)
- Followed the DSDT recompiling instructions:
> 

[LIST=1]
[*]Install the acpica package 
[*]Run acpidump -b to dump all ACPI tables to *.dat files 
[*]Run iasl -we -w3 -e *.dat -d dsdt.dat to decompile the DSDT to dsdt.dsl 
[*]Patch the DSDT via patch -F0 -N < dsdt.patch 
[*]Recompile the DSDT via iasl -ve dsdt.dsl 
[*]Generate initrd image:
[LIST=1]
[*]mkdir -p kernel/firmware/acpi 
[*]cp dsdt.aml kernel/firmware/acpi/ 
[*]find kernel | cpio -H newc --create > /boot/acpi-override.img 
[/LIST]
        
[/LIST]

   Step 4 failed for us, so we just copied the needed code from the patch ([https://github.com/latin-1/um5302ta/blob/main/patches/dsdt/spkr-dsd.patch](https://github.com/latin-1/um5302ta/blob/main/patches/dsdt/spkr-dsd.patch)) to dsdt.dsl file manually.
*  'find kernel | cpio -H newc --create > /boot/acpi-override.img' *also failed to generate a file for some reason, even with 'sudo', so we compiled acpi image to Home directory and then moved it to boot:
```
find kernel | cpio -H newc --create > ~/acpi-override.img
sudo cp acpi-override.img /boot/acpi-override.img
```
- Changed grub settings by adding this line to /etc/default/grub:```
GRUB_EARLY_INITRD_LINUX_CUSTOM = "... acpi-override.img"
```
- Updated grub:
  ```
sudo update-grub
```
- Then restarted the system, and the speakers started working eventually!

I hope it helps someone too : )

---

### Post by devcoach on 2023-03-09
I also have same error No sound on Ubuntu 22.04 also this items is not work:


[LIST=1]
[*]Sound is not work
[*]fingerprint failed when set new fingerprint
[*]touchpad two and three gestures effects is not work
[/LIST]

---

### Post by nikola-jandik-seznam on 2023-04-18
> **devcoach said:**
> I also have same error No sound on Ubuntu 22.04 also this items is not work:


[LIST=1]
[*]Sound is not work 
[*]fingerprint failed when set new fingerprint 
[*]touchpad two and three gestures effects is not work 
[/LIST]


after a year I sold asus um3402 the laptop and bought T14s gen2 with 5850u, here works everything, asus never more :-D ( 
when Asus support wrote to me that I would make a video, I already sent them to hell )

btw. 
I described the problem to asus support, how they have messed up bios, I sent them links to discussions about what problems people have under Linux and they wrote and I made a video about how the sound does not work at the end

---

