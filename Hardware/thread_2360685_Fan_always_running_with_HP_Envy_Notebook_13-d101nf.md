---
title: "Fan always running with HP Envy Notebook 13-d101nf"
date: 2017-05-07
forum: Hardware
---

### Post by thibaud-ecarot on 2017-05-07
Hello,,

I am trying since 2 weeks to solve a problem with my new computer HP Envy Notebook 13-d101nf. I have Ubuntu installed 16.04:
```
$ uname -r
4.7.10-040710-generic
$ lsb_release -d
Description:    Ubuntu 16.04.2 LTS
```

The problem is the CPU fan is always running... And I don't find a solution. My computer is not hot and my CPU is never used more of 10% when I perform test. I have tried to install Intel microcode but it's worse. Do you have any ideas to solve the problem of my fan ?

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +29.8°C  (crit = +119.0°C)
temp3:        +10.0°C  


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +38.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:         +37.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:         +39.0°C  (high = +100.0°C, crit = +100.0°C)


pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +37.5°C  

``````


$ sudo pwmconfig
# pwmconfig revision 6243 (2014-03-20)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.


We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.


/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


```


```
$ sudo sensors-detect
# sensors-detect revision 6284 (2015-05-31 14:00:33 +0200)
# System: HP HP ENVY Notebook [Type1ProductConfigId] (laptop)
# Board: HP 80DF
# Kernel: 4.7.10-040710-generic x86_64
# Processor: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz (6/78/3)


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y       
Found unknown SMBus adapter 8086:9d23 at 0000:00:1f.4.
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.


Next adapter: i915 gmbus dpc (i2c-0)
Do you want to scan it? (yes/NO/selectively): y
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Maxim MAX6642'...                              No
Probing for `Texas Instruments TMP435'...                   No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `SMSC EMC1023'...                               No
Probing for `SMSC EMC1043'...                               No
Probing for `SMSC EMC1053'...                               No
Probing for `SMSC EMC1063'...                               No


Next adapter: i915 gmbus dpb (i2c-1)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: i915 gmbus dpd (i2c-2)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: DPDDC-A (i2c-3)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Synopsys DesignWare I2C adapter (i2c-4)
Do you want to scan it? (YES/no/selectively): y
Adapter doesn't support all probing functions.
Some addresses won't be probed.


Next adapter: Synopsys DesignWare I2C adapter (i2c-5)
Do you want to scan it? (YES/no/selectively): y
Adapter doesn't support all probing functions.
Some addresses won't be probed.

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 


Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)


To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!



```


```
$ sudo fancontrol
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file

```

```

$ lsmod
Module                  Size  Used by
ctr                    16384  3
ccm                    20480  3
rfcomm                 69632  12
fuse                   98304  2
bnep                   20480  2
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  36864  2 uvcvideo,videodev
btusb                  45056  0
btrtl                  16384  1 btusb
nls_utf8               16384  1
nls_cp437              20480  1
vfat                   20480  1
fat                    69632  1 vfat
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
kvm                   577536  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
snd_hda_codec_hdmi     45056  1
ghash_clmulni_intel    16384  0
snd_hda_codec_realtek    86016  1
snd_soc_skl            57344  0
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_soc_skl_ipc        40960  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_match      16384  1 snd_soc_skl
hmac                   16384  1
snd_soc_core          208896  1 snd_soc_skl
arc4                   16384  2
snd_compress           20480  1 snd_soc_core
dw_dmac_core           24576  1 snd_soc_sst_dsp
snd_hda_intel          36864  5
rtl8723be              90112  0
snd_hda_codec         131072  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
efi_pstore             16384  0
rtl_pci                28672  1 rtl8723be
drbg                   24576  1
rtlwifi                77824  2 rtl_pci,rtl8723be
snd_hda_core           81920  7 snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
ansi_cprng             16384  0
mac80211              643072  3 rtl_pci,rtlwifi,rtl8723be
snd_hwdep              16384  1 snd_hda_codec
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
snd_pcm               110592  8 snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_hda_core
snd_seq_midi           16384  0
rtsx_pci_ms            20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
cfg80211              573440  2 mac80211,rtlwifi
memstick               20480  1 rtsx_pci_ms
aesni_intel           167936  6
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
glue_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_pcm,snd_seq
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
intel_cstate           16384  0
snd                    81920  22 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
intel_rapl_perf        16384  0
joydev                 20480  0
efivars                20480  1 efi_pstore
soundcore              16384  1 snd
serio_raw              16384  0
hci_uart               77824  0
btbcm                  16384  2 btusb,hci_uart
btqca                  16384  1 hci_uart
idma64                 20480  0
shpchp                 36864  0
virt_dma               16384  1 idma64
btintel                16384  2 btusb,hci_uart
mei_me                 32768  0
sg                     32768  0
processor_thermal_device    16384  0
mei                    94208  1 mei_me
bluetooth             516096  41 bnep,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
intel_pch_thermal      16384  0
int340x_thermal_zone    16384  1 processor_thermal_device
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_lpss_pci         16384  0
ucsi                   16384  0
battery                16384  0
rfkill                 24576  6 cfg80211,hp_wmi,bluetooth
ac                     16384  0
int3400_thermal        16384  0
intel_lpss_acpi        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
evdev                  24576  32
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
hp_wireless            16384  0
input_polldev          16384  1 lis3lv02d
acpi_pad               24576  0
tpm_crb                16384  0
tpm_tis                20480  0
tpm                    45056  2 tpm_crb,tpm_tis
coretemp               16384  0
parport_pc             28672  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
efivarfs               16384  1
autofs4                40960  2
ext4                  593920  1
crc16                  16384  2 ext4,bluetooth
jbd2                  110592  1 ext4
mbcache                16384  2 ext4
sd_mod                 45056  4
hid_generic            16384  0
usbhid                 49152  0
rtsx_pci_sdmmc         24576  0
mmc_core              135168  1 rtsx_pci_sdmmc
crc32c_intel           24576  0
i915                 1290240  6
psmouse               126976  0
ahci                   36864  3
libahci                32768  1 ahci
libata                245760  2 ahci,libahci
xhci_pci               16384  0
xhci_hcd              172032  1 xhci_pci
i2c_algo_bit           16384  1 i915
scsi_mod              225280  3 sg,libata,sd_mod
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
drm_kms_helper        147456  1 i915
usbcore               241664  5 btusb,uvcvideo,usbhid,xhci_hcd,xhci_pci
mfd_core               16384  2 rtsx_pci,intel_lpss
drm                   364544  7 i915,drm_kms_helper
usb_common             16384  1 usbcore
fan                    16384  0
thermal                20480  0
i2c_hid                20480  0
wmi                    16384  1 hp_wmi
hid                   118784  3 i2c_hid,hid_generic,usbhid
video                  40960  1 i915
fjes                   28672  0
button                 16384  1 i915

```

I hope you can help me. Because I don't have another idea.

Thanks

---

### Post by cmcanulty on 2017-05-07
I have the same issue with a HP g72t Pavillion 17" laptop.

---

### Post by vilwarin on 2017-06-02
same problem here. 
tries all ideas and solutions I could find online.

Anybody with some experience with fan control?

---

