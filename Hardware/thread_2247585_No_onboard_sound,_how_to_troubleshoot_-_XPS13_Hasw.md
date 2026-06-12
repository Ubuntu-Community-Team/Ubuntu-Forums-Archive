---
title: "No onboard sound, how to troubleshoot - XPS13 Haswell snd_hda_intel"
date: 2014-10-09
forum: Hardware
---

### Post by witchbutter on 2014-10-09
I'm running Ubuntu 14.04 on a Haswell XPS 13.  I have had nothing but audio problems since installing 14.04.  The most annoying issue is that I hear the drum roll as Ubuntu starts up, and as soon as I log in there is no sound and I can't seem to start it.

Each kernel update seems to provide less consistency and I would be extremely grateful if I could get some guidance on how to troubleshoot this.
With kernels 3.13.0-35-lowlatency & 3.13.0-36-lowlatency I was able to issue pulseaudio --start after login and sound would work.  However the current kernel
3.13.0-37-lowlatency this no longer works.

Before anyone tells me to Google this, save your keystrokes, I have many times and nothing I have read or tried works.  I'd really like to know a troubleshooting strategy to do deal with this reoccuring problem, rather than using a search engine to hope for the best.

I have also reached out to the Dell community and gotten no help.

lspci:
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

intel module is present:
sudo lsmod | grep intel 
intel_rapl             18773  0 
intel_powerclamp       14705  0 
snd_hda_intel          52306  4 
kvm_intel             143153  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   455581  1 kvm_intel
snd_pcm               102040  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd                    69273  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
intel_smartconnect     12619  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  6 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  4 ghash_clmulni_intel,aesni_intel,ablk_helper

---

