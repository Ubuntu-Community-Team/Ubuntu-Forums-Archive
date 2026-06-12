---
title: "Cannot adjust screen brightness on laptop with Intel GM965/GL960"
date: 2009-10-31
forum: Hardware
---

### Post by flakeparadigm on 2009-10-31
I am unable to adjust the screen brightness on my laptop which has an Intel GM965/GL960 card in Ubuntu Karmic.

In Jaunty I was able to use the command "xrandr –output LVDS –set BACKLIGHT_CONTROL native" on start up, but in Karmic it quits with an error message which is at the end of this post.

Could anyone help me get this figured out? It's hard to use the laptop when the screen is "stuck" at full brightness.

xrandr output:
```
tyler@tyler-laptop:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
   Serial number of failed request:  24
  Current serial number in output stream:  24

tyler@tyler-laptop:~$ xrandr --output LVDS1 --set BACKLIGHT_CONTROL native
X Error of failed request:  BadName (named color or font does not exist)
   Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  25
  Current serial number in output stream:  25
```

lspci:
```
tyler@tyler-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
 00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
 00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
 04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by slakkie on 2009-10-31
Have you tried this:

[http://ubuntuforums.org/showthread.php?t=1217421](http://ubuntuforums.org/showthread.php?t=1217421)

---

### Post by flakeparadigm on 2009-10-31
Thank you very much! Adding "nomodeset acpi_backlight=vendor" to the "GRUB_CMDLINE_LINUX_DEFAULT" entry worked like a charm!

---

### Post by slakkie on 2009-11-01
Yw, you could have solved your problem earlier: 

[http://swiss.ubuntuforums.org/showpost.php?p=8105696&postcount=9](http://swiss.ubuntuforums.org/showpost.php?p=8105696&postcount=9)

Guess you missed my post :)

---

### Post by flakeparadigm on 2009-11-01
Oh wow, I did not even notice that there! Thanks for the help earlier on then. :D

---

