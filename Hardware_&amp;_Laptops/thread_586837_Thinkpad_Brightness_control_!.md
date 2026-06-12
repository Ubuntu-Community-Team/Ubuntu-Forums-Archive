---
title: "Thinkpad Brightness control !?"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Jingo on 2007-10-22
In Feisty I was able to adjust lcd brightness through gnome-power-manager.
In Gutsy the brightness slider is gone.

Having Thinkpad T42.

the thinkpad-acpi module is loaded and /proc/acpi/ibm/brightness is present.

What might be the problem? HAL ?

---

### Post by coondog on 2007-10-22
I also am having the same issue.

Thinkpad R40e.  

I have noticed in Screens and Graphics under Admin that my default screen is listed as "Plug 'n' Play."  Would that have anything to do with not being able to adjust brightness?

---

### Post by Jingo on 2007-10-23
I dont think so.

Brightness is not controlled via the xorg drivers. Its controlled using acpi... at least for thinkpads..

---

### Post by jamesjtucker on 2007-10-25
Thinkwiki has a workaround, not IDEAL, but it works

Nvidia Quadro N140 and 570M:

The brightness controls do not work, however you can switch to a virtual terminal (ctrl+alt+F1) increase or decrease the brightness and then switch back to X (ctrl+alt+F7) without disrupting the running applications. In a few rare cases switching back to X (ctrl+alt+7) may freeze your computer with a black screen so save any open documents before switching out. 

Thats what i am using at the moment :)

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61#Nvidia_Quadro_N140_and_570M:](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61#Nvidia_Quadro_N140_and_570M:)

---

### Post by petRUShka_sch2 on 2007-10-26
> **jamesjtucker said:**
> Thinkwiki has a workaround, not IDEAL, but it works

Nvidia Quadro N140 and 570M:

The brightness controls do not work, however you can switch to a virtual terminal (ctrl+alt+F1) increase or decrease the brightness and then switch back to X (ctrl+alt+F7) without disrupting the running applications. In a few rare cases switching back to X (ctrl+alt+7) may freeze your computer with a black screen so save any open documents before switching out. 

Thats what i am using at the moment :)

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61#Nvidia_Quadro_N140_and_570M:](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61#Nvidia_Quadro_N140_and_570M:)

look at [http://www.nvidia.com/object/linux_display_ia32_100.14.23.html](http://www.nvidia.com/object/linux_display_ia32_100.14.23.html)

> 
Version: 100.14.23
Operating System: Linux x86
Release Date: October 18, 2007

Release Highlights
[B]
    * Improved hotkey switching support for some Lenovo notebooks.[/B]
    * Improved modesetting support on Quadro FX 370, Quadro FX 570, Quadro FX 1700, Quadro NVS 320M, **Quadro FX 570M**, Quadro FX 1600M, Quadro NVS 290, Quadro NVS 140M, Quadro NVS 130M, Quadro NVS 135M, and Quadro FX 360M.
    * Fixed a problem with a Compiz after vt-switching.
    * Improved interaction with Barco and Chi Mei 56" DFPs.

I think it means that you haven't this trouble with this version of driver. I didn't install this version because  i didn't find its in repository.

---

### Post by jamesjtucker on 2007-10-26
Sweet. I am installing it now. Will post my results in a bit

---

### Post by jamesjtucker on 2007-10-26
Just installed the latest driver. No change. :(

---

### Post by schlehmil on 2007-10-30
> **Jingo said:**
> In Feisty I was able to adjust lcd brightness through gnome-power-manager.
In Gutsy the brightness slider is gone.

Having Thinkpad T42.

the thinkpad-acpi module is loaded and /proc/acpi/ibm/brightness is present.

What might be the problem? HAL ?

I have the same problem with a Thinkpad T43.
I think gnome-power-manager depends on acpi video support. The video module is loaded but the brightness interface in the proc fs is not working.

```

# cat /proc/acpi/video/VID/LCD0/brightness
<not supported>

```

Maybe this problem is related to following [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148055"). As I remember it used to work before with an older kernel.

---

