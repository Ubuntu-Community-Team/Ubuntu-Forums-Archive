---
title: "Dell E6420 with NVIDIA N12P"
date: 2011-08-03
forum: Hardware
---

### Post by zerubbabel on 2011-08-03
I'm running Ubuntu 11.04 (amd64) on a Dell Latitude E6420. The paper documentation that came with the system says under Video controller/Discrete: "NVIDIA N12P with 512MB DDR3 switchable". I don't know how to confirm that this is what's actually installed, but there is no nvidia-xconfig installed, so it doesn't seem as if I have the NVIDIA driver installed.

I tried installing NVIDIA-Linux-x86_64-280.12.run (from the NVIDIA web site), but it says I don't have the supported hardware. So how can I tell which driver to install? I can't find "N12P" listed anywhere on the NVIDIA drivers page.

Basically, Ubuntu is running fine on this hardware, except that I can't get my external monitor to work at its maximum resolution, and also, theoretically, the laptop display is supposed to have maximum resolution of 1600x900, but it's only using 1366x768.

Anyway, I'd like to install the latest NVIDIA driver for my system, but don't know which one to install. Any help would be appreciated.

---

### Post by gordintoronto on 2011-08-03
This is a long thread, but you should read it:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

To see what video hardware you have, open Accessories/Terminal and enter the command:
lspci

The line(s) which includes the word "VGA" describe your video adapter(s).

---

