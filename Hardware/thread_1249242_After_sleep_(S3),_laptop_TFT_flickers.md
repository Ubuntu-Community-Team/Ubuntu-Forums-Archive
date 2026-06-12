---
title: "After sleep (S3), laptop TFT flickers"
date: 2009-08-25
forum: Hardware
---

### Post by anglergab on 2009-08-25
Hello! 

I have a **Fujitsu Siemens Amilo Li1705 laptop** with **Ubuntu 9.04 Jaunty** (all updates installed, there are no proprietary drivers available to load for graphics).

The** sleep function (S3)** is working, but after I wake the laptop (by pressing the Power button) I experience every time the following: 

[LIST=1]
[*] the **TFT-LCD screen seems flickering** (viewing the TFT panel from some inches, I can see every pixel 'oscillating' (it's very annoying, the whole screen seems oscillating in one's peripheral vision, it's like the CRTs from the past with 60 Hz refresh frequency) AND
[/LIST]

[LIST=1]
[*] (at this time) when I switch to one of the virtual consoles (by pressing Ctrl+Alt+F{1..6}) **the console text on the screen is unreadable** (it flickers heavily and is distorted (like the refresh rate (frequency would be out of range ?!)).
[/LIST]
After rebooting, everything is OK until the next wake-up from sleep state. 
The laptop has **VIA VN896 integrated graphics**. 

The question is: How could be eliminated the screen flickering (in GUI and console) after resuming from S3 sleep state?  This problem affects **a huge number of users** with VIA graphics chipset.

Thanks for your help in advance.
Gabor from Hungary

---

### Post by anglergab on 2009-08-27
I'll share more details, because there was **NO reply**.

So the same problems above appeared on this laptop in other circumstances, too.

For example: 

[LIST]
[*]earlier versions of Ubuntu did not support its integrated graphics card (e. g. the **console output** was **distorted**) so the installation could not be started in the normal way. So I had to use the alternate installer disc and append parameters like ```
vga=771
``` to the kernel line at grub menu.
[*]using other Linux distros (for example **UHU Linux**, a Hungarian one), the screen is **heavily flickering** all the time (laptop TFT-LCD, 1280x800, 60 Hz set!).
[/LIST]
**Please help**, because this is the only problem that I could **not** fix myself (all other problems: vga, audio, wlan, fan control ... were solved either in the upcoming releases of Ubuntu or by myself). I had heard that this community is great...

---

### Post by anglergab on 2009-08-28
Nobody has encountered this problem?
I think that VIA graphics chipsets are quite widespread among cheaper laptops.

---

### Post by anglergab on 2009-08-31
bump

---

### Post by anglergab on 2009-09-02
I managed to solve the console text distortion problem.
I found, that when I want to use high resolution in console (the panel's native resolution is 1280x800) - by putting ```
vga=3B8
``` to the end of the kernel line at grub, at boot) the **console text distortion after suspend problem** do not appear.
However I am able to see some tiny flickering on console screen after applying the settings described above.
I tried the ```
vga=nofb
``` disable vga **framebuffer** and ```
vga=normal
``` enable framebuffer, default console resolution - kernel parameters too. But when using them, the problems appeared.

In order to eliminate the flickering in **GUI**, I added some extra options (modelines) to the **xorg.conf** file.
I added a modeline, that states the exact horizontal and vertical refresh rates (frequencies) for a laptop TFT panel with 1280x800 native resolution.
But there was no success, the problem did not disappear.

Any suggestions?
_**Could someone explain, why is my default xorg.conf nearly empty (not only on this laptop), in other words: containing no specific information, settings about my hardware? **_

---

### Post by anglergab on 2009-09-03
bump

---

### Post by anglergab on 2009-09-08
bump

---

### Post by anglergab on 2009-09-09
Please check my bug report:

[https://bugs.launchpad.net/ubuntu/+bug/tft-flickering](https://bugs.launchpad.net/ubuntu/+bug/tft-flickering)

---

### Post by anglergab on 2009-10-04
I have installed **VIA proprietary graphics driver**.
I followed the instructions from [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome).
After rebooting,** the X could not be started**, I got a warning and the full screen consoles were unreadable **exactly** in the same way, what I get after resuming from sleep.
I had to replace *xorg.conf* with the backup copy (which is minimal, it doesn't contain a *Driver* definition line in *section "Device"*).
After rebooting, everything was like before this experiment.
 
**Note:** I also tried the **latest** revision of **openchrome** graphics driver, but the original problem is not over, it appears after resuming from sleep.
 
What do you think?

---

### Post by Ruler85 on 2009-10-06
I have exactly the same laptop and the same problem... nobody out there can help us? :(

---

### Post by jflassche on 2009-11-13
I've been having the same issue ever since I got this model laptop. Two major problems:
1) text-mode flickers and renders the screen unreadable;
2) now and again the graphic modes flicker, screen remains readable though - this however disappears after some time!

Tried my best to find an videocard reset command but no luck yet. Looks to me that the problem lies there - the card needs to be reset after a wakeup.

I noticed the empty xorg.conf as well. Perhaps HAL is taking over?

---

### Post by kishanbhat on 2010-04-01
GeneralRepublic,

Thanks to your post - [http://ubuntuforums.org/showpost.php?p=8085657&postcount=4](http://ubuntuforums.org/showpost.php?p=8085657&postcount=4),  I tried "/etc/acpi/sleep.sh" when I saw incessant flickering. The  machine went into suspend mode. I woke it up and the ***flickering is  gone***!! I think lot of users are having this problem and  GeneralRepublic has an easy solution.

Otherwise it was so stressfull in seeing this flicker and keep moving  the mouse to avoid the flickering.

Xubuntu 9.10 + Fluxbox (from ubuntu rep). Compaq nc6220
*-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics  Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0

---

### Post by kishanbhat on 2010-04-01
Thanks to post - [http://ubuntuforums.org/showpost.php?p=8085657&postcount=4](http://ubuntuforums.org/showpost.php?p=8085657&postcount=4),  I tried "/etc/acpi/sleep.sh" when I saw incessant flickering. The  machine went into suspend mode. I woke it up and the ***flickering is  gone***!! I think lot of users are having this problem and  GeneralRepublic has an easy solution.

Otherwise it was so stressfull in seeing this flicker and keep moving  the mouse to avoid the flickering.

Xubuntu 9.10 + Fluxbox (from ubuntu rep).

There is help, Ruler85

---

