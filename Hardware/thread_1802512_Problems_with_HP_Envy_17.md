---
title: "Problems with HP Envy 17"
date: 2011-07-12
forum: Hardware
---

### Post by alexthunder on 2011-07-12
1. Problems with booting: Ubuntu 10.10 was booting, but Ubuntu 11.04 and 11.10 alfa 2 freezed on booting.

Kubuntu 11.04 boots just fine. 

2. The LCD backlight dims after restarting.
Wireless turns on after restarting (no matter wether it was on or off).

3. Clickpad multi-touch does not work. Tried to install the fix
[https://launchpadlibrarian.net/60964128/synaptics-dkms_1.1.1_all.deb](https://launchpadlibrarian.net/60964128/synaptics-dkms_1.1.1_all.deb)
but it didn't install.

4. Clickpad disable does not work

---

### Post by alexthunder on 2011-10-14
I installed Lubuntu 11.04 and was able to boot several times. But then it started freezing again.

Ububtu 11.10 doesn't solve the problem for me. I can boot from a Live CD without any problem, surf the net from it. Installation goes on smoothly, but after first restart my HP Envy freezes, the screen flashes slightly.

I don't really understand why live CDs always work for me, but I can't install and run Ubuntu properly. Any idea how to make the latest versions of Ubuntu to work on my laptop?

---

### Post by alexthunder on 2011-10-16
Tried Ubuntu, KUbuntu, LUbuntu, XUbuntu 11.10, and all of them have the same problem. This seems to be related to the latest kernel. I wonder whether I can add an older kernel to the installed version or not.

---

### Post by alexthunder on 2011-12-14
Linux Mint 11 was working fine for me. When I updated it to Linux Mint 12, I started having the same problem. It seems to be related to the latest version of the kernel.

My Ati Radeon 5850 started having problems with the kernels 2.6.38 and higher. And it has always failed with any 3.x version of the kernel.

Tried installing the latest alfa of Ubuntu 12.04 today and had the same problem. The screen becomes black after rebooting. Sometimes it flashed. The recovery mode doesn't help.

Somehow I managed to boot in Ubuntu 11.10 in the recovery mode after several attempts. Downloaded kernels 2.6.37, 2.6.38, 2.6.39. I was able to boot with 2.6.37 only. The only problem is that this kernel doesn't seem to be compatible with Ubuntu 11.10, because I was offered to upgrade the OS during which the 2.6 kernel was supposed to be removed.

I downloaded [AMD Catalyst Proprietary Display Driver (Linux x86 & Linux x86_64)](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=us&rev=10.10&ostype=Linux%20x86_64) v. 10.10 and installed it. After that Ubuntu 11.10 started working just fine.

---

### Post by alexthunder on 2012-04-29
Upgraded to Ubuntu 12.04. Ubuntu didn't boot (don't even remember when my last successful Ubuntu upgrade was). Formatted my HDD and re-installed. Booted without any problem. However I can't suspend my PC. And I get black screen after rebooting. If I restart my computer I get a disk check and can boot again. Then after shutting down or rebooting Ubuntu freezes again :(

As for the screen brightness, it can be fixed by adding the following to grub:
```
video.use_bios_initial_backlight=0
```

---

