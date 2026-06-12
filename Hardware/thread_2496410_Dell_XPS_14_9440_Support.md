---
title: "Dell XPS 14 9440 Support"
date: 2024-03-26
forum: Hardware
---

### Post by christian-p26 on 2024-03-26
Hello, 
First time poster here looking for some help. I recently got the new Dell XPS 9440 Laptop with the RTX 4050 dedicated graphics card.

[https://www.dell.com/en-us/shop/cty/pdp/spd/xps-14-9440-laptop/usexcpcto9440mtl02?tfcid=91049735&&gacd=9684992-1105-5761040-266906002-0&dgc=ST&SA360CID=71700000109860337&gad_source=1&gclid=CjwKCAjw5ImwBhBtEiwAFHDZx_d_JpMbUDelZMUxriN8ShpZqiJ9qFEADLVIigVHxGRLHUXDwlEvjBoCtzUQAvD_BwE&gclsrc=aw.ds](https://www.dell.com/en-us/shop/cty/pdp/spd/xps-14-9440-laptop/usexcpcto9440mtl02?tfcid=91049735&&gacd=9684992-1105-5761040-266906002-0&dgc=ST&SA360CID=71700000109860337&gad_source=1&gclid=CjwKCAjw5ImwBhBtEiwAFHDZx_d_JpMbUDelZMUxriN8ShpZqiJ9qFEADLVIigVHxGRLHUXDwlEvjBoCtzUQAvD_BwE&gclsrc=aw.ds)

This machine ships with Windows but I was needing to load Ubuntu 22.04 on it. When I do the display fails to load unless I remove the Nvidia driver and use the Xorg driver instead. In addition webcam, speaker, and microphone all fail. I have tried to update the kernel to 6.8 but libc6 is too old to allow this. I have tested Ubuntu 23.04 and the nightly 24.04 releases. On 23.04 there is no difference from the behavior seen on 22.04 however with 24.04 I do get Nvidia support out of the box which is great and seems to indicate kernel 6.8 has support for this graphics card except that the devices mentioned above fail still. Looking at dmesg I saw that perhaps audio card firmware is missing so I followed the instructions in the sof-bin repo to install them. This seems to have cleared the dmesg error, yet no audio still. 

Unfortunately even if 24.04 was successful at this time it is not a viable option as certain compilers and applications for my work only support up to 22.04. 

Any advice on how to get Ubuntu 22.04 would be greatly appreciated.
Thank you in advance,

---

### Post by &amp;KyT$0P# on 2024-03-26
> **christian-p26 said:**
> seems to indicate kernel 6.8 has support for this graphics card 

So as a test, does [Pop!_OS 22.04]("https://pop.system76.com/") work?  It is based on Ubuntu 22.04, currently uses 6.8 kernel, and has a Nvidia-specific ISO image.

---

### Post by MAFoElffen on 2024-03-27
I'm not even going to comment on PopOS> That is a derivative of Ubuntu, but is not Ubuntu...

Your CPU is Intel Ultra, and your GPU is 4060. 

Ubuntu Noble 24.04 does have Kernel 6.8... But again, the key sticking point is that you said that  
> **christian-p26 said:**
> 
Unfortunately even if 24.04 was successful at this time it is not a  viable option as [COLOR=#ff0000]certain compilers and applications for my work only  support up to 22.04.[/COLOR] 

I have been testing DEV Noble since it hit the repo's. Even with that, that (out-of-the-box) wont work for you, without modulations.

To fall within the bounds of your requirements and boundaries... You have two options...

1. ) You can start out with 22.04 and upgrade the kernel and Linux util's to 6.8... (It needs the base upgraded to run that kernel) 

2.) Or Upgrade to 24.04 (which is still in beta), but add the gcc-11 & g++-11 to it, to fulfill your legacy compiler challenges. You would have to use update-alternative so that it has priorities set on the compilers, and you would then have a facility to choose which...

What other applications, with their versions are in your requirements?

---

### Post by &amp;KyT$0P# on 2024-03-27
> **MAFoElffen said:**
> PopOS> That is a derivative of Ubuntu, but is not Ubuntu...

I should have explained why I suggested trying it "as a test":

[LIST]
[*]If graphics works, and Pop!_OS 22.04 meets OP's needs, it is the easiest way to get 6.8 kernel with a 22.04 base on non-System76 hardware.
[/LIST]
[LIST]
[*]If graphics works, but OP finds that Pop!_OS 22.04 does not meet their needs in ways Ubuntu 22.04 would, it is possible to install that kernel/driver stack on Ubuntu 22.04 via the System76 driver PPA, even on non-System76 hardware.  Note that setting this up correctly on non-System76 systems requires an extra step (and the non-System76 systems on which I have done this don't have Nvidia graphics, so not sure if setting up the correct Nvidia driver for OP's laptop would require additional step?)
[/LIST]

---

### Post by Yellow Pasque on 2024-03-27
The Nvidia driver should work. Which version were you trying?

Also, is this laptop one with hybrid graphics or did Dell disable the Intel GPU?

---

### Post by dook123 on 2024-03-28
Hey there.  I'm in the same basket as you.  Dell XPS 14" (9440) and trying to get Ubuntu working on it.

