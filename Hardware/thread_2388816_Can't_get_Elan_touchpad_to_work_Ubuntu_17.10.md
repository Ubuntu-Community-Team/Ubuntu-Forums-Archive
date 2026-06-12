---
title: "Can't get Elan touchpad to work Ubuntu 17.10"
date: 2018-04-07
forum: Hardware
---

### Post by meleeikon on 2018-04-07
**I tried:**
i8042.reset, the i8042.kbdreset=1 the nomux. Nada. The touchpad doesn't move the mouse, but significantly gets in the way when trying to type. The slightest brush can randomly send the cursor askew, but deliberate mouse movements and the push to click yield jack diddly-squat.

I even went in and added:
MatchIsTouchpad "on"
Option "TapButton1" "1"

to my 70-synaptics.conf (The site said 50, but that did not exist)
[B]
Relevant (maybe) Information:[/B]
OS: Ubuntu 17.10 x86_64
Host: TravelMate P258-M V1.15
Kernel: 4.13.0-38-generic
Uptime: 1 min
Packages: 1732
Shell: bash 4.4.12
Resolution: 1366x768
DE: ubuntu:GNOME
WM: GNOME Shell
WM Theme: Adwaita
Terminal: gnome-terminal
CPU: Intel i5-6200U (4) @ 2.700GHz
GPU: Intel Integrated Graphics
Memory: 2006MiB / 7844MiB

Linux gambrinus 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

**My Configs:**

grub.conf: ```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="i8042.nomux=1 i8042.kbdreset=1 quiet splash"
GRUB_CMDLINE_LINUX=""
```

synaptics.conf: ```
Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection
```

**Disclaimer:**
Yes, I just dumped uname and neofetch. sosueme. Yes, I know this laptop is a piece of feces, it was free and I use it to connect to vmware webconsoles and managed switches and screenconnect. I don't really want to put Windows 10 back on it, because Windows 10 is worse and I have privacy issues. I mean DNS over TLS was a thing only a few days ago and I have it. No, I'm not really a Linux Guy. I was a slackware guy back in the 90's but 20+ years of professional windows usage has eroded that and I was much smarter before all that college drinking killed my braincells.

---

