---
title: "Ubuntu 20.04 not recognizing my intel integrated graphics"
date: 2021-03-28
forum: Hardware
---

### Post by fukur on 2021-03-28
Hi guys, so as the title says ubuntu doesn't seem to recognize my hardware. 
My motherboard is very new on the market so I'm assuming it has to do with my bios/UEFI(?), but I can't seem to pinpoint the problem.

Ubuntu 20.04
Kernel 5.8.0-48-generic

Here's the relevant hardware:
MB: ASUS PRIME B560M-A 
Processor: Intel Core i7-10700 (UHD Graphics 630)
(No dedicated graphics card)

To get 20.04 installed I had to install through the "safe graphics mode" and to be able to boot onto the desktop I have to use the 'nomodeset' flag.
If I don't use either of these methods, I'm met with a black screen... I never even get to a Ubuntu splash without the nomodeset; it will blink the ASUS splash screen and go to the black screen, which I think points to graphics driver issues.


When looking at Settings > About it shows my processor correctly, but show "llvmpipe (LLVM 11.0.0, 256 bits)" for the graphics.


My computer does have the i915 driver installed and I manually added the module with modprobe i915 just to make sure.

Here's some more information:
[FONT=Arial]```

glxinfo -B

name of display: :1
display: :1  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Mesa/X.org (0xffffffff)
    Device: llvmpipe (LLVM 11.0.0, 256 bits) (0xffffffff)
    Version: 20.2.6
    Accelerated: no
    Video memory: 31933MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 11.0.0, 256 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 20.2.6
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 3.1 Mesa 20.2.6
OpenGL shading language version string: 1.40
OpenGL context flags: (none)

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.2.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```[/FONT]
[FONT=Arial]```

lshw -c video

  *-display UNCLAIMED      
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0

       resources: iomemory:600-5ff iomemory:400-3ff memory:6000000000-6000ffffff memory:4000000000-400fffffff ioport:3000(size=64) memory:c0000-dffff

```[/FONT]
[FONT=Arial]```

lspci -nnk | grep -i vga -A3

00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:9bc5] (rev 05)
DeviceName: Onboard - Video
Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
Kernel modules: i915

```[/FONT]
```

[FONT=Arial]lsmod
[/FONT]
[FONT=Arial]Module                  Size  Used by
nls_iso8859_1          16384  1
intel_rapl_msr         20480  0
mei_hdcp               24576  0
intel_rapl_common      28672  1 intel_rapl_msr
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
crct10dif_pclmul       16384  1
ghash_clmulni_intel    16384  0
snd_hda_intel          53248  0
aesni_intel           372736  0
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         139264  1 snd_hda_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
snd_hda_core           94208  2 snd_hda_intel,snd_hda_codec
rapl                   20480  0
snd_hwdep              20480  1 snd_hda_codec
i915                 2195456  0
snd_pcm               114688  3 snd_hda_intel,snd_hda_codec,snd_hda_core
intel_cstate           20480  0
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
eeepc_wmi              16384  0
asus_wmi               36864  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
intel_wmi_thunderbolt    20480  0
wmi_bmof               16384  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
joydev                 24576  0
input_leds             16384  0
drm_kms_helper        217088  1 i915
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
efi_pstore             16384  0
snd_timer              40960  2 snd_seq,snd_pcm
ee1004                 20480  0
snd                    94208  8 snd_seq,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
cec                    53248  2 drm_kms_helper,i915
rc_core                57344  1 cec
soundcore              16384  1 snd
i2c_algo_bit           16384  1 i915
mei_me                 40960  1
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
mei                   106496  3 mei_hdcp,mei_me
sysimgblt              16384  1 drm_kms_helper
sch_fq_codel           20480  2
mac_hid                16384  0
acpi_tad               16384  0
acpi_pad              184320  0
parport_pc             45056  1
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
drm                   552960  2 drm_kms_helper,i915
ip_tables              32768  0
x_tables               49152  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   135168  2 usbhid,hid_generic
crc32_pclmul           16384  0
nvme                   45056  2
e1000e                262144  0
intel_lpss_pci         20480  0
intel_lpss             16384  1 intel_lpss_pci
i2c_i801               32768  0
nvme_core             110592  4 nvme
ahci                   40960  0
idma64                 20480  0
xhci_pci               20480  0
i2c_smbus              20480  1 i2c_i801
libahci                36864  1 ahci
xhci_pci_renesas       20480  1 xhci_pci
virt_dma               20480  1 idma64
wmi                    32768  3 intel_wmi_thunderbolt,asus_wmi,wmi_bmof
video                  49152  2 asus_wmi,i915
pinctrl_tigerlake      32768  0
pinctrl_intel          28672  1 pinctrl_tigerlake[/FONT]

```[FONT=Arial]
[/FONT]
[FONT=Arial]It's weird to me that lshw shows it as "[/FONT][COLOR=#000000][FONT=&amp]configuration: latency=0"[/FONT][/COLOR][FONT=Arial], but lspci seems to know that there is a relevant kernel module.