I stumbled across this - [https://askubuntu.com/questions/1508285/boot-fails-on-dell-xps-9440-with-fresh-23-10-installation/1508411#1508411](https://askubuntu.com/questions/1508285/boot-fails-on-dell-xps-9440-with-fresh-23-10-installation/1508411#1508411)  which was crazy helpful.  Here's how i got my machine running on 23.10


[LIST]
[*]Downloaded ubuntu-23.10.1-desktop-amd64 and burned to USB, booted from USB to install.  I also ensured i had a USB-C ethernet dongle attached during the installation, which gave me working internet during the process.
[*]During the setup, theres a prompt to "Allow installation of Third Party drivers".  Make sure this is UNSELECTED.
[*]Continue the installation, and you should get it installed OK, and wifi should be working.
[*]Now, using Mainline ([https://github.com/bkw777/mainline?tab=readme-ov-file#install](https://github.com/bkw777/mainline?tab=readme-ov-file#install)) upgrade your kernel to 6.8.
[*]Once installed, you should then be able to install Nvidia drivers using **sudo ubuntu-drivers install**
[/LIST]
Thats where i currently am, and it's working OK.  But so far, the following still don't work:


[LIST]
[*]Audio
[*]Webcam
[/LIST]

Keen to follow along on this thread too, help get it working with the remaining bits.

---

### Post by dook123 on 2024-03-28
Also replying to some other comments

**MAFoElffen** = The 9640 (16") has a 4060 GPU.  9440 (14") has a 4050 GPU.

**Yellow Pasqu** = AFAIK, they have the dual gfx cards in.  Here's the output of lspci ([https://ibb.co/VgpRhRD](https://ibb.co/VgpRhRD))

[IMG]https://ibb.co/VgpRhRD[/IMG]

Keen to help out with any details etc which can help it fully get running, so please let me know what i can do
[IMG]https://ibb.co/VgpRhRD[/IMG]

---

### Post by Yellow Pasque on 2024-03-28
Maybe this fixes your graphics issues with 22.04:
[https://ubuntuforums.org/showthread.php?t=2495988&p=14182328#post14182328](https://ubuntuforums.org/showthread.php?t=2495988&p=14182328#post14182328)

> **dook123 said:**
> Keen to help out with any details etc which can help it fully get running
Thanks for the info.

---

### Post by christian-p26 on 2024-03-28
Hello all,
Thank you so much for the help we have some progress!

I have currently gotten Ubuntu 22.04 with the Nvidia 550 driver working and booting! I ended up needing to compile the 6.8(.2) kernel and modules myself and use the Nvidia provided .run installer from their site. I did this because if I just used the downloads from mainline PEM when I later went to install Nvidia Drivers it would complain that the gcc version used to compile the kernel did not match what is on system. I am sure I could of just updated gcc or made the install work similar to what @dook123 but compiling the kernel for me seemed easy enough (and interesting). 

I am however still in the same boat as @dook123 where no built in audio, mic, or webcam are working. If I plug in a microphone I can get it to work but no external hdmi speaker. I have looked into dmesg and it is complaining about a missing topology file 'sof-mtl-rt711.tplg' which I cant seem to find anywhere including the sof-bin repo. I am also confused why it searches for this file as my understanding is the audio chipset is a Cirrus model. 

Any advice would be amazing and once again thank you!

---

### Post by mixer2 on 2024-04-01
@dook123 glad that the hint that the kernel 6.8 is mostly working out of the box on askubuntu helped you.
it seems that this forum is way better place to discuss and help each other to get the xps 14 to work.

so for the webcam:
there are open pull-requests to make ipu6 drivers work on 6.8 kernel [https://github.com/intel/ipu6-drivers/pull/213](https://github.com/intel/ipu6-drivers/pull/213) [https://github.com/intel/ivsc-driver/pull/44](https://github.com/intel/ivsc-driver/pull/44)

however i didn't got icamera to compile [https://github.com/intel/icamerasrc/tree/icamerasrc_slim_api](https://github.com/intel/icamerasrc/tree/icamerasrc_slim_api)

for details check: [https://askubuntu.com/questions/1508977/how-to-get-ipu6-webcam-xps-14-9440-to-work-on-meteor-lake-platform](https://askubuntu.com/questions/1508977/how-to-get-ipu6-webcam-xps-14-9440-to-work-on-meteor-lake-platform)

i think we might just have to wait a little bit longer until they got 6.8 kernel support merged in all the ipu6, icamera repos, then just installing the nightly builds should just work, i guess. but if anyone has a better idea, would be great. i think audio isn't that important, but webcam in a time where home office is that common, would be nice.
does anyone know which sensor is used in the xps 14 9440, or how we could find out? if it's a sensor that is not yet supported by ipu6 drivers (HM11B1, OV01A1S, OV01A10, OV02C10, OV02E10, OV2740, HM2170, HM2172 and HI556 sensors) then we might have to wait even longer.

for audio i'm more optimistic. with the command:
$ lspci -nn | grep -i audio

i get:
0000:00:1f.3 Multimedia audio controller [0401]: Intel Corporation Meteor Lake-P HD Audio Controller [8086:7e28] (rev 20)

and if we google we find Dell Precision 3591 with the same audio controller as ubuntu certified ([https://ubuntu.com/certified/202312-33218/22.04%20LTS](https://ubuntu.com/certified/202312-33218/22.04%20LTS)). might be that we need some propritery driver from the dell packages or something, but it sounds as if we could get it to work with some research (or some help from someone who know about all the linux driver stuff).
it might even be, that it's the same webcam, since it's also dell and also fhd. but as said, there ipu6 6.8 kernel support is the limiting factor, as far as i understand.

so far that's everything i know :-D
if i get something to work, i'll post it here.

one more question: is s0 standby working for you guys? if yes, how much battery does it take? s0 is not working for me, but i think it might be, because i'm currently running ubuntu from external ssd.

---

### Post by Yellow Pasque on 2024-04-01
> complaining about a missing topology file 'sof-mtl-rt711.tplg' 

Shot in the dark here, but maybe the file it should be looking for is sof-mtl-rt711-4ch.tplg (this laptop has quad speakers from what I can see). Try making a symbolic link (and rebooting):
```
cd /lib/firmware/intel/sof-ace-tplg/
sudo ln -s sof-mtl-rt711-4ch.tplg sof-mtl-rt711.tplg
```

If it doesn't work, look at dmesg again to see if anything changed. 

Whether it works or not, maybe open an issue here: [https://github.com/thesofproject/sof-bin/issues](https://github.com/thesofproject/sof-bin/issues) I'm going to guess they will make a link in their repo like I did or get/create the missing file if needed. Either that, or they can figure out where the reference to "sof-mtl-rt711.tplg" is coming from and fix that.

---

### Post by Yellow Pasque on 2024-04-01
> **mixer2 said:**
> however i didn't got icamera to compile [https://github.com/intel/icamerasrc/tree/icamerasrc_slim_api](https://github.com/intel/icamerasrc/tree/icamerasrc_slim_api)

for details check: [https://askubuntu.com/questions/1508977/how-to-get-ipu6-webcam-xps-14-9440-to-work-on-meteor-lake-platform](https://askubuntu.com/questions/1508977/how-to-get-ipu6-webcam-xps-14-9440-to-work-on-meteor-lake-platform)

To me, it looks like you either need gstreamer 1.24.x or maybe an older version of icamera.

---

### Post by dook123 on 2024-04-05
So...i found this thread [https://github.com/thesofproject/linux/issues/4879](https://github.com/thesofproject/linux/issues/4879) and it's for the 16" 9640, but i assume it's a similar audio device in the 9440.

I'm not an expert in any of this, but it sounds like the latest kernel seems to be picking up the audio device incorrectly, and thinking it needs to use the rt711 drivers, but it should actually be the cs35l56 driver.  And the fix is available (or it works in one of the latest beta Linux kernels.

So using mainline, i changed my kernel to 6.9-rc2 (Beta/Release Candidate) rebooted and it's now seemingly using the right driver, but i'm still can't get the audio device to appear, and still only see "Dummy Output" as a device.

For reference, here's a dump of dmesg

[B]sudo dmesg | grep sof
[/B][    0.057606] software IO TLB: area num 32.
[    0.605387] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.605388] software IO TLB: mapped [mem 0x0000000042986000-0x0000000046986000] (64MB)
[    0.701510] integrity: Loaded X.509 cert 'Microsoft Windows Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53'
[    3.702454] audit: type=1400 audit(1712298943.542:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/opt/microsoft/msedge/msedge" pid=760 comm="apparmor_parser"
[    3.939309] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    3.939415] sof-audio-pci-intel-mtl 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[    3.939422] sof-audio-pci-intel-mtl 0000:00:1f.3: enabling device (0000 -> 0002)
[    3.939522] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    5.037571] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    5.038373] sof-audio-pci-intel-mtl 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[    5.038744] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    5.038859] sof-audio-pci-intel-mtl 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.046837] sof-audio-pci-intel-mtl 0000:00:1f.3: use msi interrupt mode
[    5.066250] sof-audio-pci-intel-mtl 0000:00:1f.3: hda codecs found, mask 4
[    5.069522] sof-audio-pci-intel-mtl 0000:00:1f.3: Firmware paths/files for ipc type 1:
[    5.069526] sof-audio-pci-intel-mtl 0000:00:1f.3:  Firmware file:     intel/sof-ipc4/mtl/sof-mtl.ri
[    5.069527] sof-audio-pci-intel-mtl 0000:00:1f.3:  Firmware lib path: intel/sof-ipc4-lib/mtl
[    5.069528] sof-audio-pci-intel-mtl 0000:00:1f.3:  Topology file:     intel/sof-ace-tplg/sof-mtl-cs42l43-l0-cs35l56-l23.tplg
[    5.070330] sof-audio-pci-intel-mtl 0000:00:1f.3: Loaded firmware library: ADSPFW, version: 2.9.0.1
[    5.177623] sof-audio-pci-intel-mtl 0000:00:1f.3: Booted firmware version: 2.9.0.1
[   15.455299] platform sof_sdw: deferred probe pending: sof_sdw: snd_soc_register_card failed -517


But the moritz89 seems to have got it working, but i don't know how.
Anyways, figured i'd post, see if it helps

---

### Post by Yellow Pasque on 2024-04-05
> **dook123 said:**
> it's now seemingly using the right driver, but i'm still can't get the audio device to appear, and still only see "Dummy Output" as a device.

In addition to the latest sof firmware, did you update the ucm like in [https://github.com/thesofproject/linux/issues/4879#issuecomment-2027703266](https://github.com/thesofproject/linux/issues/4879#issuecomment-2027703266)
Make sure you do that and reboot.

What does this show?:
```
aplay -l
alsaucm dump text
```

---

### Post by dook123 on 2024-04-06
OK, follow the same steps in the link, but no joy.  Seems to be same issue.

**sudo dmesg | grep -E 'sof-audio-pci-intel-mtl|snd_hda_intel|cs35l56|sof_sdw|sof-audio-pci-intel-mtl|input|cs42l43-codec'**
[    0.610766] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.610829] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.610876] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.650485] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.592331] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input5
[    2.204410] input: ELAN900C:00 04F3:4212 Touchscreen as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN900C:00/0018:04F3:4212.0001/input/input6
[    2.204513] input: ELAN900C:00 04F3:4212 as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN900C:00/0018:04F3:4212.0001/input/input7
[    2.204554] input: ELAN900C:00 04F3:4212 as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN900C:00/0018:04F3:4212.0001/input/input8
[    2.204632] hid-generic 0018:04F3:4212.0001: input,hidraw0: I2C HID v1.00 Device [ELAN900C:00 04F3:4212] on i2c-ELAN900C:00
[    2.204931] input: VEN_2C2F:00 2C2F:002B Mouse as /devices/pci0000:00/0000:00:15.2/i2c_designware.1/i2c-1/i2c-VEN_2C2F:00/0018:2C2F:002B.0002/input/input10
[    2.204997] input: VEN_2C2F:00 2C2F:002B Touchpad as /devices/pci0000:00/0000:00:15.2/i2c_designware.1/i2c-1/i2c-VEN_2C2F:00/0018:2C2F:002B.0002/input/input11
[    2.205079] hid-generic 0018:2C2F:002B.0002: input,hidraw1: I2C HID v1.00 Mouse [VEN_2C2F:00 2C2F:002B] on i2c-VEN_2C2F:00
[    2.715638] input: Intel HID events as /devices/platform/INTC1070:00/input/input13
[    2.740173] input: Intel HID 5 button array as /devices/platform/INTC1070:00/input/input14
[    2.802941] input: ELAN900C:00 04F3:4212 as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN900C:00/0018:04F3:4212.0001/input/input15
[    2.803096] input: ELAN900C:00 04F3:4212 UNKNOWN as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN900C:00/0018:04F3:4212.0001/input/input16
[    2.803147] input: ELAN900C:00 04F3:4212 UNKNOWN as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN900C:00/0018:04F3:4212.0001/input/input17
[    2.803258] hid-multitouch 0018:04F3:4212.0001: input,hidraw0: I2C HID v1.00 Device [ELAN900C:00 04F3:4212] on i2c-ELAN900C:00
[    2.804902] i2c_hid_acpi i2c-ELAN900C:00: i2c_hid_get_input: IRQ triggered but there's no data
[    2.961769] input: VEN_2C2F:00 2C2F:002B Mouse as /devices/pci0000:00/0000:00:15.2/i2c_designware.1/i2c-1/i2c-VEN_2C2F:00/0018:2C2F:002B.0002/input/input19
[    2.961911] input: VEN_2C2F:00 2C2F:002B Touchpad as /devices/pci0000:00/0000:00:15.2/i2c_designware.1/i2c-1/i2c-VEN_2C2F:00/0018:2C2F:002B.0002/input/input20
[    2.962019] hid-multitouch 0018:2C2F:002B.0002: input,hidraw1: I2C HID v1.00 Mouse [VEN_2C2F:00 2C2F:002B] on i2c-VEN_2C2F:00
[    2.963560] Modules linked in: bluetooth intel_cstate snd dell_smm_hwmon mei_me hid_sensor_iio_common dell_wmi_ddv firmware_attributes_class wmi_bmof dell_wmi_descriptor usb_ljca intel_skl_int3472_tps68470 spi_intel_pci rc_core i2c_i801 ecdh_generic processor_thermal_mbox int3403_thermal cfg80211 intel_pmc_core mei industrialio intel_vpu soundcore i2c_algo_bit spi_intel ecc tps68470_regulator i2c_smbus igen6_edac int340x_thermal_zone clk_tps68470 mei_vsc_hw intel_vsec int3400_thermal pmt_telemetry intel_hid acpi_thermal_rel pmt_class intel_skl_int3472_discrete acpi_tad acpi_pad sparse_keymap input_leds hid_multitouch serio_raw mac_hid msr parport_pc ppdev lp parport efi_pstore dmi_sysfs ip_tables x_tables autofs4 hid_sensor_custom hid_sensor_hub intel_ishtp_hid hid_generic 8250_dw rtsx_pci_sdmmc nvme ucsi_acpi crc32_pclmul psmouse video thunderbolt typec_ucsi intel_ish_ipc nvme_core intel_lpss_pci rtsx_pci intel_lpss xhci_pci intel_ishtp typec idma64 xhci_pci_renesas nvme_auth i2c_hid_acpi i2c_hid hid wmi
[    3.419982] input: Dell Privacy Driver as /devices/platform/PNP0C14:02/wmi_bus/wmi_bus-PNP0C14:02/6932965F-1671-4CEB-B988-D3AB0A901919/input/input22
[    3.425639] input: Dell WMI hotkeys as /devices/platform/PNP0C14:02/wmi_bus/wmi_bus-PNP0C14:02/9DBB5994-A997-11DA-B012-B622A1EF5492/input/input23
[    3.867170] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    3.867388] snd_hda_intel 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[    4.175565] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    4.175587] sof-audio-pci-intel-mtl 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[    4.175596] sof-audio-pci-intel-mtl 0000:00:1f.3: enabling device (0000 -> 0002)
[    4.175686] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    5.223265] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input24
[    5.223459] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    5.223462] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:69/LNXVIDEO:01/input/input25
[    5.223500] snd_hda_intel 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[    5.223512] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    5.223531] sof-audio-pci-intel-mtl 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[    5.223923] sof-audio-pci-intel-mtl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    5.229236] sof-audio-pci-intel-mtl 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.236429] sof-audio-pci-intel-mtl 0000:00:1f.3: use msi interrupt mode
[    5.256302] sof-audio-pci-intel-mtl 0000:00:1f.3: hda codecs found, mask 4
[    5.262237] sof-audio-pci-intel-mtl 0000:00:1f.3: Firmware paths/files for ipc type 1:
[    5.262244] sof-audio-pci-intel-mtl 0000:00:1f.3:  Firmware file:     intel/sof-ipc4/mtl/sof-mtl.ri
[    5.262246] sof-audio-pci-intel-mtl 0000:00:1f.3:  Firmware lib path: intel/sof-ipc4-lib/mtl
[    5.262247] sof-audio-pci-intel-mtl 0000:00:1f.3:  Topology file:     intel/sof-ace-tplg/sof-mtl-cs42l43-l0-cs35l56-l23.tplg
[    5.263156] sof-audio-pci-intel-mtl 0000:00:1f.3: Loaded firmware library: ADSPFW, version: 2.9.0.1
[    5.270101] cs35l56 sdw:0:2:01fa:3556:01:2: supply VDD_P not found, using dummy regulator
[    5.270132] cs35l56 sdw:0:2:01fa:3556:01:2: supply VDD_IO not found, using dummy regulator
[    5.270147] cs35l56 sdw:0:2:01fa:3556:01:2: supply VDD_A not found, using dummy regulator
[    5.270912] cs35l56 sdw:0:2:01fa:3556:01:2: Got spk-id from AF01
[    5.271203] cs35l56 sdw:0:2:01fa:3556:01:3: supply VDD_P not found, using dummy regulator
[    5.271246] cs35l56 sdw:0:2:01fa:3556:01:3: supply VDD_IO not found, using dummy regulator
[    5.271253] cs35l56 sdw:0:2:01fa:3556:01:3: supply VDD_A not found, using dummy regulator
[    5.272542] cs35l56 sdw:0:2:01fa:3556:01:3: Got spk-id from AF01
[    5.272706] cs35l56 sdw:0:3:01fa:3556:01:0: supply VDD_P not found, using dummy regulator
[    5.272732] cs35l56 sdw:0:3:01fa:3556:01:0: supply VDD_IO not found, using dummy regulator
[    5.272743] cs35l56 sdw:0:3:01fa:3556:01:0: supply VDD_A not found, using dummy regulator
[    5.273200] cs35l56 sdw:0:3:01fa:3556:01:0: Got spk-id from AF01
[    5.273346] cs35l56 sdw:0:3:01fa:3556:01:1: supply VDD_P not found, using dummy regulator
[    5.273361] cs35l56 sdw:0:3:01fa:3556:01:1: supply VDD_IO not found, using dummy regulator
[    5.273368] cs35l56 sdw:0:3:01fa:3556:01:1: supply VDD_A not found, using dummy regulator
[    5.273515] cs35l56 sdw:0:3:01fa:3556:01:1: Got spk-id from AF01
[    5.368403] sof-audio-pci-intel-mtl 0000:00:1f.3: Booted firmware version: 2.9.0.1
[    5.380579] cs35l56 sdw:0:2:01fa:3556:01:3: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[    5.380599] cs35l56 sdw:0:3:01fa:3556:01:1: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[    5.394354] cs35l56 sdw:0:2:01fa:3556:01:2: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[    5.394361] cs35l56 sdw:0:3:01fa:3556:01:0: Cirrus Logic CS35L56 Rev B0 OTP3 fw:3.4.4 (patched=0)
[    5.398631] cs35l56 sdw:0:3:01fa:3556:01:1: Slave 1 state check1: UNATTACHED, status was 1
[    5.399350] cs35l56 sdw:0:2:01fa:3556:01:3: Slave 1 state check1: UNATTACHED, status was 1
[    5.399354] cs35l56 sdw:0:2:01fa:3556:01:2: Slave 2 state check1: UNATTACHED, status was 1
[    5.399395] cs35l56 sdw:0:3:01fa:3556:01:0: Slave 2 state check1: UNATTACHED, status was 1
[    9.237249] rfkill: input handler disabled
[   15.450342] platform sof_sdw: deferred probe pending: sof_sdw: snd_soc_register_card failed -517
[   16.454645] rfkill: input handler enabled
[   19.147197] rfkill: input handler disabled

