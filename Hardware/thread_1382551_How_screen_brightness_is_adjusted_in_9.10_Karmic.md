---
title: "How screen brightness is adjusted in 9.10 Karmic?"
date: 2010-01-16
forum: Hardware
---

### Post by Artif on 2010-01-16
What is the mechanism of backlight brighntness adjustment in Ubuntu Karmic 9.10? HAL now is not responsible and is deprecated.

The way to change brightness through command line is not ideal but good enough for me. On my laptop (Dell mini 10 with Netbook remix 9.10) during one boot perfectly works commands 
```
sudo su
echo 7 > /sys/class/backlight/compal-laptop/brightness
echo 1 > /sys/class/backlight/compal-laptop/brightness
exit

```Also I was able to adjust backlight trough Brightness applet on Gnome panel.

Now, after reboot I can't repoduce this! Now there is no files in /sys/class/backlight at all, the applet doesn't work. I played with combinations of kernel boot parameters nolapic, noapic, acpi_brightness=vendor, acpi=force trying to get functional Fn combinations but couldn't find again proper combination of boot parameters. I tried combinations mentioned in [http://ubuntuforums.org/showpost.php?p=8673113&postcount=24](http://ubuntuforums.org/showpost.php?p=8673113&postcount=24)

In Ubuntu 9.10 what to diagnose and how to get workable backlight brightness adjusment system, which have files in /sys/class/backlight ?

---

### Post by IcarusR on 2010-01-16
Have you tried...
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic acpi_backlight=vendor" 
```
As per this page..
[http://thanhsiang.org/faqing/node/142]("http://thanhsiang.org/faqing/node/142")

---

