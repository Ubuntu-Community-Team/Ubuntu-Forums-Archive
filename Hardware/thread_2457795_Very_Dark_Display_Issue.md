---
title: "Very Dark Display Issue"
date: 2021-02-09
forum: Hardware
---

### Post by linusband on 2021-02-09
Hi Everyone!

I installed Ubuntu 20.4 on an old laptop, Toshiba Satellite L-50-C-1GX, but am having an issue with the display. The laptop screen is very very dark, making it nigh impossible to see anything on it. Connecting an external monitor has allowed me to try some fixes that I found, but none have been successful, unfortunately

I've tried rebooting a few times while holding shift and F5 and I've tried editing my grub file, as per other posts I found on the Ubuntu Forums ([here]("https://ubuntuforums.org/showthread.php?t=1811647&highlight=dark+screen") and [here]("https://ubuntuforums.org/showthread.php?t=1789447&page=2")):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\" acpi_backlight=vendor"
```
This did not work. I've also tried it without quotation marks around Linux, but to no avail.

Important to note is that when I power up the laptop, "Toshiba: Leading Innovation" is shown at normal brightness, but after a few moments the screen is updated to also include "Ubuntu" at the bottom of the screen and the loading icon. As soon as this change occurs, the screen goes to very dark.

My apologies if this is a dumb question and/or if I missed some obvious fix. I really hope to get the working again, as it would be a waste to throw away a laptop that still works well otherwise.

---

### Post by CelticWarrior on 2021-02-09
How does it behave in BIOS/UEFI?

---

### Post by linusband on 2021-02-09
If I press F2 on startup it directs me to the Toshiba Setup Utility. That is shown in normal brightness.

EDIT: It seems that Toshiba Setup Utility is my UEFI. I selected UEFI from the GRUB screen and it redirected me to it.

---

### Post by CelticWarrior on 2021-02-09
OK, so it's likely a software (OS) issue but first, when at the firmware settings (UEFI - "Toshiba Setup Utility") search for brightness settings. If found try increasing the value. If there isn't such setting it means the brightness is controlled entirely by the OS -> Try increasing the brightness using the Ubuntu's (Gnome) brightness setting.

---

### Post by linusband on 2021-02-09
Okay, I re-checked the UEFI, and there are no brightness settings there. Also, Ubuntu's brightness setting says it's already at its brightest, irregardless of whether I open it on my faulty laptop screen or the correctly bright secondary one.

**EDIT**: I've also tried re-installing Ubuntu 18.04 instead. During installation the screen was fine and as bright as it should be. Post-restart, after the installation was done, I'm back with my very VERY dark screen...
**EDIT2**: I've also tried creating a [COLOR=#333333][FONT=monospace]/usr/share/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]X11/xorg.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]conf.d/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]20-intel.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]conf[/FONT][/COLOR] file, as per this [suggestion]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1249219/comments/30"). I tried this, because the buttons for adjusting the brightness do indicate on screen that it should be increasing or decreasing, but does nothing. So, the laptop screen remains dark and the second screen remains bright.

Perhaps it would help if you knew my graphic card settings?
```
sudo lshw -C display
 *-display                
      description: VGA compatible controller
      product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
      vendor: Intel Corporation
      physical id: 2
      bus info: pci@0000:00:02.0
      version: 21
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi vga_controller bus_master cap_list rom
      configuration: driver=i915 latency=0
      resources: irq:124 memory:90000000-90ffffff memory:80000000-8fffffff ioport:2000(size=64) memory:c0000-dffff
```

**EDIT3**: I've tried it through a script containing ```
echo $1 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
This didn't work either.

---