Any help would be appreciated [/FONT]:)!

---

### Post by QIII on 2021-03-28
Hello.

That hardware was not released until just after 20.04 was.  It is possible that your kernel version does not support the graphics.

I think the 5.8 kernel is part of the HWE stack, so you may be as far along as you can get with 20.04.

If you have little invested in 20.04 at this point, you may want to do a fresh install of 20.10.

However, using a non-LTS version will condemn you to 9 month updates until the next LTS is released, which should be 22.04.

---

### Post by fukur on 2021-03-28
Hi QIII,

I should have stated this in the first post, but I've tried 20.10 with the same problems. I just switched back to 20.04, since it's the version I would want to be on.

---

### Post by Doug S on 2021-03-28
I have similar, yet different enough, I suppose. About 2 weeks old now.
i5-10600K and ASUS Z490-A.
In terms of marketing names, mine seems to be COMETLAKE and yours TIGERLAKE.  [COLOR="#FF0000"]<<< EDIT 4: Yours is COMETLAKE[/COLOR]
I only run Ubuntu server, and cheated, bringing my 20.04 NVME drive from my i5-9600K computer to this one.
Anyway,...

I do observe a couple of differences in the listed stuff. As you mentioned there is no driver listed in yours under configuration, but mine lists i915:

```
doug@s19:~$ glxinfo -B
Error: unable to open display
doug@s19:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: [COLOR="#FF0000"]driver=i915[/COLOR] latency=0
       resources: iomemory:600-5ff iomemory:400-3ff irq:144 memory:6000000000-6000ffffff memory:4000000000-400fffffff ioport:3000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
doug@s19:~$ lspci -nnk | grep -i vga -A3
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:9bc5] (rev 05)
        DeviceName: Onboard - Video
        Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
        [COLOR="#FF0000"]Kernel driver in use: i915[/COLOR]
doug@s19:~$
```

As is happens, I haven't even tried the a normal Ubuntu kernel on this computer yet, as I typically run development kernels. Currently 5.12-rc4. But I'll try one and report back.

Other notes: I updated BIOS. I got all the latest firmware (Note: Ubuntu is sometimes behind in firmware and microcode). I did notice some upstream TIGERLAKE commits recently, so suggest you try the latest [Ubuntu mainline PPA kernel]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), just as a test.

EDIT 1: see [here]("https://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs/811487#811487") about firmware
EDIT 2: Standard Ubuntu kernel works fine:

```
doug@s19:~$ uname -a
Linux s19 5.4.0-70-generic #78-Ubuntu SMP Fri Mar 19 13:29:52 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```
EDIT 3: If you are using QFan BIOS control, be aware in my case there is a 12 degree difference between what ASUS thinks the processor temperature is and what it really is under heavy load. I had to compensate to get the desired response curve.

---

### Post by TheFu on 2021-03-28
You've probably already done all these, but for any lurkers later:

```
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```
If it installs any drivers, reboot.

Couldn't hurt.

---

### Post by fukur on 2021-03-28
> **TheFu said:**
> You've probably already done all these, but for any lurkers later:

```
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```
If it installs any drivers, reboot.

Couldn't hurt.


Hey TheFu, Yeah I tried that out at some point, no new drivers were installed~ 

Thanks for the advice though

---

### Post by fukur on 2021-03-28
> **Doug S said:**
> I have similar, yet different enough, I suppose. About 2 weeks old now.
i5-10600K and ASUS Z490-A.
In terms of marketing names, mine seems to be COMETLAKE and yours TIGERLAKE.
I only run Ubuntu server, and cheated, bringing my 20.04 NVME drive from my i5-9600K computer to this one.
Anyway,...

I do observe a couple of differences in the listed stuff. As you mentioned there is no driver listed in yours under configuration, but mine lists i915:

