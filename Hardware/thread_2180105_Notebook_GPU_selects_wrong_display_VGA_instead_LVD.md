---
title: "Notebook GPU selects wrong display VGA instead LVDS1 - how can I change?"
date: 2013-10-11
forum: Hardware
---

### Post by mivogt on 2013-10-11
Hi there I nreed some help with my notebook.

[LIST]
[*]It is a maxdata belinea o.book 1
[*]The CPU is a Intel celeron  (Intel Celeron M 530 / 1.73 GHz)
[*]Chip set is via (VIA VN896)
[*]GPU is via chrome 9 (VIA Chrome9 HC)
[*]it has an internal Monitor found at LVDS-1 and an external VGA found as VGA-1.
[/LIST]

>  lspci -nnk | grep -i VGA -A2
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] [1106:3371] (rev 01)
        Subsystem: Mitac Device [1071:8515]
        Kernel modules: viafb




My problem is that after finishing the graphical installer and reboot the screen stay black and system stops.

If I attach a external VGA monitor all is fine when I reboot both screens work with best fit settings.

If I boot again and disconnect the VGA monitor all stays black again.

Meanwhile I know it is something abt the settings of xorg as there is no more an xorg.conf file.
I did a basic one and got all running in 640x480 mode on the internal display.

I need to get Ubuntu to select the lvds instead of VGA for default and use the correct settings.

Using gtf and xrandr I got the correct modline for
1280*800@60hz.

> cat xrandr-output.txt
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2047 x 2047
LVDS-1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9*+
VGA-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      60.0*+   75.0
   1024x768       75.0     70.1     60.0
   800x600        75.0     60.3
   640x480        75.0     59.9
   720x400        70.1

also
> cat gtf-output.txt

  # 1280x800 @ 59.90 Hz (GTF) hsync: 49.60 kHz; pclk: 83.32 MHz


Sadly if I insert in xorg.conf it dies not work and I still need to connect the ext VGA monitor.

I tried to add my xrandr commands into light.DM startup (see [http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent]("http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent"))

and added the

> xrandr --newmode "1280x800_60.00" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync 
xrandr --addmode LVDS-1 1280x800_60.00
xrandr --output LVDS-1 --mode 1280x800_60.00 


 and also did some grub commands to get the lvds instead of VGA for default:
> video=LVDS-1:e video=VGA-1:d
tested with and without nomodeset xforcevesa etc



All with no success so far. :(

I tried with Ubuntu and kubuntu 12.x and 13. - 

Will also try xubuntu and lubuntu as suggested.
**[COLOR="#FF0000"]Update: lubuntu seems to work but I dislike the desktop and the look and will try to add unity or xfce to the basis system[/COLOR]**

But it seems to be a software thing to select the lvds ...

Any help welcome!

Thanks.

Mike.

---

