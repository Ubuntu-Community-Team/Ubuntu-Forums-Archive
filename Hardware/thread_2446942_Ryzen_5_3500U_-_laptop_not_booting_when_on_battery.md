---
title: "Ryzen 5 3500U - laptop not booting when on battery power"
date: 2020-07-09
forum: Hardware
---

### Post by mastablasta on 2020-07-09
So we got a new laptop (HP 255 G7) for the kid (i mean he saved up the money i helped to select it). I tested most hardware so far. We installed CS:GO, Portal and Gary's mod and all works fine. i also installed a few apps to test mic and camera.

But, and this is the puzzling part, i can't boot it with battery only. When the power is in it boots fine and fast, but with battery i get garbled desktop (attachment - kde wallet window is visible and panel) as if drivers aren't loaded. And looks like there really is an issue with drivers of sorts. I can still enter password for KDE walled and the laptop connects to wi-fi. i can attach mouse and i still get the message that touchpad was turned off (though not visible as only frame of message windows is displayed). I managed to get it to boot correctly once and 8 times it failed. Since i can switch normally to console and back i decided to move dmesg to a file.

dmesg: [https://paste.ubuntu.com/p/C2xNzpBKq5/](https://paste.ubuntu.com/p/C2xNzpBKq5/)

Dmesg throws out error messages as if it tried to load the driver but can't do it fully.

system specs:
OS: Kubuntu 20.04

CPU: Ryzen 5 3500U
GPU: Vega 8
RAM: 8 GB DDR4 2400 Mhz
disk: 256 GB nvme

other:
[LIST]
[*]wi-fi driver (rtl8821ce) is not in kernel, so i needed patch and i used this procedure: [https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04](https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04) 
[*]USB ports, network jack, audio stuff, camera, touchpad (synaptics) all work 
[*]legacy boot was default so i left it alone 
[*]install is default, whole disk used (swap is file) 
[*]after multiple boot failures i enabled battery report to OS in BIOS, but all it did is that OS now reports remaining battery time left. 
[*]if i boot with charger plugged in, the laptop boots normally and seems to be working normally after i unplug the charger. 
[*]plymouth screen works normally, but KDE loading screen does not display 
[/LIST]

how do i troubleshoot this? moreover how can i fix it?

---

### Post by mastablasta on 2020-07-11
I found a work around solution. The issue is indeed AMD drivers for Ryzen 5 3500U and Vega 8.
a boot option is needed: 
```
iommu=soft 
```

To try if this works hold shift on boot to enter grub, press e, then add this boot option just before the quiet splash. then press ctrl+x to boot. if it doesn't work well, hust reboot

Some things might be disabled when using this boot option . iommu has effect on these things: [https://github.com/spotify/linux/blob/master/Documentation/x86/x86_64/boot-options.txt#L207](https://github.com/spotify/linux/blob/master/Documentation/x86/x86_64/boot-options.txt#L207)
Some people reported USB3 ports not working or other external connections. in my case all seems to work as well as GPU (i could play CS:GO normally on battery).

to make it permanent edit grub configuration file.

```
sudo nano /etc/defaut/grub 
```

change line 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
```
to 
```
GRUB_CMDLINE_LINUX_DEFAULT="iommu=soft quiet splash" 
```

save the file, exit nano editor and run the update to grub:
```
sudo update-grub
```

The issue affects other laptops with Ryzen 5 3500U and is reported to be resolved in kernel 5.5, while the GPU drivers improvement (power management, fans...) is part of kernel 5.6.

By installing new kernel the issue should be resolved. 

**[SIZE=3][COLOR=#ff0000]WARNING: new kernels are not fully tested and come without extra drivers that ubuntu adds.[/COLOR][/SIZE]**

How to install new kernel:
You can use graphics app ukuu (Ubuntu Kernel Update Utility) to install new mainline kernel. instructions: [https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)

another option is described here: [https://howtoubuntu.org/how-to-install-linux-kernel-5-6-in-ubuntu](https://howtoubuntu.org/how-to-install-linux-kernel-5-6-in-ubuntu)
kernels (.deb files) can be found here: [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

removing kernel - if it's not working:
procedure is well described here: [https://karlcode.owtelse.com/blog/2017/03/13/reverting-to-a-previous-kernel/](https://karlcode.owtelse.com/blog/2017/03/13/reverting-to-a-previous-kernel/)

---

