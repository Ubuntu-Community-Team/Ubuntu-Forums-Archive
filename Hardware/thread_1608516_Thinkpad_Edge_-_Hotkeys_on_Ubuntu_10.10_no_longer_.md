---
title: "Thinkpad Edge - Hotkeys on Ubuntu 10.10 no longer working"
date: 2010-10-29
forum: Hardware
---

### Post by helleste on 2010-10-29
Hello,

I installed recommended updates on my Ubuntu 10.10 yesterday, but after reboot almost all hotkeys stop working(volume, brightness, wifi controls...). Somebody with the same issue? I have Lenovo ThinkPad Edge 14".

*

Thanks for all your advices.*

---

### Post by rCXer on 2010-10-29
I had the same problem on my Edge 14. At first I thought this was an Ubuntu bug but updating BIOS fixed it.

1. Try restoring the factory settings. Enter BIOS and choose the "Setup Defaults" (F9).  
2. If that fails try updating the BIOS.

---

### Post by helleste on 2010-10-30
> **rCXer said:**
> I had the same problem on my Edge 14. At first I thought this was an Ubuntu bug but updating BIOS fixed it.

1. Try restoring the factory settings. Enter BIOS and choose the "Setup Defaults" (F9).  
2. If that fails try updating the BIOS.

You're absolutely right. I spend whole day with this issue. After updating the BIOS everything works like charm! It's a weight off my heart :)

---

### Post by helleste on 2010-11-22
I'm afraid that my problem is back. One week ago i find exactly the same issue. Hotkeys on my Thinkpad Edge  no longer working except previous track, play/pause and next track hotkey. So I downloaded new BIOS version from lenovo.com, I updated BIOS and everything worked well again. But today exactly the same problem is back. I can't update BIOS again because i already have newest BIOS version installed...I tried to do some diagnostic test like reading code from keyboard input in console. Every single key works but when i pushed my broken hotkey no code/error code there. Looks like they don't even exist! I am really desperate because of this issue...I will be very grateful for any advice  :o

---

### Post by mennowo on 2010-11-22
This may have to do with acpi settings (which control the reaction of the system to "hotkeys", fn-keybindings). To resolve this, try looking into you /etc/default/grub file, and look at the boot flags for your kernel. Updating to 10.10 may have updated you kernel, causing different kernel boot flags.

To try this out, press e in grub menu at boot, then edit the boot options according to what it should be like for your system (which I do not know). 

On my eee-pc 1101HA the relevant line in /dev/default/grub looks like:
```
GRUB_CMDLINE_LINUX="noapic acpi_osi=Linux acpi_backlight=vendor nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb"
```After editing this file, run:```
sudo update-grub
```Then reboot. Note that in the boot menu it's the acpi related flags that matter.

Hope this helps.

---

### Post by helleste on 2010-11-22
Thanks for your response. I have Ubuntu 10.10 32bit. I have Ubuntu as my default and only system so i don't have any grub menu. I tried to open /etc/default/grub file and row with GRUB_CMDLINE_LINUX is empty. 

GRUB_CMDLINE_LINUX = ""
I tried to copy & paste your settings but, of course, it didn't work.

---

### Post by mennowo on 2010-11-23
Try to put only these flags in there:

```
acpi_osi=Linux acpi_backlight=vendor
```

See if that works. If it does not, try adding this

```
acpi_skip_timer
```

Put all flags together in between "..." divided by spaces. Please note that on my eee-pc (1101HA), this last flag made the system unstable, meaning random freezes, see [this post]("http://ubuntuforums.org/showthread.php?t=1627963") for details. However, since I was unable to find much information on this issue on the internet, and the flag was added automatically, I assume it is not a regular issue, and probably depends on the hardware.

If this does not work, maybe kernel flags on your system should be different, but I do not know in what way.

---

### Post by rCXer on 2010-11-23
That's strange. The hotkeys on my Edge 14 still work but I'm using 10.04 with BIOS 1.17 (not the latest).

Did you try restoring the "Setup Defaults"?
* At Lenovo boot splash screen press Enter
* Press F1 to enter BIOS
* Press F9 to restore the "Setup Default"

Try [this](http://en.gentoo-wiki.com/wiki/Lenovo_Thinkpad_Edge_14#Hotkeys) suggestion at the Gento wiki
* Shutdown the machine
* Remove the battery
* Wait 30 seconds
* Reinstall the battery
* Turn on the machine

---

### Post by helleste on 2010-11-23
Thanks for your advices guys. I tried to "Setup defaults" and i have no luck... It seems like that i have to use my warranty :) 

I have exactly the same problem on Windows 7 with every single Lenovo driver crap installed.

---