[B]aplay -l
[/B]aplay: device_list:277: no soundcards found...
[B]
alsaucm dump text[/B]
ALSA lib confmisc.c:165:(snd_config_get_card) Cannot get card index for -1
ALSA lib parser.c:2830:(uc_mgr_import_master_config) card 'hw:-1' is not valid
ALSA lib main.c:1560:(snd_use_case_mgr_open) error: failed to import hw:-1 use case configuration -19
alsaucm: error failed to open sound card hw:-1: No such device

---

### Post by dook123 on 2024-04-13
OK update - **Working Audio on Dell XPS 14" (9440)!**

So, Ubuntu 24.04 got released in Beta a few days ago ([https://releases.ubuntu.com/noble/](https://releases.ubuntu.com/noble/))
So...downloaded ubuntu-24.04-beta-desktop-amd64.iso to USB and installed it.  This time i actually selected to install third party drivers, and it seems happy (Working GFX card) and is showing a 4050 GTX in System Details

This version of Ubuntu comes with 6.8.0-22-generic kernel

So i installed mainline
[B]sudo add-apt-repository ppa:cappelikan/ppa
sudo apt update
sudo apt install mainline
[/B]And updated the kernel to 6.9-rc3 (latest but i suspect some earliers would work too)

Then downloaded latest available sof binaries from [https://github.com/thesofproject/sof-bin/releases](https://github.com/thesofproject/sof-bin/releases) (v2024.03)
Extracted tar and then ran install.sh as sudo (Had issues with some folder not extracting/removing properly so removed contents of /lib/firmware/intel/sof-ace-tplg first and re-ran installer again)


Then as per @Yellow Pasque comment, i "patched UCM" as per the thread in github issue ([https://github.com/thesofproject/linux/issues/4879#issuecomment-2024076848](https://github.com/thesofproject/linux/issues/4879#issuecomment-2024076848))

[B]curl -L -o alsa-ucm-conf.tar.gz [https://github.com/alsa-project/alsa-ucm-conf/archive/refs/heads/master.tar.gz](https://github.com/alsa-project/alsa-ucm-conf/archive/refs/heads/master.tar.gz)
tar xvzf alsa-ucm-conf.tar.gz -C /usr/share/alsa --strip-components=1 --wildcards "*/ucm" "*/ucm2"[/B]
Rebooted and....Working audio!


If anyone needs any further info, let me know

---

### Post by shaocheng on 2024-04-17
It is nice that you got your Ubuntu 24.04 work on XPS 14 9440! I just wonder if all the hardware worked well with the latest released Ubuntu apart from audio and graphic card. For instance, camera, touchpad (did you test if the haptic touchpad also works). Thanks!
It seems that updated kernel is major factor influencing the compatibility, right? Perhaps, this is why Pop os, which supports kernel 6.8, could work as well for someone.

---

### Post by mixer2 on 2024-05-07
@dook123 nice that you got audio working, thanks for the effort!
what's a pitty is, that it requires a mainline kernel verison. hopefully it will at some point also just work with the ubuntu 24.04 kernel.

regarding webcam it seems as also the 16" 2024 dell notebooks have the same issue: [https://github.com/intel/ipu6-drivers/issues/223](https://github.com/intel/ipu6-drivers/issues/223)

hopefully they'll fix it soon in the ipu6 drivers.

---

### Post by mixer2 on 2024-06-02
Hello,

how is, beside general hardware support your overall experience?
for me, after working for quite some time with the xps 14, it's still not completely reliable, as my old xps 13 was. it's working perfectly fine most of the time (beside webcam, of course), it's super fast and has good battery life.
however, wakeing up from standby is ~90% of the time working, but sometimes it isn't and i have to reboot. sometimes i have graphical glitches... and sometimes the system just hangs for 30-60 seconds, which is especially bad in video conferences while sharing the screen.
last problem is, that when it's connected/disconnected to/from an external display. sometimes it also crashes.
i use wayland with latest nvidia drivers (however, set it to intel mode, because i hoped that it might help with graphical glitches, which it didn't).

another problem, which is not linux related is, that usb-c connection to usb-c dell monitors causes the pc to shut down after a few seconds. this also happens on windows (and is not a hardware problem, tried it with 2 devices). other usb-c monitors work fine. it has to be some special communication between the dell products.

just wondering what the experiences of other users are :-)

---

### Post by dook123 on 2024-06-16
> **mixer2 said:**
> Hello,

how is, beside general hardware support your overall experience?
for me, after working for quite some time with the xps 14, it's still not completely reliable, as my old xps 13 was. it's working perfectly fine most of the time (beside webcam, of course), it's super fast and has good battery life.
however, wakeing up from standby is ~90% of the time working, but sometimes it isn't and i have to reboot. sometimes i have graphical glitches... and sometimes the system just hangs for 30-60 seconds, which is especially bad in video conferences while sharing the screen.
last problem is, that when it's connected/disconnected to/from an external display. sometimes it also crashes.
i use wayland with latest nvidia drivers (however, set it to intel mode, because i hoped that it might help with graphical glitches, which it didn't).

another problem, which is not linux related is, that usb-c connection to usb-c dell monitors causes the pc to shut down after a few seconds. this also happens on windows (and is not a hardware problem, tried it with 2 devices). other usb-c monitors work fine. it has to be some special communication between the dell products.

just wondering what the experiences of other users are :-)


Yeah definitely not perfect, lots of issues with wake up, and unlocking after wakeup.
I haven't had any issues with my Dell monitors and USB-C, but i have noticed that any dongle that has the 2 x USB-C ports won't fit this.   Soooo infuriating.
I loved my 2020 13" XPS, but this one just is not as good at all.  Kind regret buying it tbh, and might sell to in place of something else

---

### Post by mixer2 on 2024-06-25
> **dook123 said:**
> Yeah definitely not perfect, lots of issues with wake up, and unlocking after wakeup.
I haven't had any issues with my Dell monitors and USB-C, but i have noticed that any dongle that has the 2 x USB-C ports won't fit this.   Soooo infuriating.
I loved my 2020 13" XPS, but this one just is not as good at all.  Kind regret buying it tbh, and might sell to in place of something else

so i'm not the only one having problems.
me personally still not regretting it, because the performance is very good. when it runs it's super snappy. just has to get a little bit more stable (already stable enough for me for daily work). if they would just write and optimize the drivers upfront instead of having to wait for 6-8 month after release until the drivers get stable.
hope the ARM chips get better linux support on release dates. then my next notebook in 3 years will be ARM based.

---

### Post by hnyk94 on 2024-06-25
> **mixer2 said:**
> @dook123 nice that you got audio working, thanks for the effort!
what's a pitty is, that it requires a mainline kernel verison. hopefully it will at some point also just work with the ubuntu 24.04 kernel.

regarding webcam it seems as also the 16" 2024 dell notebooks have the same issue: [https://github.com/intel/ipu6-drivers/issues/223](https://github.com/intel/ipu6-drivers/issues/223)

hopefully they'll fix it soon in the ipu6 drivers.

Was anyone able to fix the camera issue? Does anyone have an update? :(
I was able to fix the audio/mic issue with @dook123's solution, and that helped a lot!

---

### Post by mixer2 on 2024-07-21
> **hnyk94 said:**
> Was anyone able to fix the camera issue? Does anyone have an update? :(
I was able to fix the audio/mic issue with @dook123's solution, and that helped a lot!

don't think there is much progress on camera.

however, with kernel 6.9.9, latest bios update and current ubuntu everything else seems to work much smoother than a few weeks ago.
standby is great, very reliable and quick in getting into sleep and waking up. also not draining a lot of power in standby. beside stability also battery performance overall got very good (at least with tlp).
not sure if it's bios, kernel, ubuntu updates... or maybe a combination out of it. but beside camera the notebook is slowly getting really really usable.

---

### Post by csymeonides on 2024-07-23
> **mixer2 said:**
> don't think there is much progress on camera.

however, with kernel 6.9.9, latest bios update and current ubuntu everything else seems to work much smoother than a few weeks ago.
standby is great, very reliable and quick in getting into sleep and waking up. also not draining a lot of power in standby. beside stability also battery performance overall got very good (at least with tlp).
not sure if it's bios, kernel, ubuntu updates... or maybe a combination out of it. but beside camera the notebook is slowly getting really really usable.

Sorry if this is a noob question but, how did you get the 6.9.9 kernel? Is it via mainline as [dook123 describes here]("https://ubuntuforums.org/showthread.php?t=2496410&p=14185629#post14185629")? 

I'm struggling to understand the pros and cons of installing a mainline kernel vs waiting for Ubuntu to release an update. Any advice would be super helpful! I've been very frustrated with this new Dell, but I don't want to create new problems while trying to fix the existing ones...

---

### Post by mixer2 on 2024-08-12
> **csymeonides said:**
> Sorry if this is a noob question but, how did you get the 6.9.9 kernel? Is it via mainline as [dook123 describes here]("https://ubuntuforums.org/showthread.php?t=2496410&p=14185629#post14185629")? 

I'm struggling to understand the pros and cons of installing a mainline kernel vs waiting for Ubuntu to release an update. Any advice would be super helpful! I've been very frustrated with this new Dell, but I don't want to create new problems while trying to fix the existing ones...
 
sorry for the late respone, only checking the thread from time to time.
yes just use mainline as dook described, it's super easy.

benefit is, that you get newer kernels. Ubuntu is just providing new kernels (beside bugfix and security updates) when they release a new ubuntu version. current ubuntu version is still using kernel 6.8 while there is already 6.10. on the other side, you're missing with mainline kernels the testing, ubuntu specific adaptions and stuff that is precompiled for the specific kernel ubuntu is shipped with.
usually it's the best to stick with the ubuntu kernel, but if you have very new hardware (like the 9440 still is), it's sometimes better to use latest kernel, if it's supporting your hardware better. and in 6.9 and 6.10 there are a lot of improvements for 9440s hardware.

---

### Post by concesar on 2024-09-02
As per September 3rd 2024, I am still having issues with my dell xps14 9440, I have the kernel: 6.8.0-41-generic and I am using ubuntu 24.04, I fixed the screen issue by creating a file /etc/modprobe.d/i915.conf , and adding this line: options i915 enable_psr=0, apparently the power self refresh has issues with the Nvidia card, so we disable it, it will consume just a bit more of power but as long as the flickering issue is solved is fine to me. Since this is a work pc I do need to have official kernel on. Therefore, adding a pre-released kernel is not an option to me. I guess the most annoying problem now is the sound card not being recognized, so I can't use any microphone or connect anything in the audio jack because no audio is coming out. I heard in he next release ubuntu 24.10 things might get better, does anyone has any idea if this is really like this?

---

### Post by mixer2 on 2024-09-08
> **concesar said:**
> As per September 3rd 2024, I am still having issues with my dell xps14 9440, I have the kernel: 6.8.0-41-generic and I am using ubuntu 24.04, I fixed the screen issue by creating a file /etc/modprobe.d/i915.conf , and adding this line: options i915 enable_psr=0, apparently the power self refresh has issues with the Nvidia card, so we disable it, it will consume just a bit more of power but as long as the flickering issue is solved is fine to me. Since this is a work pc I do need to have official kernel on. Therefore, adding a pre-released kernel is not an option to me. I guess the most annoying problem now is the sound card not being recognized, so I can't use any microphone or connect anything in the audio jack because no audio is coming out. I heard in he next release ubuntu 24.10 things might get better, does anyone has any idea if this is really like this?

pretty sure that it's getting better out of the box with the new ubuntu version, since they include a current kernel. mainline kernels do run quite well. only real problems left is 1. shutdown with some dell displays via usb-c (not a linux issue, same happens on windows) 2. webcam. the audio problem can be fixed with current kernels, as dook123 described in this thread (as long as you do have a current kernel, which is the case for mainline kernels or the new ubuntu version which will be released next month).

---

### Post by danrees84 on 2024-09-09
> **dook123 said:**
> OK update - **Working Audio on Dell XPS 14" (9440)!**

So, Ubuntu 24.04 got released in Beta a few days ago ([https://releases.ubuntu.com/noble/](https://releases.ubuntu.com/noble/))
So...downloaded ubuntu-24.04-beta-desktop-amd64.iso to USB and installed it.  This time i actually selected to install third party drivers, and it seems happy (Working GFX card) and is showing a 4050 GTX in System Details

This version of Ubuntu comes with 6.8.0-22-generic kernel

So i installed mainline
[B]sudo add-apt-repository ppa:cappelikan/ppa
sudo apt update
sudo apt install mainline
[/B]And updated the kernel to 6.9-rc3 (latest but i suspect some earliers would work too)

Then downloaded latest available sof binaries from [https://github.com/thesofproject/sof-bin/releases](https://github.com/thesofproject/sof-bin/releases) (v2024.03)
Extracted tar and then ran install.sh as sudo (Had issues with some folder not extracting/removing properly so removed contents of /lib/firmware/intel/sof-ace-tplg first and re-ran installer again)


Then as per @Yellow Pasque comment, i "patched UCM" as per the thread in github issue ([https://github.com/thesofproject/linux/issues/4879#issuecomment-2024076848](https://github.com/thesofproject/linux/issues/4879#issuecomment-2024076848))

[B]curl -L -o alsa-ucm-conf.tar.gz [https://github.com/alsa-project/alsa-ucm-conf/archive/refs/heads/master.tar.gz](https://github.com/alsa-project/alsa-ucm-conf/archive/refs/heads/master.tar.gz)
tar xvzf alsa-ucm-conf.tar.gz -C /usr/share/alsa --strip-components=1 --wildcards "*/ucm" "*/ucm2"[/B]
Rebooted and....Working audio!


If anyone needs any further info, let me know

I have followed these instructions on Kubuntu 24.04, running 6.10.9 via mainline. Bluetooth audio works but not the onboard speaker. I don't see a speaker device in the KDE Audio Devices settings, or via pavucontrol (only "Pro" or "Off"). Any suggestions welcome! First Nvidia laptop so haven't even got to trying to sync up Nvidia drivers onto a mainline kernel yet...

---

### Post by odnaratsuj on 2024-09-11
Thanks @dook123, for the solution to fix the internal audio on the Dell XPS 14! I can confirm that the solution worked for me. However, my headphone audio and mic aren't working through the audio jack, so I&#8217;m curious&#8212;has the solution fixed the headphone issue for anyone else?

---

### Post by danrees84 on 2024-09-27
For what it's worth, I just tried the live environment of the Fedora 41 beta, and the speaker was working fine out of the box. Didn't seem to in the Ubuntu 24.10 beta but hopefully this will settle down and get sorted with sane defaults in the final 24.10 version. It is reassuring at least it works on some version of Linux already...

---

### Post by mixer2 on 2024-09-30
did you try if the webcam works in fedora 41 beta? but i guess it's not working,,,

---

### Post by martinpenkov on 2024-10-05
With the latest changes of 24.10 only the camera is not working.

Great thread! Just what I was looking for! I initially tried to install Kali linux on my Dell XPS - but there were problems with the wifi, camera, audio & microphone. I tried Ubuntu 24.01.1 and the wifi was OK but the sound, microphone and camera are still not working. With the latest update only the camera is not working!

---

### Post by Yellow Pasque on 2024-10-05
> **mixer2 said:**
> did you try if the webcam works in fedora 41 beta? but i guess it's not working,,,

Probably not, since F41 apparently still has issues with cameras on the "Meteor Lake" CPU's
[https://hansdegoede.dreamwidth.org/28841.html](https://hansdegoede.dreamwidth.org/28841.html)

---

### Post by danrees84 on 2024-10-11
> **martinpenkov said:**
> With the latest changes of 24.10 only the camera is not working.

Great thread! Just what I was looking for! I initially tried to install Kali linux on my Dell XPS - but there were problems with the wifi, camera, audio & microphone. I tried Ubuntu 24.01.1 and the wifi was OK but the sound, microphone and camera are still not working. With the latest update only the camera is not working!

Confirmed that sound via speaker is now working on default Kubuntu 24.10 installation with no additional action required.

I am not a webcam user on this laptop so have not tried that other than try following basic instructions on ArchWiki but didn't get it to work:

[https://wiki.archlinux.org/title/Webcam_setup](https://wiki.archlinux.org/title/Webcam_setup)

---

### Post by zoomy942 on 2024-10-11
This is a perfect thread for me as well.  

I have a Dell 7320 detachable.  With ubuntu 24.04.01, everything outside of the webcam worked fine.  I saw in the news that the new kernel in 24.10 would incluide webcam support for devices like mine.  I upgraded (and clean installed) 24.10 and the webcam still doesn't work.  It's recognized for sure, which is progress, but still not working.  Looking over this thread, is my 11th gen CPU still in the will-work-eventually part of this?  

I did try Fedora 41 and it acted the same.

---

### Post by concesar on 2024-10-16
For those claiming that the latest Kernel resolves the audio issues, that&#8217;s only partially true. On my Dell XPS 14 running Ubuntu 24.10 with Kernel 6.11.0-8-generic, Bluetooth headphones and external speakers are recognized, but when connecting a 3.5mm jack or using the built-in speakers and microphone, they still don&#8217;t show up. The camera also remains non-functional. While the Wi-Fi works, connectivity with Wi-Fi 6 routers is still inconsistent. I have a dual boot with Windows 11, where everything works flawlessly, but on Ubuntu, it seems like these issues may never be fully resolved, unfortunately.

---

### Post by zoomy942 on 2024-10-17
I understand what you mean.  I have everyhting working in my 7320 except the webcam.  I still have hope but not sure where to get help.

---

### Post by titix2 on 2024-10-23
Hello here,

Bought my XPS 9440 a few months ago and made most of it working with instructions from this thread so i'd like to give a little feedback.
(TLDR : everything's working apart hibernation).

I'm running Ubuntu 24.04 LTS, and here are the steps i went through :

- Audio : Follow Dook123 instructions here [https://ubuntuforums.org/showthread.php?t=2496410&page=2&p=14185629#post14185629](https://ubuntuforums.org/showthread.php?t=2496410&page=2&p=14185629#post14185629)
and you'll have a fully functionnal audio system.

I had to install alsamixer (cli tool) to raise volume on the 4 built-in speakers.
Audio working with 3.5mm Jack 

- Bluetooth / wifi : it was never an issue (with non-free drivers)

- Video / GPU : I'm  working with  multiple screens on a single USB-C video adapter (intel integrated GPU)
Dedicated GPU (nvidia) can be activated on demand. (seems to be the default configuration)

- Suspend / HIbernation : 
Updated laptop firmware to 1.6 (read reports it will improve power consumption)
Nerver succeeded with hibernation but suspend works like a charm even with an encrypted partition.

- Webcam : It was the trickiest part
People succeed with the same webcam model on different hardware with Ubuntu 24.04 and kernel 6.8.0-45 from Ubuntu :
[https://github.com/intel/ipu6-drivers/issues/228](https://github.com/intel/ipu6-drivers/issues/228)
(you'll need to add an extra ppa, install libcamhal0, v4l2loopback etc ...)

But we need at least kernel >= 6.9 for audio, so i rebuilt kernel 6.11.0 from Ubuntu 24.10 (hoping they kept all their magical patches) ... and now my camera is working in Chrome, Firefox, Cheese ...
(I didn't checked with a fresh  Ubuntu 24.10 (with v4l2loopback, libcamhal0) )

It's been almost 3 weeks and i don't see any other issue with this laptop !

---

### Post by chiappone on 2024-10-24
Has anyone tried Ubuntu 24.10 on the XPS 9440 or 9640 yet?

---

### Post by Wapnet on 2024-10-25
Yes I did install a fresh install of 24.10 last night. Everything works out of the box except the webcam :(

I tried a lot of different things but the camera is still broken.

I red somewhere in this topic that Fedora 41 was working. So I will try a couple of hours to get the camera working but if this fails I try Fedora.

Ps I have a Dell XPS 14 9440

---

### Post by zoomy942 on 2024-10-25
Morning!  Same for me - all but webcam. When you try Fedora, can you update us?  I’m intensely curious.

---

### Post by Wapnet on 2024-10-26
I try Fedora 41 beta today but unfortunately without succes :( As you can see in the code the camera is detected (without any manual software installation) but it isnt working. I think its good to follow this page: [https://hansdegoede.dreamwidth.org/28841.html](https://hansdegoede.dreamwidth.org/28841.html)

```

sudo dmesg | grep -i ipu
[    0.010841] ACPI: SSDT 0x0000000051FE7000 0000F9 (v02 INTEL  IpuSsdt  00001000 INTL 20210930)
[    6.244968] intel-ipu6 0000:00:05.0: enabling device (0000 -> 0002)
[    6.245185] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.287411] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.290308] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.320510] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.377687] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.421642] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.449102] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.478573] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.560244] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.596221] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.670146] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.698625] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.699746] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.731935] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.733205] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.766697] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.767779] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.797584] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.861010] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.889994] intel-ipu6 0000:00:05.0: FW version: 20230925
[    6.899764] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    6.931381] intel-ipu6 0000:00:05.0: FW version: 20230925
[    7.027778] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    7.059010] intel-ipu6 0000:00:05.0: FW version: 20230925
[    7.845771] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    7.884458] intel-ipu6 0000:00:05.0: FW version: 20230925
[    9.037667] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[    9.098521] intel-ipu6 0000:00:05.0: FW version: 20230925
[   15.810121] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[   15.864411] intel-ipu6 0000:00:05.0: FW version: 20230925
[   15.868259] intel-ipu6 0000:00:05.0: IPU6 in secure mode touch 0x80000000 mask 0x0
[   15.907429] intel-ipu6 0000:00:05.0: FW version: 20230925
[   15.923614] intel-ipu6 0000:00:05.0: Found supported sensor OVTI02C1:00
[   15.923794] intel-ipu6 0000:00:05.0: Connected 1 cameras
[   15.926775] intel-ipu6 0000:00:05.0: Sending BOOT_LOAD to CSE
[   15.998940] intel-ipu6 0000:00:05.0: Sending AUTHENTICATE_RUN to CSE
[   16.082010] intel-ipu6 0000:00:05.0: CSE authenticate_run done
[   16.082021] intel-ipu6 0000:00:05.0: IPU6-v4[7d19] hardware version 6
[   44.025212]  snd_soc_core nvidia_uvm(PO) binfmt_misc snd_compress intel_ipu6_isys ac97_bus snd_usb_audio snd_pcm_dmaengine snd_hda_intel videobuf2_dma_contig libarc4 snd_intel_dspcfg videobuf2_memops snd_intel_sdw_acpi intel_uncore_frequency videobuf2_v4l2 intel_uncore_frequency_common snd_hda_codec videobuf2_common snd_usbmidi_lib x86_pkg_temp_thermal ivsc_csi snd_ump intel_powerclamp snd_hda_core v4l2_fwnode cdc_mbim snd_rawmidi cdc_wdm v4l2_async snd_hwdep coretemp snd_seq dell_pc videodev snd_seq_device snd_ctl_led platform_profile typec_displayport mc snd_pcm ivsc_ace spi_nor btusb dell_laptop btrtl cdc_ncm iwlwifi iTCO_wdt kvm_intel mtd cdc_ether btintel dell_wmi snd_timer intel_pmc_bxt usbnet iTCO_vendor_support mei_gsc_proxy hid_sensor_als dell_smbios btbcm vfat nvidia(PO) mei_vsc kvm spi_ljca gpio_ljca i2c_ljca intel_rapl_msr fat dcdbas rapl intel_cstate intel_uncore dell_smm_hwmon dell_wmi_descriptor pcspkr dell_wmi_ddv dell_wmi_sysman firmware_attributes_class mei_me wmi_bmof i2c_i801 spi_intel_pci btmtk
[   44.025272]  hid_sensor_trigger snd mii cfg80211 spi_intel i2c_smbus hid_sensor_iio_common mei bluetooth soundcore industrialio_triggered_buffer usb_ljca kfifo_buf industrialio idma64 processor_thermal_device_pci processor_thermal_device rfkill processor_thermal_wt_hint processor_thermal_rfim processor_thermal_rapl intel_rapl_common processor_thermal_wt_req thunderbolt processor_thermal_power_floor intel_ipu6 processor_thermal_mbox ipu_bridge igen6_edac intel_skl_int3472_tps68470 tps68470_regulator clk_tps68470 intel_pmc_core int3403_thermal int340x_thermal_zone intel_vsec acpi_tad pmt_telemetry joydev int3400_thermal mei_vsc_hw intel_hid pmt_class acpi_thermal_rel acpi_pad intel_skl_int3472_discrete sparse_keymap loop nfnetlink zram xe drm_ttm_helper gpu_sched drm_suballoc_helper drm_gpuvm drm_exec hid_sensor_hub intel_ishtp_hid i915 nvme nvme_core nvme_auth crct10dif_pclmul i2c_algo_bit crc32_pclmul drm_buddy crc32c_intel rtsx_pci_sdmmc polyval_clmulni ttm polyval_generic mmc_core drm_display_helper
[   44.028053]  snd_soc_core nvidia_uvm(PO) binfmt_misc snd_compress intel_ipu6_isys ac97_bus snd_usb_audio snd_pcm_dmaengine snd_hda_intel videobuf2_dma_contig libarc4 snd_intel_dspcfg videobuf2_memops snd_intel_sdw_acpi intel_uncore_frequency videobuf2_v4l2 intel_uncore_frequency_common snd_hda_codec videobuf2_common snd_usbmidi_lib x86_pkg_temp_thermal ivsc_csi snd_ump intel_powerclamp snd_hda_core v4l2_fwnode cdc_mbim snd_rawmidi cdc_wdm v4l2_async snd_hwdep coretemp snd_seq dell_pc videodev snd_seq_device snd_ctl_led platform_profile typec_displayport mc snd_pcm ivsc_ace spi_nor btusb dell_laptop btrtl cdc_ncm iwlwifi iTCO_wdt kvm_intel mtd cdc_ether btintel dell_wmi snd_timer intel_pmc_bxt usbnet iTCO_vendor_support mei_gsc_proxy hid_sensor_als dell_smbios btbcm vfat nvidia(PO) mei_vsc kvm spi_ljca gpio_ljca i2c_ljca intel_rapl_msr fat dcdbas rapl intel_cstate intel_uncore dell_smm_hwmon dell_wmi_descriptor pcspkr dell_wmi_ddv dell_wmi_sysman firmware_attributes_class mei_me wmi_bmof i2c_i801 spi_intel_pci btmtk
[   44.028107]  hid_sensor_trigger snd mii cfg80211 spi_intel i2c_smbus hid_sensor_iio_common mei bluetooth soundcore industrialio_triggered_buffer usb_ljca kfifo_buf industrialio idma64 processor_thermal_device_pci processor_thermal_device rfkill processor_thermal_wt_hint processor_thermal_rfim processor_thermal_rapl intel_rapl_common processor_thermal_wt_req thunderbolt processor_thermal_power_floor intel_ipu6 processor_thermal_mbox ipu_bridge igen6_edac intel_skl_int3472_tps68470 tps68470_regulator clk_tps68470 intel_pmc_core int3403_thermal int340x_thermal_zone intel_vsec acpi_tad pmt_telemetry joydev int3400_thermal mei_vsc_hw intel_hid pmt_class acpi_thermal_rel acpi_pad intel_skl_int3472_discrete sparse_keymap loop nfnetlink zram xe drm_ttm_helper gpu_sched drm_suballoc_helper drm_gpuvm drm_exec hid_sensor_hub intel_ishtp_hid i915 nvme nvme_core nvme_auth crct10dif_pclmul i2c_algo_bit crc32_pclmul drm_buddy crc32c_intel rtsx_pci_sdmmc polyval_clmulni ttm polyval_generic mmc_core drm_display_helper
[   44.030743]  snd_soc_core nvidia_uvm(PO) binfmt_misc snd_compress intel_ipu6_isys ac97_bus snd_usb_audio snd_pcm_dmaengine snd_hda_intel videobuf2_dma_contig libarc4 snd_intel_dspcfg videobuf2_memops snd_intel_sdw_acpi intel_uncore_frequency videobuf2_v4l2 intel_uncore_frequency_common snd_hda_codec videobuf2_common snd_usbmidi_lib x86_pkg_temp_thermal ivsc_csi snd_ump intel_powerclamp snd_hda_core v4l2_fwnode cdc_mbim snd_rawmidi cdc_wdm v4l2_async snd_hwdep coretemp snd_seq dell_pc videodev snd_seq_device snd_ctl_led platform_profile typec_displayport mc snd_pcm ivsc_ace spi_nor btusb dell_laptop btrtl cdc_ncm iwlwifi iTCO_wdt kvm_intel mtd cdc_ether btintel dell_wmi snd_timer intel_pmc_bxt usbnet iTCO_vendor_support mei_gsc_proxy hid_sensor_als dell_smbios btbcm vfat nvidia(PO) mei_vsc kvm spi_ljca gpio_ljca i2c_ljca intel_rapl_msr fat dcdbas rapl intel_cstate intel_uncore dell_smm_hwmon dell_wmi_descriptor pcspkr dell_wmi_ddv dell_wmi_sysman firmware_attributes_class mei_me wmi_bmof i2c_i801 spi_intel_pci btmtk
[   44.030814]  hid_sensor_trigger snd mii cfg80211 spi_intel i2c_smbus hid_sensor_iio_common mei bluetooth soundcore industrialio_triggered_buffer usb_ljca kfifo_buf industrialio idma64 processor_thermal_device_pci processor_thermal_device rfkill processor_thermal_wt_hint processor_thermal_rfim processor_thermal_rapl intel_rapl_common processor_thermal_wt_req thunderbolt processor_thermal_power_floor intel_ipu6 processor_thermal_mbox ipu_bridge igen6_edac intel_skl_int3472_tps68470 tps68470_regulator clk_tps68470 intel_pmc_core int3403_thermal int340x_thermal_zone intel_vsec acpi_tad pmt_telemetry joydev int3400_thermal mei_vsc_hw intel_hid pmt_class acpi_thermal_rel acpi_pad intel_skl_int3472_discrete sparse_keymap loop nfnetlink zram xe drm_ttm_helper gpu_sched drm_suballoc_helper drm_gpuvm drm_exec hid_sensor_hub intel_ishtp_hid i915 nvme nvme_core nvme_auth crct10dif_pclmul i2c_algo_bit crc32_pclmul drm_buddy crc32c_intel rtsx_pci_sdmmc polyval_clmulni ttm polyval_generic mmc_core drm_display_helper

```

Offtopic pro-tip: if you use fedora 41 with Nvidia on the XPS 14. Add "GSK_RENDERER = NGL" to /etc/environment otherwise you can't start any gnome apps anymore.

---

### Post by zoomy942 on 2024-10-26
Thank you for sharing that.  From the looks of it, there is progress but it's not quite working.  

Progress is more than zero!

---

### Post by chiappone on 2024-10-28
I'm sure it will be worked out in the near future. Does anyone have a good pointer to how to set up dual boot on the XPS?  Thanks.

---

### Post by concesar on 2024-10-28
Unfortunately, this setup isn&#8217;t working for me. I suspect it may be due to the drive encryption, or perhaps some other random issue. I&#8217;ve tried several kernel versions, from 6.8 to 6.11, but nothing has resolved the issues with the microphone, video, and sound on my XPS 14 running Ubuntu. Strangely, everything works fine in Windows, but Ubuntu has been nothing but trouble on this device.

I wouldn&#8217;t recommend this laptop for anyone looking to use it for serious work on Linux, it&#8217;s been a huge time sink. Maybe with more effort, I&#8217;ll find a solution, but at this point, it&#8217;s becoming too much to manage.

---

### Post by chiappone on 2024-10-28
This is discouraging, ordered my xps 16 and hoping to dual boot with linux.

---

### Post by winsvega2 on 2024-10-29
I use xps16 with ubuntu24.04/6.8.0-latest
6.8.0 gpu works/no sound (4 W/h idle power consumption!)
6.9.x fixes the sound, but no gpu (20 W/h idle power consumption, maybe because no gpu?)
6.10/11 break stuff. 24.10 I didn't try.

Camera I don't need. Dual boot works with windows no problem.

So for coding it is really cool with 22 cores.
Although one downside is that thread sanitizer is buggy on ubuntu.

To watch a movie or use camera though has to reboot. 

Does anyone know how to build nvidia drivers for 6.9.x kernel?

---

### Post by chiappone on 2024-10-29
Did you have to do anything special to dual boot?

---

### Post by Yellow Pasque on 2024-10-29
> **winsvega2 said:**
> I use xps16 with ubuntu24.04/6.8.0-latest
Does anyone know how to build nvidia drivers for 6.9.x kernel?

What Nvidia driver series are you using? 550.x?
Maybe 550.127.05 works with newer kernels: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=noble](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=noble)

---

### Post by winsvega2 on 2024-11-01
The image comes with 535.104.05

---

### Post by winsvega2 on 2024-11-01
> **chiappone said:**
> Did you have to do anything special to dual boot?

Make sure all windows bitlocker system encryption is switched off or it will lock your system.

---

### Post by zoomy942 on 2024-11-04
I made a bug report here - 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2085738](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2085738)

---

### Post by nm-old-timer on 2024-11-05
@danrees84
I didn't get audio on the Kubuntu 24.10 on my XPS 14 9440.  Are you sure you did noting special?

---

### Post by jsilberb-stryker on 2024-11-08
I have a Dell XPS 16 9640 running Ubuntu 24.04.1 LTS. Hardware support is workable for me (I'm using an external webcam and a usb audio interface) but my main problem is that occasionally (randomly, multiple times a day) the whole system freezes, does not respond to keyboard and I can no longer ssh into it. When this happens I need to force shutdown using the power button and reboot. I tried lots of things (different kernels, nvidia driver versions, turning of hardware acceleration when using chrome, ...) but so far couldn't fix the issue. Has anyone experienced similar issues with recent XPS models?

---

### Post by hnyk94 on 2024-11-26
> **titix2 said:**
> Hello here,

Bought my XPS 9440 a few months ago and made most of it working with instructions from this thread so i'd like to give a little feedback.
(TLDR : everything's working apart hibernation).

I'm running Ubuntu 24.04 LTS, and here are the steps i went through :

- Audio : Follow Dook123 instructions here [https://ubuntuforums.org/showthread.php?t=2496410&page=2&p=14185629#post14185629](https://ubuntuforums.org/showthread.php?t=2496410&page=2&p=14185629#post14185629)
and you'll have a fully functionnal audio system.

I had to install alsamixer (cli tool) to raise volume on the 4 built-in speakers.
Audio working with 3.5mm Jack 

- Bluetooth / wifi : it was never an issue (with non-free drivers)

- Video / GPU : I'm  working with  multiple screens on a single USB-C video adapter (intel integrated GPU)
Dedicated GPU (nvidia) can be activated on demand. (seems to be the default configuration)

- Suspend / HIbernation : 
Updated laptop firmware to 1.6 (read reports it will improve power consumption)
Nerver succeeded with hibernation but suspend works like a charm even with an encrypted partition.

- Webcam : It was the trickiest part
People succeed with the same webcam model on different hardware with Ubuntu 24.04 and kernel 6.8.0-45 from Ubuntu :
[https://github.com/intel/ipu6-drivers/issues/228](https://github.com/intel/ipu6-drivers/issues/228)
(you'll need to add an extra ppa, install libcamhal0, v4l2loopback etc ...)

But we need at least kernel >= 6.9 for audio, so i rebuilt kernel 6.11.0 from Ubuntu 24.10 (hoping they kept all their magical patches) ... and now my camera is working in Chrome, Firefox, Cheese ...
(I didn't checked with a fresh  Ubuntu 24.10 (with v4l2loopback, libcamhal0) )

It's been almost 3 weeks and i don't see any other issue with this laptop !

This finally worked for me. I tried @dook123's comment for fixing the audio a while ago, but I still had issues with the camera. I followed the instructions you shared (the GitHub issue) but couldn't resolve it since I was on Ubuntu 24.04 with kernel 6.9.9-generic. I upgraded Ubuntu to 24.10, which allowed me to use kernel 6.11.0-9-generic. Then, I followed the instructions and installed linux-modules-ipu6-6.11.0-9-generic and linux-modules-extra-6.11.0-9-generic for this kernel version. I followed all the mentioned steps here, and it fixed the issue: [https://dshedd.com/2023/07/18/fixing-lenovos-mipi-camera-problems-on-ubuntu-22-04/](https://dshedd.com/2023/07/18/fixing-lenovos-mipi-camera-problems-on-ubuntu-22-04/)

This didn't fix the issue in Cheese, but I don't mind as long as it works on Teams and Zoom, which it does now.

---

