---
title: "how do I tell which X driver is used?"
date: 2010-02-13
forum: Hardware
---

### Post by akos.maroy on 2010-02-13
with no xorg.conf file, and everything automagically being configured for X, how would I tell which X driver is actually in use? xdpyinfo doesn't seem to provide this information :(

also, when HOWTOs talk about adding settings to the xorg.conf file, which is nonexistent, I saw 'minimal' xorg.conf files that should be used, and the special settings added. but these haven't worked for me. so, what is the 'default' minimal xorg.conf file, that is equivalent in effect to the automagical configuration?

and another question: on 10.04, where did /etc/init.d/gdm go? how do I start the login screen manually?

---

### Post by mikewhatever on 2010-02-13
Try this:

sudo lshw -C display | grep -i driver

---

### Post by akos.maroy on 2010-02-13
> **mikewhatever said:**
> Try this:

sudo lshw -C display | grep -i driver

well, this displays the hardware (actually does not display anything, but without the grep it does), but it does not show which X driver is being used...

---

### Post by Ayuthia on 2010-02-13
You can also look at /var/log/Xorg.0.log.  It will tell you which driver is being used.

For most of the graphics card setups, I think that xorg.conf has been the best place to configure.  If it is other devices, most of the default settings are found in /usr/share/hal/fdi/policy and any personal changes should be copied and placed in /etc/hal/fdi/policy so that they are not overwritten on updates.  

However in Lucid, it will change to udev so the default settings will be found in /lib/udev/rules.d and any changes should go into /etc/udev/rules.d.  

This is all changing because hal has been deprcated and udev is now the replacement.

If you are looking to start gdm, you can do it by the following:
```
sudo service gdm start
```
The service command is the replacement for /etc/init.d so you can use start, restart, or stop just like you used to use.

---

### Post by Girya on 2010-02-13
```
grep -i driver /etc/X11/xorg.conf
```

returns 	Driver	"nvidia" on my sys karmic

---

### Post by akos.maroy on 2010-02-13
> **Ayuthia said:**
> You can also look at /var/log/Xorg.0.log.  It will tell you which driver is being used.

For most of the graphics card setups, I think that xorg.conf has been the best place to configure.  If it is other devices, most of the default settings are found in /usr/share/hal/fdi/policy and any personal changes should be copied and placed in /etc/hal/fdi/policy so that they are not overwritten on updates.  

However in Lucid, it will change to udev so the default settings will be found in /lib/udev/rules.d and any changes should go into /etc/udev/rules.d.  

This is all changing because hal has been deprcated and udev is now the replacement.

If you are looking to start gdm, you can do it by the following:
```
sudo service gdm start
```
The service command is the replacement for /etc/init.d so you can use start, restart, or stop just like you used to use.

thanks for the info. and how would I force a specific X driver? the system uses 'radeon', but I want to force 'radeonhd'...

---

### Post by Ayuthia on 2010-02-13
Here is what I had for radeonhd in my xorg.conf:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load  "dri"
    Load  "drm"
    Load  "record"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
EndSection

Section "Monitor"
    #DisplaySize      260   160 # mm
    Identifier   "Monitor0"
    VendorName   "AUO"
    ModelName    "9214"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "radeonhd"
    VendorName  "ATI Technologies Inc"
    BoardName   "RS780M/RS780MN [Radeon HD 3200 Graphics]"
        Option     "DRI"                    "True"
        Option     "AccelMethod"            "exa"
        Option     "RenderAccel"            "on"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Modes     "1280x800"
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Modes     "1280x800"
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Modes     "1280x800"
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Modes     "1280x800"
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Modes     "1280x800"
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Modes     "1280x800"
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

Section "ServerFlags"
    Option "AIGLX"  "On"
EndSection

```
I am not for sure if it is all necessary, but it is what I used and was able to get it to work.

I hope that helps.

EDIT: The BoardName is most likely not necessary, but I grabbed it from some other site a while back.

---

### Post by akos.maroy on 2010-02-14
thanks for the xorg.conf file. unfortunately I doesn't work for me. this is what I get at the end:

```
(II) RADEONHD: version 1.3.0, built from non-git sources

(II) Primary Device is: PCI 01@00:00:0
(EE) No devices detected.


```

am I doing something wrong?

---

### Post by mikewhatever on 2010-02-14
> **akos.maroy said:**
> well, this displays the hardware (actually does not display anything, but without the grep it does), but it does not show which X driver is being used...

That's odd. Can you post the output of <sudo lshw -C display>, without grep.
Here's what comes up in my case:

       configuration: driver=**psb** latency=0

---

### Post by akos.maroy on 2010-02-14
> **mikewhatever said:**
> That's odd. Can you post the output of <sudo lshw -C display>, without grep.
Here's what comes up in my case:

       configuration: driver=**psb** latency=0

sure, here it is:

```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff(prefetchable) memory:d4100000-d411ffff ioport:4000(size=256) memory:d4140000-d415ffff(prefetchable)

```

---

### Post by mikewhatever on 2010-02-14
Indeed, there is no driver mentioned. Let's search the modules for a possible candidate:

lsmod | grep 'ati\|radeon\|fglrx\|vesa'

---

### Post by akos.maroy on 2010-02-14
> **mikewhatever said:**
> Indeed, there is no driver mentioned. Let's search the modules for a possible candidate:

lsmod | grep 'ati\|radeon\|fglrx\|vesa'

here you go:

```
# lsmod | grep 'ati\|radeon\|fglrx\|vesa'
snd_hda_codec_atihdmi     2879  1 
snd_hda_codec          79599  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel

```

seems to list only the alsa driver related to the hdmi video output...

---

