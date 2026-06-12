---
title: "Need help with a VT1708/A [Azalia HDAC] sound-chip"
date: 2009-12-03
forum: Hardware
---

### Post by Marran77 on 2009-12-03
Hello 

I have a MSI P4M890-motherboard with a internal soundcard. 
The lspci-command shows:
```
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

It uses the **realtek ALC883-codec**.

After installing the latest nvidia-settings from a ppa (which where buggy, so I removed them and reinstalled the old one) the sound started sound cracky and gave a hissing sound when I raised the volume. 

Adding **ignore_dB=1** to the **load-module module-udev-detect** line in **/etc/pulse/default.pa** solved the hissing and cracking sound (which also worked on my installed Audigy-card). 

But my issue now is that the line-out connected to my stereo produces a very low sound. I have to turn up the volume very much to even hear something and the sound is distorted. So, if someone knows anything about this, please help me...

---

