---
title: "Dual Head Belkin Soho 4 port KVM problem with 1 edid.bin"
date: 2014-08-04
forum: Hardware
---

### Post by musicboy on 2014-08-04
I set up this dual head KVM but switching between 2 PC's resets the first one, when it goes into screen saver or monitors off etc this resets the resolution to the minimum and with an NVIDA graphics card using the NVDIA settings manager will not reset the monitors to the desired resolutions so I have to restart, logging out and logging back in doesn't solve the problem either.

So I set up the edid.bin from the primary first monitor i.e. my left one and then this solves the problem for ONLY that monitor, when switching back and screens off or waking from screen saver, only then the right monitor is reset to low resolution and the same problem the NVIDA settings manager will not allow that monitor to be reset to the desired resolution.

My question is to the Ubuntu community does anyone know how to or can it be done, to set the edid.bin from monitor one i.e. calling it edid_1.bin for the left one and then acquiring after the right monitor edid.bin and naming that edid_2.bin, putting them in the root desktop and then adding both in xorg.config so that on waking the xorg.config reads both monitors edid_1.bin for the left monitor and edid_2.bin for the right monitor.

I just cant work out how to do this, I tried to configure my own method of xorg.config but I must have done something wrong as it would not boot properly so I had to manually delete the xorg.config and reboot then reset xorg.config etc

The only option at present I have is to keep setting the brightness and lock to 'Turn screen of when inactive for: Never' option when going backwards and forwards between PC's using the KVM but obviously I would like to solve this problem, so if anyone could help me set 2x edid.bin files as outlined I would very much appreciate the help.

Thanks,

Studio Freak

---

### Post by papibe on 2014-08-04
Hi musicboy.

I see a couple of options.

First, you can set a different edid file for different monitors. The proprietary Nvidia driver allows that. The syntax is something like:
```
Option	"CustomEDID" "DFP-0:/etc/X11/right.bin"
Option	"CustomEDID" "DFP-1:/etc/X11/left.bin"
```
DPF-0 and DFP-1 are the naming convention the Nvidia driver uses and it may change depending on the interface (VGA, HDMI, etc). Check your '/var/log/Xorg.0.log' to get the proper names.

The Nvidia driver also saves part of your customization on your home directory (in ~/.nvidia-settings-rc). That is the reason why most settings you save on the 'Nvidia X Server Settings' are correctly loaded every time you log into the desktop (without saving the info on /etc/X11/xorg.conf)

The latter works because there's a script set on 'Startup Applications' that load the configuration from your directory. The content of the script is very simple:
```
sh -c '/usr/bin/nvidia-settings --load-config-only'
```
I imagine that if you save your setting using 'Nvidia X Server Settings' (or nvidia-settings), you can reload them by running the script manually again.

Hope that helps. Let us know if you need more help with that.
Regards.

---

