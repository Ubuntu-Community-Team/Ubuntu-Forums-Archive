---
title: "Running dedicated graphics card"
date: 2017-11-16
forum: Hardware
---

### Post by jane1960 on 2017-11-16
Hi All,
This seems like a great place for a newbie to ask a question :-)

I've installed Ubuntu for doing some data processing, and I've put it a nice GeForce Graphics card to use for data processing :p 

As I'm not going to be doing much gaming at the moment, I would like Ubuntu to be running all display graphics with the internal graphics on my motherboard, and to be using the resources of the dedicated graphics card for the data processing. I do currently have my monitor connected to the motherboard graphics output. However I notice that when looking at the NVIDIA logging application (nvidia-smi) that one of the processes running on my GeForce card is "**/usr/lib/xorg/Xorg"**. 
I think that this is the application that runs all the graphics for the computer. Does this mean that my motherboard is deferring all graphics to the card?

Should I boot into the linux terminal, remove it, and somehow reinstall it to run on my motherboard?

Thank you 
Best wishes all
J

---

### Post by slickymaster on 2017-11-16
Thread moved to **Hardware** for a better fit

---

### Post by uragno on 2017-11-16
Please embed (using CODE button "#")  the outputs of these commands (from CLI):
```
sudo lspci -vv

sudo lsmod

sudo ls -la /usr/share/X11/xorg.conf.d/

```

Bye!

---

### Post by Autodave on 2017-11-16
Generally, if you add a graphics card (PCI-E type) to your computer, the on-board graphics are disabled by default.

Is this a laptop or desktop?  Make and model and graphics card model?

---

### Post by jane1960 on 2017-11-16
Thanks a lot for your replies.
It makes sense to me that Ubuntu disables on board graphics, as most people would want to use the card for graphics.
I'm running a desktop with an ASUS 1151 Z270-P and a NVIDIA's GeForce 1080ti.

Here are the outputs of the commands

```
$ sudo lsmod
Module                  Size  Used by
btrfs                1093632  0
xor                    24576  1 btrfs
raid6_pq              114688  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                  102400  0
msdos                  20480  0
jfs                   184320  0
xfs                  1187840  0
libcrc32c              16384  1 xfs
cpuid                  16384  0
bnep                   20480  2
ccm                    20480  1
snd_hda_codec_hdmi     49152  2
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   593920  0
arc4                   16384  2
snd_hda_intel          36864  4
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
irqbypass              16384  1 kvm
rtl8192ce              57344  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
rtl_pci                28672  1 rtl8192ce
rtl8192c_common        49152  1 rtl8192ce
rtlwifi                73728  3 rtl_pci,rtl8192ce,rtl8192c_common
mac80211              782336  3 rtl_pci,rtl8192ce,rtlwifi
cfg80211              602112  2 mac80211,rtlwifi
snd_rawmidi            32768  1 snd_seq_midi
nvidia_uvm            671744  0
aesni_intel           167936  2
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_seq,snd_pcm
snd                    77824  19 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
soundcore              16384  1 snd
industrialio           69632  2 acpi_als,kfifo_buf
mei_me                 40960  0
hci_uart               98304  0
mei                   102400  1 mei_me
intel_lpss_acpi        16384  0
btbcm                  16384  1 hci_uart
input_leds             16384  0
shpchp                 36864  0
btqca                  16384  1 hci_uart
btintel                16384  1 hci_uart
bluetooth             557056  11 hci_uart,btintel,btqca,bnep,btbcm
wmi                    16384  2 asus_wmi,mxm_wmi
intel_lpss             16384  1 intel_lpss_acpi
mac_hid                16384  0
acpi_pad              180224  0
uas                    24576  0
usb_storage            69632  1 uas
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
nvidia_drm             45056  2
i915                 1449984  3
nvidia_modeset        843776  4 nvidia_drm
nvidia              13004800  200 nvidia_modeset,nvidia_uvm
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  2 i915,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  81920  0
ahci                   36864  2
drm                   352256  6 i915,nvidia_drm,drm_kms_helper
mii                    16384  1 r8169
libahci                32768  1 ahci
video                  40960  2 asus_wmi,i915
i2c_hid                20480  0
hid                   114688  3 i2c_hid,hid_generic,usbhid
fjes                   73728  0
```

```
sudo ls -la /usr/share/X11/xorg.conf.d/
total 40
drwxr-xr-x 3 root root 4096 Nov 13 09:43 .
drwxr-xr-x 5 root root 4096 Apr 12  2017 ..
-rw-r--r-- 1 root root   92 Mar 16  2017 10-amdgpu.conf
-rw-r--r-- 1 root root 1350 Oct 13 13:23 10-quirks.conf
-rw-r--r-- 1 root root   92 Mar 16  2017 10-radeon.conf
-rw-r--r-- 1 root root  964 Mar 10  2017 40-libinput.conf
drwxr-xr-x 2 root root 4096 Nov 10 17:32 50-nvidia-drm-outputclass.conf
-rw-r--r-- 1 root root  590 Mar  7  2017 51-synaptics-quirks.conf
-rw-r--r-- 1 root root 1751 Mar  7  2017 70-synaptics.conf
-rw-r--r-- 1 root root 2747 Mar  7  2017 70-wacom.conf
lrwxrwxrwx 1 root root   29 Nov 10 17:32 glamoregl.conf -> /etc/alternatives/glamor_conf
```

   ```
sudo lspci -vv
[https://paste.ubuntu.com/25974292/](https://paste.ubuntu.com/25974292/)

```

---

### Post by Autodave on 2017-11-16
"It makes sense to me that Ubuntu disables on board graphics, as most people would want to use the card for graphics."

Ubuntu doesn't disable it: your motherboard/BIOS disables it.

---

### Post by Bashing-om on 2017-11-16
jane1960; Hello -

The system sees both the Intel and nvidia graphic's sets . Great !

Generally it is the tool nvidia-prime that controls which card is that primary.

Check that nvidia-prime and nvidia-settings are installed:
```

dpkg -l | grep -i nvidia

```

And do you have the config file ?
```

ls -al /etc/X11/Xorg.conf

```

[INDENT][INDENT]you can have it either way
[/INDENT][/INDENT]

---

