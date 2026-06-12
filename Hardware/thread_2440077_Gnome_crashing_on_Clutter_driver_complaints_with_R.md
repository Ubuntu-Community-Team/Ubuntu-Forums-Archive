---
title: "Gnome crashing on Clutter driver complaints with Radeon Pro WX 5100"
date: 2020-04-05
forum: Hardware
---

### Post by tmwilder on 2020-04-05
Hello forum community!

I just purchased a Dell Precision machine to do some work from home. I tried to get a box certified via Sputnik because I had read that they were stable and was looking to avoid fiddling - so went for roughly this: [https://certification.ubuntu.com/hardware/201804-26212](https://certification.ubuntu.com/hardware/201804-26212)

However - on initial startup of factory config machine - the GUI works for configuration, restarts - then fails to start the desktop environment. CLI sessions are fine and I can patch and do other ops. On the session starting the desktop UI we get stuck in a text dialog during boot of: ```
UBUNTU: clean, w/x files, y/z blocks 
```

The issue is reproducible on every boot.

Flipping through logs - I observe syslog complaints about driver support for clutter immediately before gdm fails out. I believe this is the error in syslog leading to the actual problem - but am including more logs below and seeking help on determining that:

```

Apr  5 08:30:05 otter gnome-shell[1269]: Unable to initialize Clutter: Unable to initialize the Clutter backend: no available drivers found.
Apr  5 08:30:05 otter gnome-shell[1269]: Unable to initialize Clutter.
Apr  5 08:30:05 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: (pid:1269) done (status:1)
Apr  5 08:30:05 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Apr  5 08:30:05 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: DEBUG(+): Re-starting app: /org/gnome/SessionManager/App1
Apr  5 08:30:05 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: DEBUG(+): Starting app: /org/gnome/SessionManager/App1
Apr  5 08:30:05 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: starting org.gnome.Shell.desktop: command=/usr/bin/gnome-shell startup-id=109d1df9c13dbce045158610060493518700000012460000
Apr  5 08:30:05 otter gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: (pid:1269) done (status:1)
Apr  5 08:30:05 otter gnome-session-binary[1246]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Apr  5 08:30:05 otter gnome-session-binary[1246]: DEBUG(+): Re-starting app: /org/gnome/SessionManager/App1
Apr  5 08:30:05 otter gnome-session-binary[1246]: DEBUG(+): Starting app: /org/gnome/SessionManager/App1
Apr  5 08:30:05 otter gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: starting org.gnome.Shell.desktop: command=/usr/bin/gnome-shell startup-id=109d1df9c13dbce045158610060493518700000012460000
Apr  5 08:30:05 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: started pid:1276
Apr  5 08:30:05 otter gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: started pid:1276
Apr  5 08:30:06 otter gnome-shell[1276]: Unable to initialize Clutter: Unable to initialize the Clutter backend: no available drivers found.
Apr  5 08:30:06 otter gnome-shell[1276]: Unable to initialize Clutter.
Apr  5 08:30:06 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: (pid:1276) done (status:1)
Apr  5 08:30:06 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Apr  5 08:30:06 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: DEBUG(+): Re-starting app: /org/gnome/SessionManager/App1
Apr  5 08:30:06 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Apr  5 08:30:06 otter gnome-session-binary[1246]: DEBUG(+): GsmAutostartApp: (pid:1276) done (status:1)
Apr  5 08:30:06 otter gnome-session-binary[1246]: Unrecoverable failure in required component org.gnome.Shell.desktop
Apr  5 08:30:06 otter /usr/lib/gdm3/gdm-x-session[1204]: gnome-session-binary[1246]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Apr  5 08:30:06 otter gnome-session-binary[1246]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Apr  5 08:30:06 otter gnome-session-binary[1246]: DEBUG(+): Re-starting app: /org/gnome/SessionManager/App1
Apr  5 08:30:06 otter gnome-session-binary[1246]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Apr  5 08:30:06 otter gnome-session-binary[1246]: CRITICAL: We failed, but the fail whale is dead. Sorry....

```

The other suspicious two errors before this failure are:
```
amdkcl: module verification failed: signature and/or required key missing - tainting kernel
```

And one with a complaint of: 
```
[drm:intel_bios_init] [i915] *ERROR* unexpected child device config size 39 (expected 38 for VBT versiion 221)
...
[drm] failed to retrieve link info, disabling eDP

```

I've spent ~8h today Googling and trying things - some sampling of stuff that didn't work ranging from varying degrees of reasonableness to bad guesses based on things I found:

0. Kill gdm and try to start again
1. System reboot
2. Starting gdm3 from another session window
3. apt update -> upgrade and restart
4. An attempt to remove existing amdgpu drivers and install the latest for 18.04 LTS from AMD (resulted in sessions no longer starting, and I opted to factory reset rather than do recovery.)
5. Turning on WaylandEnable=false in /etc/gdm3/custom.conf and do a system restart
6. Call DELL support - they were pretty unfamiliar with debugging Linux systems I bounced around on call for a while. I got a friendly rep who tried but then admitted he really could only debug Windows systems - and started an email support thread to get someone else to help me later.

At this point I'm out of ideas and could use some more expert help - my best working theory is that the drivers I have for the AMD card just don't work with my Gnome config, but I don't have good actionable steps to correct after trying to search for alternatives and could use pointers - let me know if I can provide more info or try anything.

The one thing I'm working on now and will update thread - I saw some folks having success replacing gdm3 with lightdm - so I will try that and update.

Here is some diagnostic info:
```
uname -a Linux otter 4.15.0-1076-oem #86-Ubuntu SMP Wed Mar 4 05:40:20 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

```
lspci | grep -i VGA 

00:02.0 VGA compatible controller: Intel Corporation Device 3e98 (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon Pro WX 5100]
 
```

gpu-manager.log
```

log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-1076-oem/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-1076-oem/updates/dkms
Found amdgpu module: amdgpu.ko
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? yes
Is amdgpu loaded? yes
Is amdgpu blacklisted? no
Is amdgpu versioned? yes
Is amdgpu pro stack? yes
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? yes
Vendor/Device Id: 8086:3e98
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 1002:67c7
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "i915"
Found "/dev/dri/card0", driven by "amdgpu"
Number of connected outputs for /dev/dri/card0: 0
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "amdgpu"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "amdgpu"
Found "/dev/dri/card1", driven by "i915"
output 0:
    card1-DP-5
Number of connected outputs for /dev/dri/card1: 1
Does it require offloading? yes
last cards number = 2
Has amd? yes
Has intel? yes
Has nvidia? no
How many cards? 2
Has the system changed? No
Intel IGP detected
Desktop system detected
or laptop with open drivers
Nothing to do

```

```
grep gnome /var/log/syslog
```
[https://drive.google.com/file/d/12360JpnZ0y_7OfgLgTIwNwDXMu3vX-_s/view?usp=sharing](https://drive.google.com/file/d/12360JpnZ0y_7OfgLgTIwNwDXMu3vX-_s/view?usp=sharing)
Uploaded to public drive since the forum won't let me upload a text file of sufficient size.

---

### Post by tmwilder on 2020-04-05
Trying lightdm am able to get to the login screen, then on actually signing in I get a large nnumber of permission denied errors and the same clutter failure message.

---

### Post by tmwilder on 2020-04-05
I gave up on Dell's factory config and just installed latest 18.04 from a thumb drive and that worked - boo Dell. Maybe the problem related to shipping with kernel 4.15?

---

