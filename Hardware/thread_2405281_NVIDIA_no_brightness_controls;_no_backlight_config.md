---
title: "NVIDIA: no brightness controls; no backlight config file (?)"
date: 2018-11-03
forum: Hardware
---

### Post by bennywas on 2018-11-03
My brightness control keys don't work after installing the NVIDIA driver (but they worked fine on nouveau), and I can't find a brightness slider in the settings GUI to manually slide. My brightness isn't at 100% like some other users' problems; it looks like 10%, I think because that's what I had it set to when I was installing nvidia and rebooting. Anyway, I researched other solutions and a lot of them mention editing configuration files related to X11/xorg or a backlight folder that's supposed to have a configuration file in it, but all of those places were either empty folders for me or didn't exist. **(EDIT: See below posts for what I've already tried.)** Here's my GPU info...

[FONT=courier new]lspci -vnn | grep -i vga[/FONT]
```
00:02.0 VGA  compatible controller [0300]: Intel Corporation 3rd Gen Core processor  Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0  VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT  650M Mac Edition] [10de:0fd5] (rev a1) (prog-if 00 [VGA controller])
```
[FONT=courier new]sudo lshw -C video[/FONT]
```
  *-display                 
       description: VGA compatible controller
       product: GK107M [GeForce GT 650M Mac Edition]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:49 memory:c0000000-c0ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:2000(size=128) memory:c1000000-c107ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c1400000-c17fffff memory:b0000000-bfffffff ioport:3000(size=64)
```

After [searching NVIDIA's website]("https://www.nvidia.com/Download/index.aspx?lang=en-us") for the most recent compatible driver for my card, I settled on nvidia-driver-410 which I installed using [the PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"). (The first time, I tried installing the "recommended" driver versions that were visible from Software & Updates>Additional Drivers...but nvidia-driver-396 had the same screen brightness issue, and nvidia-driver-340 gave me a black screen on boot; so, I used the PPA thinking the newest compatible version wouldn't have this bug. But since it does, that tells me this is a bug across versions, so I'm just gonna keep 410 for now.)

Would someone please walk me through the steps of troubleshooting this? My mind is frazzled from reading so many related posts. :)

---

### Post by bennywas on 2018-11-04
:-\" (Am I in the right subforum? Is my title clear enough? Should I have included more or less information? Are my tags sufficient?)

---

### Post by bennywas on 2018-11-04
**What I've tried:**
[URL="https://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver"]https://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver
[/URL]
- First answer (creating a .conf in /usr/share/X11/xorg.conf.d/)... I actually do have that directory so I tried this solution, writing the file's BoardName as GeForce GT 650M Mac Edition instead of the OP's BoardName; rebooted. Nothing changed. So I deleted the .conf file I created. Also, I noticed there's already a "10-nvidia.conf" file in that directory, which says:
```
Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection
```
Not sure if that matters.
- Second/third/fourth answer... None of the directories they mention exist for me.[FONT=courier new] sudo find / -iname *xorg*.conf [/FONT]shows that the only directory containing an xorg.conf file is "/usr/share/doc/xserver-xorg-video-intel/xorg.conf". (It also returns, "find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied"; not sure if that's important.) So maybe I could try creating an xorg.conf within /etc/X11/...?...
- Fifth answer (bash script)... I read the instructions in that custom script and tried[FONT=courier new] nvidia-settings -n -q all | grep brightness [/FONT]which returned nothing, so I assumed the script wouldn't work for me. So I didn't try it.
 ^ ***EDIT:** I'm revisiting the abovementioned bash script solution. When I add RegistryDwords to /usr/share/X11/xorg.conf.d/10-nvidia.conf, BacklightBrightness appears as an attribute of nvidia-settings. But the script doesn't work. Also, another way to make BacklightBrightness show up as an attribute is running nvidia-xconfig and adding the RegistryDwords lines to the newly created /etc/X11/xorg.conf file. And in that instance the script doesn't work either. Whether or not I add RegistryDwords anywhere, ~/.nvidia-settings-rc includes lines mentioning RedBrightness and RedGamma (etc.)...so...maybe I could try editing those directly?
- Sixth answer (nvidiabl)... That nvidiabl github page looks super old, and I'm not confident enough to use a forked project, so I didn't try.
- Last answer on page... I tried this solution, since "/usr/share/doc/xserver-xorg-video-intel/xorg.conf" is the one conf file I actually do have. Previously written in it was:
```
Section "Device"
    Identifier "Intel"
    Driver "intel"
#    Option "AccelMethod" "uxa"
EndSection
```
I commented all that out and added:
```
Section "Device"
    Identifier "NVIDIA"
    Driver "nvidia"
#    Option "AccelMethod" "uxa"
EndSection
```
And rebooted. Nothing was fixed, so I undid it. (**EDIT:** I should try this but with the RegistryDwords parahraph. Will update.) Given that the directory had intel in the name, I guess I shouldn't've expected it to work. I should mention though: there *is* a /usr/share/doc/xserver-xorg-video-nvidia-410 folder, containing only a changelog and a copyright (no conf). Maybe I should add a conf file to this...?... Then again, the xserver-xorg-video-nouveau folder doesn't have a conf file, and brightness control was working fine when I was using that, so...idk. I didn't try adding anything there yet.
- By the way, I have no "nvidia_backlight", "intel_backlight", or "acpi_video0" folders anywhere.[FONT=courier new] sudo find / -iname *backlight* [/FONT][pastebin,]("https://paste.ubuntu.com/p/CNtNgNsctT/")[FONT=courier new] sudo find / -iname *brightness* [pastebin]("https://paste.ubuntu.com/p/dqFwcsQGtH/").

[/FONT]**More things I've tried:**
[https://forums.linuxmint.com/viewtopic.php?t=185148](https://forums.linuxmint.com/viewtopic.php?t=185148)
- My NVIDIA X Server Settings doesn't seem to have brightness controls in the interface. It also doesn't have a "PRIME Profiles" tab, which other posts keep mentioning but is lacking for me. For the record, the interface didn't have this tab when I was trying the "recommended" older nvidia version either.
- I tried editing GRUB to include acpi_backlight=video, vendor, native, and none, but none of those options fixed anything.
- Installed xbacklight and rebooted, but none of the commands work (so I uninstalled it).
- Ran nvidia-xconfigure from root shell, which returned:
```
 WARNING: Unable to locate/open X configuration file.

Package xorg-server was not found in the pkg-config search path
Perhaps you should add the directory containing 'xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
New X configuration file written to '/etc/X11/xorg.conf'
```
To clarify, I have no 'xorg-server.pc' anywhere on my computer (although there is a '/usr/share/apport/package-hooks/source_xorg-server.py').
And so now that I have that xorg.conf, still, nothing's fixed on reboot.
- I tried editing the new /etc/X11/xorg.conf file to include the BoardName and Option described in the very first solution I looked at, but no change. So I'm gonna delete the files I nvidia-xconfiure created in '/etc/X11/', which were xorg.conf, xorg.conf.save, and xorg.conf.nvidia-xconfig-original. Deleted.
- Maybe I should try running X -configure...?...

I'll keep looking around and trying solutions, but I really feel like I've hit rock bottom in terms of the similarity of other people's problems and also my limited knowledge of Linux/computers in general. As a last resort, maybe someone could recommend to me what the newest version of nvidia I could install that might not have this issue? Any help would be appreciated honestly.

---

### Post by dtach on 2019-10-19
Hi Bennywas. Thank you for your detailed troubleshooting you've documented for this issue. I am experiencing the same thing. Did you ever find a solution?

---

