---
title: "GPU twice in System Details, resolution 1024x768, Unknown Display and wrong name iGPU"
date: 2024-06-22
forum: Hardware
---

### Post by hadronfive on 2024-06-22
Hi, I have just installed Ubuntu 24.04 LTS, the main problem is the capped resolution at 1024x720, however, the symptoms are different to what I've seen in searches.

There are two problems:

[LIST=1]
[*]My dedicated GPU Nvidia GeForce GTX 960 shows up twice in System Details and I have 2 Unknown Displays in the Display settings 
[*]I don't know if my integrated Intel(R) HD Graphics 4600 are detected and installed correctly 
[/LIST]
I just need some help figuring out if these are one problem or two individual ones. However I don't have the knowledge to confirm that or know how to solve Problem 1 with the 2x GPU being shown.

If the Intel(R) HD Graphics 4600 are correctly detected and installed, and it turns out that my monitor just cannot be detected, then I can create my own Display (I have seen guides how to do that). However, I would like to confirm if everything is installed correctly to avoid future problems with my graphics.
 
System Details:

[[IMG]https://i.postimg.cc/3JQK2DLh/System-Details.png[/IMG]]("https://postimages.org/")

Here are the Display settings, you can see that (1) is the one and only screen I am looking at:

[[IMG]https://i.postimg.cc/SNLmdN5M/Display-Settings.png[/IMG]]("https://postimages.org/")

During my try to re-install Ubuntu, I have noticed that for the  Installer, the onboard and the dedicated GPU get identified correctly in  System Details. Reinstalling did not help, unfortunately. Ubuntu seems  to always install it like that right now.


**More information:**

I am dual-booting Windows 10 and Ubuntu. I have just installed Windows freshly as well. Clean slate, setting up the computer. Grub and launching works fine, so I am happy about that.

My CPU is the Intel(R) Core(TM) i5-4460 with an integrated Intel(R) HD Graphics 4600, and I also have a dedicated NVIDIA GeForce GTX 960.

My monitor only has 1 VGA port and is connected to the GTX 960, not the mainboard port.

**PS: I've noticed that it shows up in the ****lshw and**** lspci**** logs, but wrongly as Xeon.** At least I only know it by Intel(R) HD Graphics 4600.

Here are some logs that I've seen people post in related posts:

**sudo glxinfo -B:**

```

    name of display: :1
    display: :1  screen: 0
    direct rendering: Yes
    Memory info (GL_NVX_gpu_memory_info):
        Dedicated video memory: 4096 MB
        Total available memory: 4096 MB
        Currently available dedicated video memory: 3688 MB
    OpenGL vendor string: NVIDIA Corporation
    OpenGL renderer string: NVIDIA GeForce GTX 960/PCIe/SSE2
    OpenGL core profile version string: 4.6.0 NVIDIA 535.183.01
    OpenGL core profile shading language version string: 4.60 NVIDIA
    OpenGL core profile context flags: (none)
    OpenGL core profile profile mask: core profile
    
    OpenGL version string: 4.6.0 NVIDIA 535.183.01
    OpenGL shading language version string: 4.60 NVIDIA
    OpenGL context flags: (none)
    OpenGL profile mask: (none)
    
    OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 535.183.01
    OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```

**inxi -SMCGx:**

```

    System:
      Host: ***** Kernel: 6.8.0-35-generic arch: x86_64 bits: 64
        compiler: gcc v: 13.2.0
      Desktop: GNOME v: 46.0 Distro: Ubuntu 24.04 LTS (Noble Numbat)
    Machine:
      Type: Desktop Mobo: Gigabyte model: B85M-D3H v: x.x
        serial: <superuser required> UEFI: American Megatrends v: F13
        date: 06/19/2014
    CPU:
      Info: quad core model: Intel Core i5-4460 bits: 64 type: MCP arch: Haswell
        rev: 3 cache: L1: 256 KiB L2: 1024 KiB L3: 6 MiB
      Speed (MHz): avg: 2098 high: 3400 min/max: 800/3400 cores: 1: 3400 2: 800
        3: 3393 4: 800 bogomips: 25543
      Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
    Graphics:
      Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics
        vendor: Gigabyte driver: i915 v: kernel arch: Gen-7.5 bus-ID: 00:02.0
      Device-2: NVIDIA GM206 [GeForce GTX 960] vendor: Gigabyte driver: nvidia
        v: 535.183.01 arch: Maxwell bus-ID: 01:00.0
      Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.6 driver: X:
        loaded: modesetting,nouveau,nvidia unloaded: fbdev,vesa dri: crocus
        gpu: nvidia,nvidia-nvswitch resolution: 1: 1024x768~60Hz 2: N/A
      API: EGL v: 1.5 drivers: crocus,kms_swrast,nvidia,swrast platforms:
        active: gbm,x11,surfaceless,device inactive: wayland,device-2
      API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: nvidia mesa v: 535.183.01
        glx-v: 1.4 direct-render: yes renderer: NVIDIA GeForce GTX 960/PCIe/SSE2

```

**lshw -c video:**

```

      *-display                 
           description: VGA compatible controller
           product: GM206 [GeForce GTX 960]
           vendor: NVIDIA Corporation
           physical id: 0
           bus info: pci@0000:01:00.0
           version: a1
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
           configuration: driver=nvidia latency=0
           resources: irq:40 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
      *-display
           description: VGA compatible controller
           product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 06
           width: 64 bits
           clock: 33MHz
           capabilities: msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:38 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
      *-graphics
           product: simpledrmdrmfb
           physical id: 2
           logical name: /dev/fb0
           capabilities: fb
           configuration: depth=32 resolution=1024,768

```

[B]lsmod:
[/B]
```

    Module                  Size  Used by
    snd_seq_dummy          12288  0
    snd_hrtimer            12288  1
    nvidia_uvm           1806336  0
    qrtr                   53248  4
    nvidia_drm             94208  8
    bnep                   32768  2
    nvidia_modeset       1314816  10 nvidia_drm
    intel_rapl_msr         20480  0
    intel_rapl_common      40960  1 intel_rapl_msr
    x86_pkg_temp_thermal    20480  0
    intel_powerclamp       24576  0
    coretemp               24576  0
    kvm_intel             487424  0
    snd_hda_codec_realtek   200704  1
    binfmt_misc            24576  1
    nvidia              56827904  437 nvidia_uvm,nvidia_modeset
    kvm                  1437696  1 kvm_intel
    snd_hda_codec_generic   122880  1 snd_hda_codec_realtek
    snd_hda_codec_hdmi     94208  2
    snd_hda_intel          61440  3
    snd_intel_dspcfg       36864  1 snd_hda_intel
    cmdlinepart            12288  0
    snd_intel_sdw_acpi     16384  1 snd_intel_dspcfg
    spi_nor               163840  0
    irqbypass              12288  1 kvm
    crct10dif_pclmul       12288  1
    polyval_clmulni        12288  0
    polyval_generic        12288  1 polyval_clmulni
    mtd                   106496  3 spi_nor,cmdlinepart
    snd_hda_codec         217088  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
    snd_hda_core          151552  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
    ghash_clmulni_intel    16384  0
    mei_pxp                16384  0
    i915                 4276224  3
    snd_hwdep              20480  1 snd_hda_codec
    sha256_ssse3           32768  0
    at24                   28672  0
    sha1_ssse3             32768  0
    aesni_intel           356352  0
    snd_pcm               200704  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
    btusb                  77824  0
    spi_intel_platform     12288  0
    mei_hdcp               28672  0
    spi_intel              32768  1 spi_intel_platform
    snd_seq_midi           24576  0
    crypto_simd            16384  1 aesni_intel
    btrtl                  36864  1 btusb
    snd_seq_midi_event     16384  1 snd_seq_midi
    btintel                57344  1 btusb
    drm_buddy              20480  1 i915
    snd_rawmidi            57344  1 snd_seq_midi
    btbcm                  24576  1 btusb
    cryptd                 28672  2 crypto_simd,ghash_clmulni_intel
    btmtk                  16384  1 btusb
    ttm                   114688  1 i915
    rapl                   20480  0
    snd_seq               118784  9 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
    bluetooth            1032192  15 btrtl,btmtk,btintel,btbcm,bnep,btusb
    snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
    drm_display_helper    253952  1 i915
    intel_cstate           24576  0
    snd_timer              49152  3 snd_seq,snd_hrtimer,snd_pcm
    cec                    98304  2 drm_display_helper,i915
    rc_core                77824  1 cec
    i2c_i801               36864  0
    ecdh_generic           16384  1 bluetooth
    i2c_smbus              16384  1 i2c_i801
    snd                   147456  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
    i2c_algo_bit           16384  1 i915
    ecc                    45056  1 ecdh_generic
    mei_me                 53248  2
    lpc_ich                32768  0
    soundcore              16384  1 snd
    mei                   172032  5 mei_hdcp,mei_pxp,mei_me
    nls_iso8859_1          12288  1
    input_leds             12288  0
    serio_raw              20480  0
    mac_hid                12288  0
    msr                    12288  0
    parport_pc             53248  1
    ppdev                  24576  0
    lp                     28672  0
    parport                77824  3 parport_pc,lp,ppdev
    efi_pstore             12288  0
    nfnetlink              20480  1
    dmi_sysfs              24576  0
    ip_tables              36864  0
    x_tables               69632  1 ip_tables
    autofs4                57344  2
    hid_generic            12288  0
    usbhid                 77824  0
    hid                   184320  2 usbhid,hid_generic
    xhci_pci               24576  0
    crc32_pclmul           12288  0
    ahci                   49152  2
    r8169                 118784  0
    realtek                36864  1
    libahci                57344  1 ahci
    xhci_pci_renesas       20480  1 xhci_pci
    video                  73728  2 i915,nvidia_modeset
    wmi                    32768  1 video

```

**lspci -nnk | grep -i vga -A3:**

```

    00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
        Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [1458:d000]
        Kernel driver in use: i915
        Kernel modules: i915
    --
    01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
        Subsystem: Gigabyte Technology Co., Ltd GM206 [GeForce GTX 960] [1458:36be]
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```


**What I have tried:**
 
[LIST]
[*]Reinstalling Ubuntu 
[*]ubuntu-drivers install, ubuntu-drivers autoinstall 
[*]Install the older 470 Nvidia driver both from Additional Drivers and terminal via ubuntu-drivers install, but that was back before I thought that Intel HD Graphics not detected was the problem 
[*]Manually install Intel HD Graphics 4600 driver, however I quickly noticed that it should be in Ubuntu by default (I was unable to find the drivers, instead the Intel website directed me to the Ubuntu website, which told me that Intel drivers are in the kernel already) 
[/LIST]
 If you know something that can help, I am grateful! And if you need any more details, I am happy to post them.

---

### Post by hadronfive on 2024-06-23
Hi, if you need any more details, feel free to ask! I just need a quick assessment, figuring out if these are one problem or two individual ones.

Even if you say that it is fine and just a visual glitch in the System Details, that would be great! Just need a quick expert looking over and saying "that's fine" or "that's not fine".

Thanks for everyone in advance!

---

### Post by Yellow Pasque on 2024-06-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2060268](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2060268)

If you want to give more info:
```
sudo nvidia-bug-report.sh
```
and attach the resulting log.

---

### Post by hadronfive on 2024-06-23
Sure, here's the log: (see attachment)

---

### Post by Yellow Pasque on 2024-06-23
> (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768

See the bug report I linked to and make sure SimpleDRM is disabled. I think it's causing your issue. The correct kernel modules are loaded for your GPUs and the 3D renderer is correct.

---

### Post by hadronfive on 2024-06-23
Alright, thank you very much! The problem with 2x GPU is now solved.

Another problem has arisen: My suspicion that my Intel HD Graphics 4600 is not detected is now amplified. Look at these System Details:

[URL="https://postimages.org/"][IMG]https://i.postimg.cc/gJz10WdL/System-Details-Software-Rendering.png[/IMG]
[/URL]
"Software Rendering". I've read that means that Ubuntu is in a mode, where Ubuntu hasn't found a fitting driver in the repositories, so it's in Software Rendering mode. That means, that I have to find the right Intel Graphics 4600 driver, if it exists.

Thanks for the help! Somehow I didn't find that bug link, and by solving the first problem, it has lead me to the real problem.

---

### Post by Yellow Pasque on 2024-06-23
> **hadronfive said:**
> Alright, thank you very much! The problem with 2x GPU is now solved.

Okay, but was the resolution problem resolved? That's the important part.

> Another problem has arisen: My suspicion that my Intel HD Graphics 4600 is not detected is now amplified... That means, that I have to find the right Intel Graphics 4600 driver, if it exists.

No. The correct driver is installed in Ubuntu by default. Why are you trying to use the Intel GPU anyway? Do you have more displays than the GTX960 can handle?

---

### Post by hadronfive on 2024-06-23
No, the resolution problem is not solved. However, doesn't it work like Windows where on normal Desktop, the integrated graphics are used? I thought that the missing resolution comes from the missing Intel HD Graphics driver.

But you might be right, for all tasks that are demanding, I will use my dedicated GPU anyway, so perhaps it should suffice to use Wayland to set a custom display.

Another thing I tried is the force probe solution, that you proposed [here]("https://ubuntuforums.org/showthread.php?t=2495988&p=14182328#post14182328"). Unfortunately it didn't work for me. This guy has a very similar problem to mine.

---

### Post by hadronfive on 2024-06-23
I am having a hard time finding an up-to-date guide about setting a custom resolution with Wayland. Does [this]("https://askubuntu.com/questions/973499/wayland-how-to-set-a-custom-resolution") guide still work?

---

### Post by Yellow Pasque on 2024-06-23
I don't use Wayland and don't know anything about it.

> **hadronfive said:**
> doesn't it work like Windows where on normal Desktop, the integrated graphics are used? I thought that the missing resolution comes from the missing Intel HD Graphics driver.
You seem to think you have a laptop with hybrid Intel/Nvidia ("Optimus") graphics. You don't. You have two completely separate GPU's. If you don't have any display plugged into the motherboard's video output, go into the BIOS/EFI and disable the Intel GPU. Because You don't need it, and it seems to confuse you.

> Another thing I tried is the force probe solution, that you proposed [here]("https://ubuntuforums.org/showthread.php?t=2495988&p=14182328#post14182328"). Unfortunately it didn't work for me. This guy has a very similar problem to mine.
No. Completely different. That is only for hardware so new (Meteor Lake GPU's), that it hadn't been included in Ubuntu 23.10. That does not apply to your GPU, which already had the i915 module loaded.

---

### Post by hadronfive on 2024-06-23
Alright, so I have read that Ubuntu 24.04 changed to Wayland. Perhaps I should switch to xorg since I then can use the guides with xrandr.

I've also just tried installing the Nvidia GTX 960 driver from Nvidia's homepage, which did fail during the installation, didn't find multiple directories and also didn't add the 1920x1080 resolution. Any more ideas about getting these drivers working?

---

### Post by hadronfive on 2024-06-23
Oh, nevermind:

```
echo $XDG_SESSION_TYPE
x11
```

Which means, xorg is running. So I can use the xrandr guides.

---

### Post by Yellow Pasque on 2024-06-23
> Any more ideas about getting these drivers working?
No. Good luck though.

---

### Post by hadronfive on 2024-06-24
Unfortunately these xrandr guides didn't work for me. I always get this error message:
```
xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  59
  Current serial number in output stream:  59
```

---

