---
title: "Biostar NF61VM2"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by beemer on 2006-11-02
Does anyone know how to get the Nvidia chipset on the Biostar NF61VM2 to work under edgy?  I can't get sound or dma because of this.  lspci gives "unknown"s for like 13 items in the list for NVIDIA Chipset stuff. 

The [Newegg]("http://www.newegg.com/Product/Product.asp?Item=N82E16813138036") prod specs show a nforce 400 chipset but I'm really confused if I should use nforce drivers from nvidia or what to do?  For sound, I tried intel8x0 and hda-intel but neither seemed to work when I modprobed them.

Edit: Here's the biostar link: [Biostar NF61VM2]("http://http://www.biostar-usa.com/mbdetails.asp?model=NF61V%20Micro%20AM2")

Thanks,

Beemer

---

### Post by beemer on 2006-11-02
Anyone have this board?

Here's a lspci output:
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
**00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)**
**00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)**
00:07.0 Bridge: nVidia Corporation Unknown device 03ef (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0392 (rev a1)

---

### Post by beemer on 2006-11-03
no one else has this board?

---

### Post by skunkydog on 2006-11-06
I have the same audio device, but I think my board is MSI.  Anyway, no audio here either.  

But hey, now you got company!

---

### Post by skunkydog on 2006-11-07
I found [this]("http://www.nvnews.net/vbulletin/showthread.php?t=75920") page which pointed to [this]("http://www.nvidia.com/object/linux_nforce_1.11.html") page.  It sounded like Ubuntu should have the driver already.  I looked around and found snd-hda-intel.ko and cnd-hda-codec.ko.  I did ```
modprobe  snd\-hda\-intel
modprobe snd\-hda\-codec
``` to load them, but still no audio.  /dev/dsp is also still missing.

[Newegg ]("http://www.newegg.com/Product/Product.asp?Item=N82E16813138036") says your board has the Realtek ALC861 chipset.  So maybe [this]("http://www.linuxforums.org/forum/linux-laptops/70890-there-no-sound-when-i-installed-ubuntu-my-laptop.html") page will help you.

---

### Post by skunkydog on 2006-11-08
Mine's working now.  I tried installing alsa-tools and alsa-oss but I also downloaded alsa-drivers so I don't know what worked.  lsmod now shows:

snd_hda_intel          21528  1 
snd_hda_codec         172544  1 snd_hda_intel
snd_pcm_oss            47232  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84996  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm

at least the first 2 of which were not there before.
The mixer shows the device as HDA NVidia and gamix as HDA NVidia: Realtek ALC888.

I just built this so if I do it again, I'll be careful to see what does it.

---

### Post by liam.casimir on 2006-12-27
hey guys, i have a Biostar mobo too (NF61VM2), same problem as yours INTEGRATED AUDIO
(Realtek ALC861 8-Channel HD Audio), INTEGRATED LAN Realtek RTL8201CL PHY- Integrated 10/100 transceiver), i have dapper drake installed. i'm currently downloading edgy hoping that it will fix the problem.  any update?

---

