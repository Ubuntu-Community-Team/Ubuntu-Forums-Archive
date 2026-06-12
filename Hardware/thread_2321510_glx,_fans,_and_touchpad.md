---
title: "glx, fans, and touchpad"
date: 2016-04-22
forum: Hardware
---

### Post by yazdzik-k on 2016-04-22
Dear Friends,

Asus ux 501  VW-DS71T  uhd screen,  pcie ssd,  intel wl.

Good news,  gnome looks normal on uhd,  although I dearly would love HiDPI in mate.....
install,  after a dozen tries,  is persistent after reboot if I install absolutely nothing.


Linux deblap2 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Having believed myself relatively sane, today's adventure may prove otherwise. 

```

00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H LPSS I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-H LPSS I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
02:00.0 Unassigned class [ff00]: Alcor Micro Device 6621
03:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
3d:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller (rev 01)

```

```


Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
rfcomm                 69632  2
bnep                   20480  2
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    81920  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
arc4                   16384  2
i2c_designware_platform    16384  0
joydev                 20480  0
asus_nb_wmi            24576  0
i2c_designware_core    20480  1 i2c_designware_platform
snd_hda_intel          36864  6
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
snd_hwdep              16384  1 snd_hda_codec
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
kvm                   536576  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
crc32_pclmul           16384  0
nls_iso8859_1          16384  1
uvcvideo               90112  0
aesni_intel           167936  2
iwlmvm                311296  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
mac80211              737280  1 iwlmvm
snd_rawmidi            32768  1 snd_seq_midi
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
videobuf2_vmalloc      16384  1 uvcvideo
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_timer              32768  2 snd_pcm,snd_seq
videobuf2_v4l2         28672  1 uvcvideo
input_leds             16384  0
serio_raw              16384  0
iwlwifi               200704  1 iwlmvm
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
snd                    81920  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
soundcore              16384  1 snd
media                  24576  2 uvcvideo,videodev
hid_multitouch         20480  0
idma64                 20480  0
btusb                  45056  0
mei_me                 36864  0
virt_dma               16384  1 idma64
btrtl                  16384  1 btusb
intel_lpss_pci         16384  0
mei                    98304  1 mei_me
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
shpchp                 36864  0
hci_uart               77824  0
elan_i2c               36864  0
btbcm                  16384  2 btusb,hci_uart
btqca                  16384  1 hci_uart
int3403_thermal        16384  0
btintel                16384  2 btusb,hci_uart
bluetooth             520192  31 bnep,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
tpm_crb                16384  0
int3402_thermal        16384  0
int3400_thermal        16384  0
mac_hid                16384  0
int340x_thermal_zone    16384  3 int3402_thermal,processor_thermal_device,int3403_thermal
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad               20480  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
usbhid                 49152  0
i915_bpo             1261568  8
nouveau              1495040  1
mxm_wmi                16384  1 nouveau
intel_ips              20480  1 i915_bpo
ttm                    98304  1 nouveau
i2c_algo_bit           16384  2 i915_bpo,nouveau
drm_kms_helper        139264  2 i915_bpo,nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
nvme                   65536  4
ahci                   36864  0
drm                   360448  12 ttm,i915_bpo,drm_kms_helper,nouveau
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_multitouch,usbhid
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
pinctrl_sunrisepoint    28672  0
video                  40960  3 i915_bpo,nouveau,asus_wmi
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0

```


Issues:

nothing I can do makes nvidia drivers work.  the gui  from hardware settings,  or the binary install from synaptic both lead to blank screen at reboot.... 
even using nvidia-xconfig is useless,  and I have done many cli installs of the driver in Debian.  something is amiss.

touchpad works -  but were there a 4.5 kernel available,  I believe support to be better,  as there must be a better input driver

fan situation is dreadful,  as installing lm-sensors also leads to freeze at login screen.  

(yes,  I have tested these things one by one)

Thus,  
I need foolproof(since Google and fora have been useless, mostly due to distro released today,  and hardware not much older),

install and load nvidia
(do we still need to blacklist nouveau?,  if so where,  as I am new to ubuntu) 
and the idea of intel igpu driving a uhd screen is humourous at best.  the nouveau is surely passable,  but once one must actually work on videos,  et al,  it will be a problem.  
(college kids actually submit 4k videos for classwork......aaargh)


is there a way to install 4.5 kernel(I can compile,  but there is a 4.5 in sid)

finally,  and most urgent,  since it makes the system unusable,  how to stop the perpetual fan

since lm-sensors caused disaster,  I am skeptical of fancontrol,  and have somewhat lost joy in reinstalling,  as fast as it is on this machine.  
    
for anyone reading this,  who is having issues with persistence,  the usb boot does not require cms to be enabled,  and, indeed,  that creates a plethora of other issues. 

all in all,  an heroic effort on the part of the devs who created a plug and play distro for uhd screens,  and,  had there been a tonne of documentation on this,  the install would be easy.

finally,  where do we put boot parameters nowadays in ubuntu,  as I think the parameter "1915.enable_execlists=0"  might help.
also,  since coretemp usually stops the fan issue,  how can I install lm-sensors,  and add the coretemp to the modulesload without killing the boot?

lastly,  although I am aware of the dilemma between packaging and call necessity,  the reality is that Skype, like the cellular phone,  is part of life,  and has i386 deps.  attacking microsoft politically does not get work done when someone says,  "Skype me when you get there",    this,  and adobe reader,  the former more importantly,  are needed if we deal with lots of different types of places,  just as the three of four browsers where some sites work better than others, irrespective of standards, in sundry browsers.  

once the hw stuff is dead clear,  amassing the necessary, and sometimes just covenient packages should be a cakewalk.

With gratitude and best wishes,

Martin

---

