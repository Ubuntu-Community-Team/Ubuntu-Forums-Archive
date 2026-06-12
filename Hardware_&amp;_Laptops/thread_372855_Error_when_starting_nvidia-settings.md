---
title: "Error when starting nvidia-settings"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by simsen on 2007-02-28
Hello all!

First let me declare my absolute fascination with Ubuntu and Kubuntu, they are both such great operating systems! I am currently favouring Kubuntu, I hope I don't offend anyone here on ubuntuforums.org by saying that. KDE just does it for me. When it works, hahah.

However, I have spent countless hours reading forums, guides and how-tos everywhere, and still I cannot find a solution to my main problem: **The screen is positioned too far to the right when at 1280x1024 resolution.**

After many, many hours fiddling with *xorg.conf* and *sudo dpkg-reconfigure xserver-xorg*, I have a smidgeon of hope that nvidia-settings might do the trick, but I get errors when typing "nvidia-settings" in terminal. Here are the errors:
```

ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
X Error: BadDevice, invalid or uninitialized input device 154
Major opcode:  143
Minor opcode:  3
Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
Major opcode:  143
Minor opcode:  3
Resource id:  0x0
Failed to open device
```

**My question is: where do I begin problem-solving this?**

Any help is much appreciated.

- Simsen

---

### Post by simsen on 2007-03-01
YAY YAY YAY! Not only did i fix the strange errors when running **nvidia-settings**, but I also fixed my main problem: t**he viewable area on the screen was positioned wrong when at 1280x1024 resolution**.

The first problem: I removed all sections pertaining to Wacom-tablets in /etc/X11/xorg.conf. I don't have a Wacom-tablet, so it made perfect sense.

My main problem bugged me for hours, but I finally got it right. The solution was deceptively simple, but I still don't understand it fully: I simply added **Option "IgnoreEDID" "1"** to my xorg.conf.

Before I did that I made sure I had the newest Nvidia driver and that the Driver option in the Device section of xorg.conf was set to "nvidia" NOT "nv"

Happy beyond words.

---

