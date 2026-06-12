---
title: "Two-finger scrolling on Asus K450LD"
date: 2015-01-20
forum: Hardware
---

### Post by Nguyen_Manh_Hieu on 2015-01-20
Hi everyone,
I'm newbie and using a Asus K450LD
My mouse has broken-down and i have using tochpad
I installed ubuntu 14.04, devices have good but still have a small bug that not using multitochpad 
i haven't exp on using terminal, i need to do something without mouse 
that my outport

~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input6
U: Uniq=
H: Handlers=rfkill kbd event5 
B: PROP=0
B: EV=100013
B: KEY=80000 0 800000000000 0 0 a1606f00900000 8200027800501000 e000000000000 0
B: MSC=10

I: Bus=0003 Vendor=0bda Product=57b4 Version=0012
N: Name="USB Camera"
P: Phys=usb-0000:00:14.0-5/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input7
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input11
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input14
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input13
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input12
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0011 Vendor=0002 Product=0001 Version=0063
N: Name="PS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input127
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

---

### Post by Pilot6 on 2015-01-20
Please give output of

dmesg | grep pnp

---

### Post by Nguyen_Manh_Hieu on 2015-01-20
> **Pilot6 said:**
> Please give output of

dmesg | grep pnp

[    0.275800] pnp: PnP ACPI init
[    0.276022] pnp 00:01: [dma 4]
[    0.276044] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.276066] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.276192] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.276418] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.276637] pnp 00:09: Plug and Play ACPI device, IDs FLT0102 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.276680] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.277817] pnp: PnP ACPI: found 14 devices

---

### Post by Pilot6 on 2015-01-20
[COLOR=#000000]You have a Focaltech touchpad.[/COLOR]
[COLOR=#000000]It is not officially supported yet. But you can insall my build from here.[/COLOR]

[https://www.dropbox.com/sh/07642x3lz...tYMoH9gka?dl=0]("https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0")

[COLOR=#000000]I recomend 3.0.16-29 version, since it is official now.[/COLOR]

---

### Post by Nguyen_Manh_Hieu on 2015-01-20
> **Pilot6 said:**
> [COLOR=#000000]You have a Focaltech touchpad.[/COLOR]
[COLOR=#000000]It is not officially supported yet. But you can insall my build from here.[/COLOR]

[https://www.dropbox.com/sh/07642x3lz...tYMoH9gka?dl=0]("https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0")

[COLOR=#000000]I recomend 3.0.16-29 version, since it is official now.[/COLOR]

How to install ???

---

### Post by Pilot6 on 2015-01-21
Download 4 deb files to your home folder and run in terminal

sudo dpkg -i linux*.deb

Then reboot.

---

### Post by Nguyen_Manh_Hieu on 2015-01-21
Can you port link into google drive ??? i can't download from dropbox
[https://www.dropbox.com/sh/07642x3lziqgmz9/AAB9jpnQY3NdSl6IEc1ISM77a/stable/3.16.0-29.39/linux-image-extra-3.16.0-29-generic_3.16.0-29.39pilot6_amd64.deb?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AAB9jpnQY3NdSl6IEc1ISM77a/stable/3.16.0-29.39/linux-image-extra-3.16.0-29-generic_3.16.0-29.39pilot6_amd64.deb?dl=0)

Thank you very much :))

---

### Post by Pilot6 on 2015-01-21
[https://drive.google.com/folderview?id=0B0dG3PkSq7CAcE9tX3ZqM3BWRzA&usp=sharing](https://drive.google.com/folderview?id=0B0dG3PkSq7CAcE9tX3ZqM3BWRzA&usp=sharing)

---

### Post by Nguyen_Manh_Hieu on 2015-01-21
After install i still can't use two-finger scroll , xiput is "PS/2 Logitech wheel trackpad" not "Focaltech"

ANYTHING ELSE ???

---

### Post by Pilot6 on 2015-01-21
This is very strange. Did you try to install any other drivers?
And give output

uname -a

---