```
doug@s19:~$ glxinfo -B
Error: unable to open display
doug@s19:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: [COLOR=#FF0000]driver=i915[/COLOR] latency=0
       resources: iomemory:600-5ff iomemory:400-3ff irq:144 memory:6000000000-6000ffffff memory:4000000000-400fffffff ioport:3000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
doug@s19:~$ lspci -nnk | grep -i vga -A3
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:9bc5] (rev 05)
        DeviceName: Onboard - Video
        Subsystem: ASUSTeK Computer Inc. Device [1043:8694]
        [COLOR=#FF0000]Kernel driver in use: i915[/COLOR]
doug@s19:~$
```

As is happens, I haven't even tried the a normal Ubuntu kernel on this computer yet, as I typically run development kernels. Currently 5.12-rc4. But I'll try one and report back.

Other notes: I updated BIOS. I got all the latest firmware (Note: Ubuntu is sometimes behind in firmware and microcode). I did notice some upstream TIGERLAKE commits recently, so suggest you try the latest [Ubuntu mainline PPA kernel]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), just as a test.

EDIT 1: see [here]("https://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs/811487#811487") about firmware
EDIT 2: Standard Ubuntu kernel works fine:

```
doug@s19:~$ uname -a
Linux s19 5.4.0-70-generic #78-Ubuntu SMP Fri Mar 19 13:29:52 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```
EDIT 3: If you are using QFan BIOS control, be aware in my case there is a 12 degree difference between what ASUS thinks the processor temperature is and what it really is under heavy load. I had to compensate to get the desired response curve.


Hey Doug,

Thanks for the response. I've tried the latest mainline stable kernel update (5.11.10) and it didn't make a difference for me. Although in your edit, it seems that the standard kernel shipped with 20.04 is working in your case.
I still haven't tried the firmware updates yet, but I'm hoping that it will make a difference. Will also try to update my BIOS and see if that has an effect (if it's out of date anyway).

Will report back soon.

Thanks

---

### Post by Doug S on 2021-03-28
> **fukur said:**
>  I've tried the latest mainline stable kernel update (5.11.10) and it didn't make a difference for me. No, I meant kernel 5.14-rc4 (and -rc5 should be out by now actually. It's out on kernel.org)

EDIT 1: See this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1909457") report.
EDIT 2: The code referenced by that bug report is not in the 5.12-rc5 code. Try the Ubuntu kernel referenced in the bug report (5.10.0-14.15, which I do not know how to find it or whatever).
EDIT 3: See [this]("https://unix.stackexchange.com/questions/642535/xorg-detects-no-displays-with-an-intel-uhd-630") (which just refers to the above bug report).

---

### Post by fukur on 2021-03-31
Hi Doug,

I tried out the kernel referenced in the bug report you linked to in your comment.
My problem was fairly similar, so I was hopeful, but it did not seem to solve my problems.

For those people looking at this thread in the future the 
I found the source [here]("https://launchpad.net/ubuntu/+source/linux/5.10.0-14.15") and the .deb files for the kernel [here]("https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/bootstrap/+build/20950478").

---

### Post by CatKiller on 2021-03-31
> **QIII said:**
> I think the 5.8 kernel is part of the HWE stack, so you may be as far along as you can get with 20.04.

If you have little invested in 20.04 at this point, you may want to do a fresh install of 20.10.

Just so you're aware, 20.10 has exactly the same kernel as 20.04 with the HWE stack. 20.04 HWE will get the 21.04 kernel a while after 21.04 is released, the 21.10 kernel a while after 21.10 is released, and the 22.04 kernel a while after 22.04 is released. HWE-edge will get them sooner, but not before they've been used by the interim Ubuntu releases. I think the schedule is 3 months after the interim release for HWE, and 6 weeks after the interim release for HWE-edge.

---

### Post by Doug S on 2021-03-31
> **fukur said:**
> I tried out the kernel referenced in the bug report you linked to in your comment.
My problem was fairly similar, so I was hopeful, but it did not seem to solve my problems.Suggest you add an entry to the bug report with your test results.

If you didn't yet, I would suggest to still try Ubuntu mainline ppa kernel 5.14-rc4 (The mainline builds are broken, yet again, so -rc5 isn't available yet.) While I did look and the code of that patch was not included, perhaps something else was included later on and my search term was rendered incorrect. I did not read the whole thread for that patch set and do not know if it was superseded.

EDIT 1: I see some added information in that [other reference]("https://unix.stackexchange.com/questions/642535/xorg-detects-no-displays-with-an-intel-uhd-630") I gave earlier. Suggest you try the last successfully compiled Ubuntu mainline PPA - drm-tip kernel, [here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/2021-03-25/")

---

