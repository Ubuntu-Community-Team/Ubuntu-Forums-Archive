---
title: "Samsung 730U AMD Graphic Card Driver Issue"
date: 2019-10-13
forum: Hardware
---

### Post by nowdyle on 2019-10-13
Hello,
I have problem at my laptop. My GPU not working, i think it's not supported anymore from AMD. How can I handle these problem ? 
My computer is Samsung 730u3e.Amd not show x64 driver on your drivers list.
Thanks for your advice.):P

```
sudo lspci -nn | grep -E 'VGA|Display'
```
> 200:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
[COLOR=#ff0000]**01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] [1002:6601]**[/COLOR]

```
dmesg
```
> [ 3762.505420] radeon 0000:01:00.0: failed VCE resume (-110).
[ 3762.586446] r8169 0000:03:00.0 enp3s0: Link is Down
[ 3762.613557] usb 1-1.4: reset high-speed USB device number 3 using ehci-pci
[ 3762.613571] usb 2-1.5: reset full-speed USB device number 3 using ehci-pci
[ 3762.621777] usb 3-3: reset high-speed USB device number 2 using xhci_hcd
[ 3762.655090] [drm] ring test on 0 succeeded in 1 usecs
[ 3762.655094] [drm] ring test on 1 succeeded in 1 usecs
[ 3762.695811] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[ 3762.696017] ata1.00: configured for UDMA/133
[ 3763.826509] [drm:uvd_v1_0_start [radeon]] *ERROR* UVD not responding, trying to reset the VCPU!!!
[ 3764.841866] [drm:uvd_v1_0_start [radeon]] *ERROR* UVD not responding, trying to reset the VCPU!!!
[ 3765.857212] [drm:uvd_v1_0_start [radeon]] *ERROR* UVD not responding, trying to reset the VCPU!!!

```
lsb_release -a
```
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic


---

### Post by mikewhatever on 2019-10-14
Try this: [https://askubuntu.com/questions/717504/errors-error-uvd-not-responding-trying-to-reset-the-vcpu](https://askubuntu.com/questions/717504/errors-error-uvd-not-responding-trying-to-reset-the-vcpu)

---

