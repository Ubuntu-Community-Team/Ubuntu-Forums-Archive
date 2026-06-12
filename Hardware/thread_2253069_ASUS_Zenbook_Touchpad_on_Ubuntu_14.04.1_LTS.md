---
title: "ASUS Zenbook Touchpad on Ubuntu 14.04.1 LTS"
date: 2014-11-17
forum: Hardware
---

### Post by ehsan3 on 2014-11-17
I just installed Ubuntu 14.04.1 on ASUS Zenbook. It seems that the touchpad is not recognized.

In file /proc/bus/input/devices, there is no word "pad". The word "mouse", however, appears three times:

> 

I: Bus=0003 Vendor=03eb Product=8a32 Version=0111
N: Name="Atmel Atmel maXTouch Digitizer"
P: Phys=usb-0000:00:14.0-7/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input14
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=260800000000003

...

I: Bus=0011 Vendor=0002 Product=0001 Version=0063
N: Name="PS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input11
U: Uniq=
H: Handlers=mouse1 event14 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3



Could you please let me know how I can install suitable touchpad driver? Currently, the touchpad doesn't work well (some functionalities don't work at all). Thanks a lot in advance.

---

### Post by Pilot6 on 2014-11-17
You have a new Focaltech touchpad. It is not supported by the kernel yet. But the driver is ready and I made a kernel image with the driver installed.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Install these debs and touchpad will work.

---

### Post by ehsan3 on 2014-11-17
Thank you very much. It works (after restarting) ;)

> **Pilot6 said:**
> 
You have a new Focaltech touchpad. It is not supported by the kernel yet. But the driver is ready and I made a kernel image with the driver installed.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Install these debs and touchpad will work.


---

### Post by microUgly on 2014-11-22
Is this kernel advisable for Mint users?

I have a ZenBook ux303ln running Mint 17 and the kernel is currently at 3.13.

I have only had the laptop for a few days, but am seriously missing being able to touchpad scroll :)

---

### Post by Pilot6 on 2014-11-22
> **microUgly said:**
> Is this kernel advisable for Mint users?

I have a ZenBook ux303ln running Mint 17 and the kernel is currently at 3.13.

I have only had the laptop for a few days, but am seriously missing being able to touchpad scroll :)
There is no difference. Mint uses same kernels.

---

### Post by microUgly on 2014-11-22
Thank you so much, Pilot6.  Your kernel seems to work perfectly.

There was a couple of message during the installation that you might be interested in:
```
$ sudo dpkg -i linux-headers-*.deb linux-image-*.deb
Selecting previously unselected package linux-headers-3.16.7-focaltech3+bt2+.(Reading database ... 159180 files and directories currently installed.)
Preparing to unpack linux-headers-3.16.7-focaltech3+bt2+_3.16.7-focaltech3+bt2+-10.00.Custom_amd64.deb ...
Unpacking linux-headers-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...
Selecting previously unselected package linux-image-3.16.7-focaltech3+bt2+.
Preparing to unpack linux-image-3.16.7-focaltech3+bt2+_3.16.7-focaltech3+bt2+-10.00.Custom_amd64.deb ...
Done.
Unpacking linux-image-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...
Setting up linux-headers-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
Error! echo
Your kernel headers for kernel 3.16.7-focaltech3+bt2+ cannot be found at
/lib/modules/3.16.7-focaltech3+bt2+/build or /lib/modules/3.16.7-focaltech3+bt2+/source.
Error! echo
Your kernel headers for kernel 3.16.7-focaltech3+bt2+ cannot be found at
/lib/modules/3.16.7-focaltech3+bt2+/build or /lib/modules/3.16.7-focaltech3+bt2+/source.
Setting up linux-image-3.16.7-focaltech3+bt2+ (3.16.7-focaltech3+bt2+-10.00.Custom) ...


 Hmm. There is a symbolic link /lib/modules/3.16.7-focaltech3+bt2+/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/3.16.7-focaltech3+bt2+/build




 Hmm. The package shipped with a symbolic link /lib/modules/3.16.7-focaltech3+bt2+/source
 However, I can not read the target: No such file or directory
 Therefore, I am deleting /lib/modules/3.16.7-focaltech3+bt2+/source


Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
Error! Bad return status for module build on kernel: 3.16.7-focaltech3+bt2+ (x86_64)
Consult /var/lib/dkms/virtualbox-guest/4.3.10/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
update-initramfs: Generating /boot/initrd.img-3.16.7-focaltech3+bt2+
Warning: No support for locale: en_AU.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.7-focaltech3+bt2+ /boot/vmlinuz-3.16.7-focaltech3+bt2+
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.7-focaltech3+bt2+
Found initrd image: /boot/initrd.img-3.16.7-focaltech3+bt2+
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
  No volume groups found
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```

Is this scheduled for an official release?  I read that 3.18 would include FocalTech improvements, so I tried it and it made no difference.

---

### Post by Pilot6 on 2014-11-22
These messages are OK for a custom kernel.

It is not in 3.18 yet. And I am not sure it will be. Probably it will be applied in 3.19.
I will try to keep ubuntu kernel 3.16 up to date.

---

### Post by dab77 on 2014-11-29
Hi I would like to thank you very much for this solution which worked also for me.
It's 2 months that I'm getting mad in trying to make the touchpad work.
Now it works as expected, although the broadcom wifi doesn't anymore... but i'll find a solution.

Asus K550JK-XO002H.

---

### Post by dab77 on 2014-11-29
Hi, unfortunately I cannot bring my Broadcom Wireless to work with your kernel.
The dkms command fail to build some modules:```
dab@dab-lab ~ $ cat /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/make.log
DKMS make.log for bcmwl-6.30.223.141+bdcom for kernel 3.16.0-26-generic (x86_64)
dom 30 nov 2014, 01.33.03, CET
make: Entering directory `/usr/src/linux-headers-3.16.0-26-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function ‘wl_cfg80211_get_key’:
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1383:2: warning: passing argument 1 of ‘memcpy’ discards ‘const’ qualifier from pointer target type [enabled by default]
  memcpy(params.key, key.data, params.key_len);
  ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/include/linuxver.h:40,
                 from /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:26:
./arch/x86/include/asm/string_64.h:32:14: note: expected ‘void *’ but argument is of type ‘const u8 *’
 extern void *memcpy(void *to, const void *from, size_t len);
              ^
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: At top level:
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1593:2: warning: initialization from incompatible pointer type [enabled by default]
  .get_station = wl_cfg80211_get_station,
  ^
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1593:2: warning: (near initialization for ‘wl_cfg80211_ops.get_station’) [enabled by default]
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function ‘wl_notify_connect_status’:
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1844:4: warning: passing argument 3 of ‘cfg80211_ibss_joined’ makes pointer from integer without a cast [enabled by default]
    cfg80211_ibss_joined(ndev, (u8 *)&wl->bssid, GFP_KERNEL);
    ^
In file included from /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:33:0:
include/net/cfg80211.h:4002:6: note: expected ‘struct ieee80211_channel *’ but argument is of type ‘unsigned int’
 void cfg80211_ibss_joined(struct net_device *dev, const u8 *bssid,
      ^
/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:1844:4: error: too few arguments to function ‘cfg80211_ibss_joined’
    cfg80211_ibss_joined(ndev, (u8 *)&wl->bssid, GFP_KERNEL);
    ^
In file included from /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:33:0:
include/net/cfg80211.h:4002:6: note: declared here
 void cfg80211_ibss_joined(struct net_device *dev, const u8 *bssid,
      ^
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.141+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.16.0-26-generic'
dab@dab-lab ~ $ 


```

And I don't know how to solve that. Also Nvidia and Virtualbox Modules fail to build.

Broadcom model:```
dab@dab-lab ~ $ lspci -vnn | grep Network
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)


```

Thank you, Davide.

---

### Post by Pilot6 on 2014-11-30
The problem is that this version of bcmwl-kernel-source is not building with 3.16 kernel. They will fix it soon as 3.16 kernel is already in 14.04 repos as lts-utopic.

You can install this package from 14.10.
[http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

It should work.

---

### Post by dab77 on 2014-12-01
Thank you. not that, but the very latest revision of that packed installed and worked like a charm.
I Appreciated a lot.
Davide

---

### Post by vic202 on 2014-12-05
I can't seem to find many other comments regarding other models of Asus laptops with Focaltech pads installed.

I have an X550CA - it identifies as a Focaltech touchpad using the pnp grep command but the various patched kernels don't work (I've tried Pilot6's kernels and a 3.17.2 kernel from the launchpad tracker).

3.18 with the protobare command sees the touchpad work as PS2 mouse but the proper solutions don't seem to work - does anyone have any ideas?

Thanks guys!

---

### Post by Pilot6 on 2014-12-05
> **vic202 said:**
> I can't seem to find many other comments regarding other models of Asus laptops with Focaltech pads installed.

I have an X550CA - it identifies as a Focaltech touchpad using the pnp grep command but the various patched kernels don't work (I've tried Pilot6's kernels and a 3.17.2 kernel from the launchpad tracker).

3.18 with the protobare command sees the touchpad work as PS2 mouse but the proper solutions don't seem to work - does anyone have any ideas?

Thanks guys!

Focaltech touchpad support is not in any official kernel yet. Did you try my build of 3.16.0-26.35 kernel? Try it. It should work.

---

### Post by vic202 on 2014-12-05
Hi - and many thanks for replying!

I've tried a variety of patched kernels and I'm currently on yours! The patches mean that the touchpad actually shows up in the settings menu, but is still unresponsive.

I've seen elsewhere adding the i8042.noloop=1 command may help, but it hasn't for me... the only way I can currently enable the pad is by using the psmouse.proto=bare command, which means it has basic functionality.

Any assistance would be greatly appreciated!

---

### Post by Pilot6 on 2014-12-05
Please give output

dmesg | egrep 'pnp|i8042'

And also try to add i8042.nomux=1 i8042.noloop=1 

to /etc/default/grub

And do not forget to do
sudo update-grub

after that.

---

### Post by vic202 on 2014-12-05
Thanks again... no luck with adding i8042.nomux=1 i8042.noloop=1

output from dmesg | egrep 'pnp|i8042' - 

```
$ dmesg | egrep 'pnp|i8042'
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-26-generic root=UUID=ac58ad61-f418-4f16-b10b-5991cae67b15 ro i8042.nomux=1 i8042.noloop=1 quiet splash vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-26-generic root=UUID=ac58ad61-f418-4f16-b10b-5991cae67b15 ro i8042.nomux=1 i8042.noloop=1 quiet splash vt.handoff=7
[    0.261549] pnp: PnP ACPI init
[    0.261921] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.262138] pnp 00:05: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.262193] pnp 00:06: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.262761] pnp: PnP ACPI: found 10 devices
[    0.780320] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.781601] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.781609] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.866506] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.969178] input: FocalTechPS/2 FocalTech FocalTech Touchpad as /devices/platform/i8042/serio1/input/input5
```

---

### Post by Jane_Says on 2014-12-17
The same problem appears to exist in the new line of Transformer books also.  I have the TP300LA and it has two components that do notwork OOB in Linux.  It does not have wired ethernet connectivity and the Wireless 7260 does not work on the 14.10 installer.  The same with the FocalTech touchpad.  The easy solution to the former was to go to the newest mainline kernel and 3.18 fixes it.  But the FocalTech behaves like nothing more than a mouse.  My dmesg is the same as that above except for the last line 

[COLOR=#000000]it shows as a PS/2 Logitech Wheel Mouse as the flags detect and reroute it in the current kernel patches.  Perhaps the FocalTech driver will enter stream at some point.  For now, the touchscreen functionality combined with the wireless is workable but the touchpad would be really nice.[/COLOR]

---

### Post by zakoyan on 2014-12-17
I am here also to thank you ) your custom kernel did the thing with my Asus X553M touchpad, too. What I've lost is my panel element ponting to network settings, but is much less sensitive lost than the touchpad prtending to be a mouse) Thank you so much.

---

### Post by Pilot6 on 2014-12-17
Network settings have nothing to do with the kernel. Probably you edited /etc/network/interfaces.

---

### Post by zakoyan on 2014-12-17
I've been dumb. Just restored the network and sound volume pics in the panel (I am on Xubuntu)

---

### Post by zakoyan on 2014-12-17
No, I did nothing but instolling thak kernel of yours from Dropbox. Some mystery ) but by now everything is brilliant. Thank you once again.

---

### Post by Chloe_Thomas on 2015-01-19
Hi everybody,

I am new on that forum. I am French but unfortunately I didn't find any solution on the French forum.
I recently bought an Asus notebook (r409lc-wx118h) and I've removed completely Windows 8 to install Ubuntu 14.04.
I  managed the installation but I've got some problems with my touchpad:  it works but my laptop doesn't recognize it. When I have a look on the  parameters, the touchpad is not detected. In fact the touchpad only  works when I use one finger but it doesn't work as a multi-touch pad.
Moreover, after putting my laptop on standby mode, the touchpad doesn't work at all.

I  had a look on this forum page and I read that it is recommended to  install a driver, but I don't know what type of touchpad it is  (Elantech, or Folantech...)

Maybe someone has the same laptop and has solved this problem.

Thank you in advance,

Chloe

---

### Post by Pilot6 on 2015-01-19
Please give output of

dmesg | grep pnp

And I will tell you which touchpad you have.

---

### Post by Chloe_Thomas on 2015-01-19
Thank you for quick reply !

Here is the output :

[    0.281253] pnp: PnP ACPI init
[    0.281463] pnp 00:01: [dma 4]
[    0.281485] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.281508] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.281645] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.281885] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.282122] pnp 00:09: Plug and Play ACPI device, IDs FLT0102 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.282167] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.283299] pnp: PnP ACPI: found 14 devices

---

### Post by Pilot6 on 2015-01-19
You have a Focaltech touchpad.
It is not officially supported yet. But you can insall my build from here.

[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

I recomend 3.0.16-29 version, since it is official now.

---

### Post by Chloe_Thomas on 2015-01-19
Thank you very much, I am going to try now and I'll tell you how it works.

What is the difference between linux-headers and linux-image ? I am not sure which one I have to install..

---

### Post by Pilot6 on 2015-01-19
You need to install all 4 deb files.
Just download them to your home folder and run 

sudo dpkg -i linux*.deb

---

### Post by Chloe_Thomas on 2015-01-19
I installed it, it works perfectly now !
Thank you very much

---

### Post by jhewat34 on 2015-01-23
Pilot6, you are my hero right about now! I bought an ASUS X553M a few months ago that has been gathering dust ever since due to the touchpad issue (bought it for typing University work, but with no 'disable touchpad while typing' option it was pretty much useless for that purpose). Thanks a lot!

---

### Post by Sebastian_Nilsson on 2015-01-23
Hello. 
I've recently installed Ubuntu 14.04 on my Asus F550LN (it has a Focaltech touchpad) and I haven't been able to get my touchpad working at all. I've tried installing some of your kernel builds but to no avail. I should say that I'm very new to Ubuntu and Linux in general. 
Any help would be greatly appreciated.

---

### Post by Pilot6 on 2015-01-24
Sebastian,

There may be 3 reasons why your touchpad does not work.

1. You installed the kernel not correctly or boot in another kernel.
Look at output of
uname -a
and check.

2. You tried to install Elantech driver.

You can see it by

dkms status

3. It just does not work. Yhis driver does not work on some models. It is not known why yet.

---

### Post by Sebastian_Nilsson on 2015-01-24
Thank you for the quick reply! 

This is the output from the first command and it looks correct to me:
> Linux sebastian-X550LN 3.16.0-29-generic #39 SMP Tue Dec 16 13:15:25 MSK 2014 x86_64 x86_64 x86_64 GNU/Linux

The output from dkms status is the following:
> bbswitch, 0.7, 3.13.0-44-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-29-generic, x86_64: installed
nvidia-340, 340.65, 3.16.0-29-generic, x86_64: installed
nvidia-340-uvm, 340.65, 3.16.0-29-generic, x86_64: installed

Says nothing about Elantech or Focaltech, am I missing something?

---

### Post by Pilot6 on 2015-01-25
It looks OK. Then probably your model is not supported yet.

---

### Post by Sebastian_Nilsson on 2015-01-25
> **Pilot6 said:**
> It looks OK. Then probably your model is not supported yet.

That's a shame. Not sure if I should go back to Windows or if I should get a wireless mouse for now. Thank you for your time, you've been of great help to lots of people here!

---

### Post by Pilot6 on 2015-01-25
But are you sure you have a Focaltech?

---

### Post by Sebastian_Nilsson on 2015-01-25
> **Pilot6 said:**
> But are you sure you have a Focaltech?

Pretty sure, yes. Output of xinput list is:

> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; FocalTechPS/2 FocalTech FocalTech Touchpad    id=14    [slave  pointer  (2)]
&#9116;   &#8627; Thermaltake USB Gaming Mouse                id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]



---

### Post by syver.enstad on 2015-01-26
Fantastic, works on my Asus X555LA too

---

### Post by ankout on 2015-01-28
Bonsoir

I also just install a Ubuntu 14.04 on an Asus UX303LN-4023, and, surprise, the touchpad doesn't work!

I try to install the latest debs from Pilot6 dropbox, but the terminal tells me that this is not a valid debian packet...

```
~/Bureau/focaltech/test-2$ sudo dpkg -i linux*.deb
dpkg-deb : erreur : `linux-headers-3.16.0-28_3.16.0-28.38pilot6_all.deb » n'est pas une archive de format Debian   /* Is not a debian format archive */
dpkg: error processing archive linux-headers-3.16.0-28_3.16.0-28.38pilot6_all.deb (--install):
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2                                                      /* sub-process dpkg-deb --control returns error 2 */
dpkg-deb : erreur : `linux-headers-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb » n'est pas une archive de format Debian
dpkg: error processing archive linux-headers-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb (--install):
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
dpkg-deb : erreur : `linux-image-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb » n'est pas une archive de format Debian
dpkg: error processing archive linux-image-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb (--install):
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
dpkg-deb : erreur : `linux-image-extra-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb » n'est pas une archive de format Debian
dpkg: error processing archive linux-image-extra-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb (--install):
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution :
 linux-headers-3.16.0-28_3.16.0-28.38pilot6_all.deb
 linux-headers-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb
 linux-image-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb
 linux-image-extra-3.16.0-28-generic_3.16.0-28.38pilot6_amd64.deb


```

Sorry it's in french, but I guess you understand...

uname -a
```
Linux tang-laptop 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

 dmesg | grep pnp
```
[    0.252503] pnp: PnP ACPI init
[    0.252686] pnp 00:01: [dma 4]
[    0.252705] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.252725] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.252849] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.253070] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.253277] pnp 00:09: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.253322] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.254390] pnp: PnP ACPI: found 13 devices
```

What may be the trouble (in addition of me ;) )

Thanks in advanced

L'Ankou

---

### Post by Pilot6 on 2015-01-28
Try to install 2.6.0-29.39. This is latest stable. But they installed OK. Noone complained.
But delete 28.38 debs from your home directory first.

---

### Post by Pilot6 on 2015-01-28
I checked it. The package is OK. Maybe you downloaded it with errors.

---

### Post by ankout on 2015-01-28
Thanls for your prompt reply!!

Did you mean 3.16.0-29.39? It is the only one I can see here : [https://www.dropbox.com/sh/07642x3lziqgmz9/AADmz5pR4X5ZTfRSDKmeDZo_a/stable?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AADmz5pR4X5ZTfRSDKmeDZo_a/stable?dl=0)

I just delete all the previously DL packages

---

### Post by Pilot6 on 2015-01-28
Right. That was a typo. Fixed it.

---

### Post by ankout on 2015-01-28
same error again :

```
sudo dpkg -i linux*.deb
[sudo] password for tang: 
dpkg-deb : erreur : `linux-headers-3.16.0-29_3.16.0-29.39pilot6_all.deb » n'est pas une archive de format Debian
dpkg: error processing archive linux-headers-3.16.0-29_3.16.0-29.39pilot6_all.deb (--install):
 le sous-processus dpkg-deb --control a retourné une erreur de sortie d'état 2
dpkg-deb : erreur : `linux-headers-3.16.0-29-generic_3.16.0-29.39pilot6_amd64.deb » n'est pas une archive de format Debian
```

This time I try from /home/, before I was in a desktop folder, but it doesn't seem to change anything...

---

### Post by Pilot6 on 2015-01-28
I have no idea why it does not install. I just checked and it installs.

---

### Post by ankout on 2015-01-28
Is it because I am running a 3.13 kernel? 
I have only install nvidia drivers (from repos), virtualbox and that's all... almost fresh install...

EDIT : 
I just checked with sudo su, no change

---

### Post by Pilot6 on 2015-01-28
No. It does not matter which version is already installed.

---

### Post by Pilot6 on 2015-01-28
Let me download them and check. Maybe some problem with dropbox.

---

### Post by Pilot6 on 2015-01-28
No. Just downloaded and installed.

---

### Post by Pilot6 on 2015-01-28
The only guess maybe that something corrupts files while download.

---

### Post by Pilot6 on 2015-01-28
I put md5sum file there. Check.

---

### Post by ankout on 2015-01-28
Oops, I think I found!

I did right clic/save as... I got files named ***.deb, but they sure were not deb at all :S

I DL it the right way, and I come back after trying... Shouldn't have taste this old rum tonight.... ;)

---

### Post by ankout on 2015-01-28
OK, it installs!

But I get the error (extract):
```
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
Error! Bad return status for module build on kernel: 3.16.0-29-generic (x86_64)
Consult /var/lib/dkms/nvidia-331-uvm/331.113/build/make.log for more information.
Paramétrage de linux-image-3.16.0-29-generic (3.16.0-29.39pilot6) ...
Running depmod.
```

I try to reboot, lets see :)

Many thanks anyway, one beer for you if you come next to Marseille :)

---

### Post by ankout on 2015-01-28
OK, it works, great, but it is not fluent at all, I think there's something wrong with nvidia, I got a crash at first reboot when I tried to move the pointer very fast.

The mouse is really slow, in fact the speed setting in Parameters seems ineffective.

---

### Post by Pilot6 on 2015-01-29
Nvidia driver did not install correctly. Try to reinstall it from official repos.

---

### Post by luk5 on 2015-02-10
Hi,

I am experiencing same issue with ASUS X550CL.
Installed recommended kernel and there are two major differences:
1. bluetooh mouse is now working correctly (previously it was working ok only in active window)
2. touchpad does not work at all (previously pointer moved randomly little bit when sliding on touchpad. Now it does not and once computer is started there is no pointer at all until I move the mouse)

I was wandering that maybe it is somehow disabled but tried combination of Fn+F9 and it does not change anything.

Any ideas what could went wrong?

Thanks in advance!
Luk

---

### Post by Pilot6 on 2015-02-10
luk5,

Please give output of

dmesg grep serio

But the touchpad still does not work on some models for some reason.

---

### Post by luk5 on 2015-02-10
here is it: 

```
[  877.900934] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  878.507739] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  879.106654] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  879.706650] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  880.304673] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  880.904186] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  881.503255] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  882.102449] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  882.711984] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  883.311408] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  883.910966] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  884.510888] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  885.109909] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  885.708549] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  886.308413] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  886.918577] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  887.516753] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  888.116565] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  888.716799] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  889.315342] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  889.914818] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  890.514143] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  891.122976] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  891.722374] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  892.320542] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  892.921582] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  893.519516] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  894.119132] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  894.717646] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  895.323892] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  895.921241] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  896.520716] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  897.120253] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  897.719423] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  898.318331] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  898.917594] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  899.527329] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  900.126082] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  900.725124] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  901.324179] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  901.922585] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  902.522865] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  903.122120] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  903.731488] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  904.330519] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  904.930531] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  905.530076] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  906.129549] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  906.728568] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  907.326814] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  907.935330] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  908.534353] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  909.132504] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  909.731232] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  910.330060] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  910.928718] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  911.527441] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  912.136875] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  912.735995] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  913.335349] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  913.934470] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  914.534564] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  915.133958] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  915.733361] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  916.342211] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  916.944110] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  917.542065] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  918.141505] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  918.740671] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  919.338945] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  919.938264] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  920.547345] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  921.146110] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  921.744579] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  922.344576] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  922.942479] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  923.542349] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  924.142923] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  924.750149] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  925.350451] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  925.950165] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  926.549967] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  927.149518] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  927.748932] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  928.347956] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  928.957028] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  929.557535] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  930.157609] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  930.758106] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  931.355956] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  931.955593] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  932.554830] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  933.163967] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  933.763138] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  934.362656] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  934.962711] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  935.561944] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  936.161307] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  936.760914] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  937.371526] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  937.969758] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  938.569135] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  939.169385] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  939.770253] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  940.367614] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  940.967518] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  941.576950] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  942.176893] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  942.775923] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  943.376543] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  943.976597] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  944.575656] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  945.175383] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  945.783222] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  946.382498] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  946.981524] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  947.582303] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  948.182494] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  948.782742] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  949.381179] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  949.990572] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  950.589392] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  951.189799] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  951.789946] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  952.389549] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  952.989705] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  953.589546] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  954.195763] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  954.796172] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  955.396533] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  955.997167] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  956.595295] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  957.194746] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  957.794375] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  958.400225] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  958.999731] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  959.599279] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  960.200313] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  960.799891] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  961.400321] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  961.999260] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  962.605476] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  963.204836] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  963.804693] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  964.403306] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  965.001669] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  965.601729] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  966.200305] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  966.803965] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  967.402508] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  968.000755] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  968.600311] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  969.200033] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  969.799295] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  970.399416] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  970.999802] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  971.600707] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  972.200267] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  972.799911] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  973.398831] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  973.999342] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  974.599624] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  975.199397] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  975.799513] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  976.400120] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  976.999595] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  977.599927] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  978.200474] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  978.800922] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  979.401277] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  980.001085] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  980.601944] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  981.200629] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  981.800825] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  982.402001] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  983.001008] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  983.601502] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  984.201916] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  984.805283] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  985.403767] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  986.002920] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  986.602194] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  987.203313] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  987.803418] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  988.403773] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  989.011619] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  989.612046] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  990.212545] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  990.811576] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  991.410798] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  992.011772] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  992.611757] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  993.219825] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  993.819930] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  994.418922] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  995.019377] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  995.620176] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  996.219810] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  996.818700] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  997.426341] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  998.025980] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  998.626541] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  999.225438] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  999.825611] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1000.426499] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1001.025456] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1001.635078] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1002.233366] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1002.833007] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1003.432757] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1004.031990] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1004.633313] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1005.232639] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1005.840460] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1006.437177] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1007.035531] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1007.634888] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1008.235282] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1008.834918] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1009.434879] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1010.037993] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1010.636485] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1011.236343] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1011.834947] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1012.433616] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1013.034350] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1013.634693] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1014.232420] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1014.831017] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1015.438968] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1016.037316] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1016.636931] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1017.237458] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1017.837971] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1018.438925] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1019.038092] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1019.646479] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1020.245226] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1020.844114] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1021.443099] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1022.043694] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1022.644539] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1023.243769] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1023.852572] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1024.451697] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1025.052071] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1025.651254] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1026.251639] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1026.852416] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1027.452690] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1028.061886] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1028.661951] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1029.262059] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1029.862290] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1030.462267] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1031.061965] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1031.660804] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1032.269740] psmouse serio4: Failed to enable mouse on isa0060/serio4
[ 1072.717956] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.740746] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.764636] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.786906] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.811152] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.833353] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.857588] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.880181] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.904155] psmouse serio4: focaltech: Unknown packet type: 18
[ 1072.927000] psmouse serio4: focaltech: Unknown packet type: 08
[ 1072.950959] psmouse serio4: focaltech: Unknown packet type: 08
[ 1072.973861] psmouse serio4: focaltech: Unknown packet type: 08
[ 1072.997588] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.019853] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.044889] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.067102] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.090991] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.113857] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.137788] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.161566] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.185469] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.208465] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.232063] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.254542] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.278515] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.300776] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.325014] psmouse serio4: focaltech: Unknown packet type: 18
[ 1073.347225] psmouse serio4: focaltech: Unknown packet type: 18
[ 1073.371451] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.394069] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.418011] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.440272] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.464158] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.486430] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.510427] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.532633] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.556582] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.579363] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.603252] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.625467] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.649695] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.672307] psmouse serio4: focaltech: Unknown packet type: 38
[ 1073.696248] psmouse serio4: focaltech: Unknown packet type: 18
[ 1073.718947] psmouse serio4: focaltech: Unknown packet type: 18
[ 1073.742925] psmouse serio4: focaltech: Unknown packet type: 18
[ 1073.765891] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.789604] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.811878] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.836220] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.859121] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.883069] psmouse serio4: focaltech: Unknown packet type: 08
[ 1073.905796] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.929678] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.952618] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.976402] psmouse serio4: focaltech: Unknown packet type: 28
[ 1073.998674] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.023026] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.045945] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.069881] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.092146] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.116369] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.138578] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.162810] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.209661] psmouse serio4: focaltech: Unknown packet type: 38
[ 1074.233600] psmouse serio4: focaltech: Unknown packet type: 08
[ 1074.258586] psmouse serio4: focaltech: Unknown packet type: 08
[ 1074.281486] psmouse serio4: focaltech: Unknown packet type: 08
[ 1074.305664] psmouse serio4: focaltech: Unknown packet type: 08
[ 1074.328461] psmouse serio4: focaltech: Unknown packet type: 08
[ 1074.352397] psmouse serio4: focaltech: Unknown packet type: 28
[ 1074.375295] psmouse serio4: focaltech: Unknown packet type: 08
[ 1074.399080] psmouse serio4: focaltech: Unknown packet type: 28
[ 1074.421339] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.131654] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.155029] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.178344] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.201718] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.224562] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.248452] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.271939] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.295369] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.318539] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.341947] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.365242] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.388609] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.411745] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.435529] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.458310] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.481680] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.504827] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.528179] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.551259] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.574989] psmouse serio4: focaltech: Unknown packet type: 38
[ 1540.597783] psmouse serio4: focaltech: Unknown packet type: 38
[ 1540.621487] psmouse serio4: focaltech: Unknown packet type: 38
[ 1540.644583] psmouse serio4: focaltech: Unknown packet type: 38
[ 1540.667934] psmouse serio4: focaltech: Unknown packet type: 38
[ 1540.691076] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.714859] psmouse serio4: focaltech: Unknown packet type: 18
[ 1540.737636] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.761009] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.784150] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.807738] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.831800] psmouse serio4: focaltech: Unknown packet type: 08
[ 1540.854725] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.877800] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.901224] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.924296] psmouse serio4: focaltech: Unknown packet type: 28
[ 1540.947678] psmouse serio4: focaltech: Unknown packet type: 38
[ 1540.970745] psmouse serio4: focaltech: Unknown packet type: 38
[ 1540.994513] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.017243] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.040668] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.063758] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.087161] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.110302] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.134019] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.156794] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.180157] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.203245] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.226599] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.249795] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.273522] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.296301] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.319744] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.342657] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.366114] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.389306] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.413019] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.435809] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.459228] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.482247] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.505619] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.528808] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.552521] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.575314] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.598736] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.621809] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.645179] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.668256] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.692028] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.714761] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.738127] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.761220] psmouse serio4: focaltech: Unknown packet type: 18
[ 1541.784574] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.808750] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.832641] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.856406] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.880351] psmouse serio4: focaltech: Unknown packet type: 08
[ 1541.903195] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.926967] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.949763] psmouse serio4: focaltech: Unknown packet type: 28
[ 1541.973130] psmouse serio4: focaltech: Unknown packet type: 38
[ 1541.996203] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.019571] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.042705] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.066419] psmouse serio4: focaltech: Unknown packet type: 18
[ 1542.089152] psmouse serio4: focaltech: Unknown packet type: 18
[ 1542.112567] psmouse serio4: focaltech: Unknown packet type: 18
[ 1542.135637] psmouse serio4: focaltech: Unknown packet type: 08
[ 1542.159008] psmouse serio4: focaltech: Unknown packet type: 08
[ 1542.182193] psmouse serio4: focaltech: Unknown packet type: 08
[ 1542.205682] psmouse serio4: focaltech: Unknown packet type: 08
[ 1542.228807] psmouse serio4: focaltech: Unknown packet type: 08
[ 1542.252175] psmouse serio4: focaltech: Unknown packet type: 08
[ 1542.275260] psmouse serio4: focaltech: Unknown packet type: 08
[ 1542.298617] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.321701] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.345432] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.368209] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.530200] psmouse serio4: focaltech: Unknown packet type: 18
[ 1542.553795] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.577177] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.600354] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.624076] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.646846] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.670212] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.693297] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.716653] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.739833] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.763557] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.786343] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.810565] psmouse serio4: focaltech: Unknown packet type: 28
[ 1542.834620] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.856944] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.880885] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.903726] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.926527] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.949932] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.973066] psmouse serio4: focaltech: Unknown packet type: 38
[ 1542.996436] psmouse serio4: focaltech: Unknown packet type: 38
[ 1543.019451] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.043219] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.065945] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.089370] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.112457] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.135864] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.158935] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.193449] psmouse serio4: focaltech: Unknown packet type: 18
[ 1543.517003] psmouse serio4: focaltech: Unknown packet type: 08
[ 1543.713749] psmouse serio4: focaltech: Unknown packet type: 08
[ 1543.738282] psmouse serio4: focaltech: Unknown packet type: 08
[ 1615.527614] psmouse serio4: focaltech: Unknown packet type: 08
[ 1615.549840] psmouse serio4: focaltech: Unknown packet type: 08
[ 1615.585922] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.494559] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.516775] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.541009] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.563629] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.587525] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.609791] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.634087] psmouse serio4: focaltech: Unknown packet type: 28
[ 5327.656301] psmouse serio4: focaltech: Unknown packet type: 28
[ 5327.680540] psmouse serio4: focaltech: Unknown packet type: 28
[ 5327.703244] psmouse serio4: focaltech: Unknown packet type: 28
[ 5327.727682] psmouse serio4: focaltech: Unknown packet type: 38
[ 5327.750819] psmouse serio4: focaltech: Unknown packet type: 38
[ 5327.774770] psmouse serio4: focaltech: Unknown packet type: 38
[ 5327.797579] psmouse serio4: focaltech: Unknown packet type: 38
[ 5327.821458] psmouse serio4: focaltech: Unknown packet type: 38
[ 5327.845354] psmouse serio4: focaltech: Unknown packet type: 18
[ 5327.869127] psmouse serio4: focaltech: Unknown packet type: 18
[ 5327.891352] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.915711] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.938487] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.962383] psmouse serio4: focaltech: Unknown packet type: 08
[ 5327.984608] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.008849] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.031111] psmouse serio4: focaltech: Unknown packet type: 28
[ 5328.055286] psmouse serio4: focaltech: Unknown packet type: 28
[ 5328.078137] psmouse serio4: focaltech: Unknown packet type: 28
[ 5328.102029] psmouse serio4: focaltech: Unknown packet type: 38
[ 5328.124299] psmouse serio4: focaltech: Unknown packet type: 38
[ 5328.148550] psmouse serio4: focaltech: Unknown packet type: 38
[ 5328.170752] psmouse serio4: focaltech: Unknown packet type: 38
[ 5328.194988] psmouse serio4: focaltech: Unknown packet type: 18
[ 5328.217780] psmouse serio4: focaltech: Unknown packet type: 18
[ 5328.241667] psmouse serio4: focaltech: Unknown packet type: 18
[ 5328.263941] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.288186] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.310385] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.334618] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.357321] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.381307] psmouse serio4: focaltech: Unknown packet type: 08
[ 5328.403576] psmouse serio4: focaltech: Unknown packet type: 08
[ 6829.323061] psmouse serio4: focaltech: Unknown packet type: 08
[ 6829.346148] psmouse serio4: focaltech: Unknown packet type: 28
[ 7425.519297] psmouse serio4: focaltech: Unknown packet type: 08
[ 7425.542697] psmouse serio4: focaltech: Unknown packet type: 08
[ 7425.567191] psmouse serio4: focaltech: Unknown packet type: 18
[ 7425.589692] psmouse serio4: focaltech: Unknown packet type: 18
[ 7425.614632] psmouse serio4: focaltech: Unknown packet type: 18
[ 7708.637056] psmouse serio4: focaltech: Unknown packet type: 18


```

I already had a problem to enable wiereless with Fn+F2 - that's now fixed with :```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```

Fn+F9 (touchpad enabling) respond with proper picture,  but does not change anything in work

---

### Post by Pilot6 on 2015-02-10
This touchpad problem has noot been soleved for your model yet.

You can enable touchpad booting with

psmouse.proto=bare

It will work, but without multitouch.

---

### Post by luk5 on 2015-02-11
Thank you Pilot6 !

Hope permanent solution will be found soon. In the meantime I enabled touchpad as PSmouse. Works good enough :)

Thanks again!

---

### Post by Pilot6 on 2015-02-14
luk5,

Mathias Gottschlag fixed issues for some models, where driver did not work. I will upload the kernel images soon, after some testing.

---

### Post by Pilot6 on 2015-02-14
The images are at [https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0) in next directory.

---

### Post by marduk7 on 2015-02-17
Hi Pilot6,
thanks for the good work, my Zenbook UX303LA touchpad is working properly now with your kernel in Linux Mint 17.1.
However now it appears that all 3.16 kernels have a problem with uvcvideo. Here is the launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362358](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362358)
Fix is quite simple: [http://git.linuxtv.org/cgit.cgi/pinchartl/media.git/commit/?h=uvcvideo/fixes&id=a7f053c67c357c4b68c1be21976a1d464f97916b](http://git.linuxtv.org/cgit.cgi/pinchartl/media.git/commit/?h=uvcvideo/fixes&id=a7f053c67c357c4b68c1be21976a1d464f97916b)
Now I'd like to apply this patch as well to test if it works. Would you be able to share your patch for focaltech or the complete source tarball with the touchpad driver included? Thanks in advance.
Andrew

---

### Post by marduk7 on 2015-02-17
Found your github. I will take it from there.

---

### Post by Pilot6 on 2015-02-17
Marduk7, if the patch solves the issue, just let me know. I will backport it there.

It looks like it is not a kernel bug, but an application bug.

I see it has been fixed in 3.18
[https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/commit/?id=c601f53f8fe5aab4d8b506104d0fd0a7b6a19922](https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/commit/?id=c601f53f8fe5aab4d8b506104d0fd0a7b6a19922)

It looks like it has been backported already. Try with 3.18 kernel.

---

### Post by marduk7 on 2015-02-17
Actually it looks like it was backported already in your sources as well.. So maybe this is another issue or indeed an application bug.
I have commented on the launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362358](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362358)
The problem magically went away after updating the guvcview and libguvcview to 2.0.1. Let's use launchpad if you want to comment on this issue.
This thread is marked as closed. I can still post a quick reply, but I can't reply in advanced mode and it's not a good idea to mix two issues in the same thread anyway. Thanks for the help :)

---

### Post by mörgæs on 2015-02-17
> **marduk7 said:**
> 
This thread is marked as closed.
No,it's marked SOLVED, which is a different matter.

---

### Post by vonkad2 on 2015-02-20
I just installed Linux Mint 17.1 on an ASUS Zenbook UX303LN and installing the patched 3.16 kernel by pilot6 is the only thing that works. Installing current stable 3.19 does not move me from PS2-emulation to fully functional touchpad with two-finger scrolling. 

When will the patch appear in a mainstream Linux kernel ? Thanks, David Vonka

---

### Post by Pilot6 on 2015-02-20
In 3.20.

---

### Post by Yakuza on 2015-02-23
My model is an Asus X450V, installed the latest kernel build in NEXT folder, the hotkey for touchpad enabling works but the touchpad itself is completely dead, even the partial movement I had with the default kernel disappearead.

**uname -a**
```
Linux manubook 3.16.0-31-generic #41 SMP Mon Feb 23 17:11:45 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux
```

**dkms status**
```
bbswitch, 0.8, 3.13.0-32-generic, x86_64: installed
bbswitch, 0.8, 3.16.0-30-generic, x86_64: installed
bbswitch, 0.8, 3.16.0-31-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-30-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-31-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-30-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-31-generic, x86_64: installed
```

**dmesg | grep pnp**
```
[    0.580925] pnp: PnP ACPI init
[    0.636121] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.636273] pnp 00:05: Plug and Play ACPI device, IDs FLT0102 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.636312] pnp 00:06: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.636746] pnp: PnP ACPI: found 10 devices
```

**dmesg | grep serio**
```
[    1.071526] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.071530] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.071554] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.071573] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.071591] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.119876] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.340325] input: FocalTechPS/2 FocalTech FocalTech Touchpad as /devices/platform/i8042/serio4/input/input11
[    1.368087] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    1.960051] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    2.566139] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    3.172985] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    3.764807] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    4.355820] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    4.946700] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    5.539394] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    6.129923] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    6.720687] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    7.311335] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    7.901947] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    8.492804] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    9.084193] psmouse serio4: Failed to enable mouse on isa0060/serio4
[    9.674824] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   10.272308] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   10.864134] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   11.455742] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   12.050645] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   12.645707] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   13.236564] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   13.826479] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   14.417834] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   15.008399] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   15.599014] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   16.189524] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   16.780234] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   17.370910] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   17.961632] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   18.554102] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   19.146170] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   19.742433] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   20.334634] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   20.925286] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   21.516384] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   22.107311] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   22.698634] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   23.293689] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   23.889793] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   24.481182] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   25.071838] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   25.662598] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   26.254530] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   26.847355] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   27.438894] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   28.030502] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   28.622189] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   29.218375] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   29.809947] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   30.401028] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   30.993229] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   31.585295] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   32.177823] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   32.768627] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   33.367116] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   33.958092] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   34.550031] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   35.141278] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   35.733455] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   36.324577] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   36.916886] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   37.508629] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   38.100576] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   38.692704] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   39.284345] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   39.875057] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   40.465881] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   41.057929] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   41.648790] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   42.239654] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   42.836478] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   43.427108] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   44.017908] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   44.609773] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   45.200414] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   45.791118] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   46.381760] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   46.976108] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   47.568167] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   48.159585] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   48.750270] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   49.341102] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   49.932943] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   50.523467] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   51.114178] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   51.704948] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   52.299340] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   52.890793] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   53.481210] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   54.071852] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   54.662696] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   55.253752] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   55.846115] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   56.450074] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   57.042211] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   57.633801] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   58.224828] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   58.815971] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   59.406788] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   59.997555] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   60.589258] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   61.179898] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   61.770476] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   62.361123] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   62.951907] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   63.543428] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   64.134306] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   64.725341] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   65.316239] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   65.914292] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   66.504660] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   67.095487] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   67.686647] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   68.277307] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   68.868275] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   69.458972] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   70.053359] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   70.644840] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   71.235076] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   71.826616] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   72.416928] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   73.008273] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   73.599279] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   74.189917] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   74.780533] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   75.374392] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   75.964883] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   76.555073] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   77.144909] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   77.735606] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   78.326822] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   78.921315] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   79.515938] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   80.110639] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   80.703000] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   81.293698] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   81.884363] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   82.475564] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   83.066562] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   83.660216] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   84.251195] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   84.854015] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   85.448446] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   86.039417] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   86.630093] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   87.220862] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   87.811606] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   88.401606] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   88.992445] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   89.587958] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   90.180493] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   90.770490] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   91.361319] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   91.952141] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   92.542961] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   93.134762] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   93.725458] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   94.316112] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   94.906847] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   95.498818] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   96.089412] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   96.680045] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   97.270911] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   97.861718] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   98.452650] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   99.043471] psmouse serio4: Failed to enable mouse on isa0060/serio4
[   99.639972] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  100.230900] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  100.821510] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  101.412076] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  102.002564] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  102.593245] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  103.183655] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  103.776599] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  104.366835] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  104.957255] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  105.547994] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  106.138361] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  106.729365] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  107.319908] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  107.910494] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  108.501244] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  109.095906] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  109.686329] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  110.276862] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  110.867625] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  111.458224] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  112.049223] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  112.639695] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  113.236018] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  113.827024] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  114.419828] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  115.009481] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  115.601956] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  116.192609] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  116.783267] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  117.374144] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  117.964886] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  118.561321] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  119.152302] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  119.743329] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  120.334777] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  120.925744] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  121.516690] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  122.107576] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  122.699376] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  123.290557] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  123.881099] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  124.471269] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  125.061483] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  125.652436] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  126.243221] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  126.834465] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  127.425648] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  128.022215] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  128.613283] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  129.204254] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  129.795253] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  130.386330] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  130.977277] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  131.568235] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  132.161834] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  132.752555] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  133.342693] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  133.933655] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  134.524551] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  135.114821] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  135.705724] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  136.295793] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  136.886705] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  137.481642] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  138.072604] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  138.664495] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  139.255717] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  139.846706] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  140.437681] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  141.028990] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  141.624791] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  142.214640] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  142.805558] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  143.396451] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  143.987041] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  144.578396] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  145.169294] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  145.760334] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  146.351382] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  146.945557] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  147.536686] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  148.127537] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  148.718533] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  149.309446] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  149.900440] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  150.491500] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  151.088249] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  151.678895] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  152.269800] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  152.860693] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  153.451479] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  154.042363] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  154.633307] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  155.224184] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  155.815129] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  156.405889] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  156.996844] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  157.587606] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  158.178378] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  158.769139] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  159.360301] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  159.951243] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  160.548324] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  161.137954] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  161.729054] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  162.320156] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  162.911297] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  163.502582] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  164.093454] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  164.686482] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  165.277430] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  165.867998] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  166.458942] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  167.049875] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  167.641275] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  168.232612] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  168.823877] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  169.414977] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  170.011348] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  170.602481] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  171.193395] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  171.784336] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  172.375180] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  172.965964] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  173.556805] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  174.152165] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  174.743026] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  175.338685] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  175.933377] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  176.528952] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  177.123965] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  177.720371] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  178.315872] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  178.907062] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  179.498201] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  180.089175] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  180.680708] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  181.272052] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  181.863292] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  182.454346] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  183.045397] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  183.642473] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  184.232902] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  184.823593] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  185.414927] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  186.006174] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  186.597265] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  187.188144] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  187.783797] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  188.374524] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  188.965522] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  189.556585] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  190.147775] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  190.739281] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  191.330181] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  191.920952] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  192.511970] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  193.106042] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  193.698658] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  194.289740] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  194.880992] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  195.471965] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  196.063233] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  196.654603] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  197.252006] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  197.842493] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  198.433598] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  199.024992] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  199.616629] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  200.207654] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  200.798881] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  201.390088] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  201.981157] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  202.572227] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  203.163300] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  203.754630] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  204.345638] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  204.936689] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  205.528225] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  206.119236] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  206.715680] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  207.306880] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  207.897889] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  208.489102] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  209.080517] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  209.671925] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  210.263624] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  210.858262] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  211.449256] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  212.040218] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  212.631211] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  213.222216] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  213.813702] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  214.404784] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  214.995929] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  215.587231] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  216.181673] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  216.773620] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  217.365636] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  217.956392] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  218.548525] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  219.139670] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  219.730793] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  220.327525] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  220.918572] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  221.510309] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  222.102371] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  222.695001] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  223.286487] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  223.878254] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  224.470602] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  225.062052] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  225.653736] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  226.244983] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  226.836123] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  227.428467] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  228.020532] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  228.612838] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  229.204361] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  229.805849] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  230.398509] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  230.990381] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  231.582614] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  232.176143] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  232.767054] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  233.359293] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  233.951644] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  234.542565] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  235.137933] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  235.731468] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  236.326289] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  236.918369] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  237.510329] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  238.102694] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  238.693699] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  239.290552] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  239.881484] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  240.473237] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  241.064665] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  241.656227] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  242.246862] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  242.837844] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  243.431233] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  244.024087] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  244.616052] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  245.207962] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  245.798931] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  246.391369] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  246.982472] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  247.574747] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  248.166443] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  248.766411] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  249.356797] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  249.947708] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  250.539516] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  251.131618] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  251.727416] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  252.318643] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  252.916232] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  253.508220] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  254.099953] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  254.691700] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  255.283602] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  255.879168] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  256.471653] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  257.063526] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  257.655629] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  258.259054] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  258.849618] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  259.443480] psmouse serio4: Failed to enable mouse on isa0060/serio4
[  260.035698] psmouse serio4: Failed to enable mouse on isa0060/serio4
```

I will have to check touchpad support in the kernel before purchasing another notebook, that's just sad.

UPDATE:

Wanted to try 3.19 from Mathias, but it seems I cannot compile the NVIDIA proprietary drivers on it so it's a no go, for now psmouse.proto=bare must suffice.

---

### Post by Pilot6 on 2015-02-24
As soon as Mathias makes his latest fix available, I will backport it to 3.16. The fix is straightforward now, but I do not want to make another fork.

---

### Post by Yakuza on 2015-02-24
> **Pilot6 said:**
> As soon as Mathias makes his latest fix available, I will backport it to 3.16. The fix is straightforward now, but I do not want to make another fork.

Thanks mate, looking forward to that!

---

### Post by Pilot6 on 2015-02-27
Yakuza,

I backported latest patches from Mathias. I hope your touchpad works now.
It is here in 'next' directory.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

---

### Post by Yakuza on 2015-03-10
> **Pilot6 said:**
> Yakuza,

I backported latest patches from Mathias. I hope your touchpad works now.
It is here in 'next' directory.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Sorry if it took me such along time to answer, I was traveling for work.

You did it mate! It works perfectly :)

---

### Post by danylion on 2015-03-24
Thank you Pilot6! Happily using my touchpad :)

---

### Post by Pilot6 on 2015-03-25
Now fix is in both stable and next directories.

---

### Post by ehood2 on 2015-04-05
Hey I have **ASUS D552CL**, and the computer doesnt recognize **touchpad.**
ubuntu:~$ dmesg | grep pnp
[    0.626721] pnp: PnP ACPI init
[    0.681618] pnp 00:01: [dma 4]
[    0.681644] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.681670] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.681795] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.681911] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.682072] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.682143] pnp 00:09: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.682193] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.682754] pnp: PnP ACPI: found 14 devices

ubuntu:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=13    [slave  pointer  (2)]/[COLOR=#008000]/ /I dont recognize this mouse[/COLOR]///
&#9116;   &#8627; SIGMACHIP Usb Mouse                         id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)

my kernel is **3.13**, will your solution work for me?

---

### Post by Pilot6 on 2015-04-05
Yes, It should work. 3.16 kernel is default for 14.04.2.

---

### Post by ehood2 on 2015-04-06
I have 3.13 kernel not 3.16 . will it work?

---

### Post by Pilot6 on 2015-04-06
If you install my kernel, you will have 3.16 .

---

### Post by ehood2 on 2015-04-06
where is your kernel?
and could you instruct me how to install it?

---

### Post by Pilot6 on 2015-04-06
The kernel is here.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Download all deb files from 'stable' directory to your home directory and run in terminal

sudo dpkg -i linux*.deb

Then reboot.

---

### Post by ehood2 on 2015-04-06
thanks its working ..

---

### Post by xen4 on 2015-04-07
Thank you Pilot6. Everything works on my ASUS UX303L, except that after installing the kernel my pointer speed seems to have reduced and I can't even change it through the settings. Any suggestions?

---

### Post by Pilot6 on 2015-04-07
Pointer speed setting is not supported yet. And it is not known how to fix it.

---

### Post by broslowski2 on 2015-04-09
Hello.

THX for deb files - however - after latest auto ubuntu LTS update this do not work. Is there another latest deb files?

Thank you

---

### Post by Pilot6 on 2015-04-09
Latest debs are at the same place. If you did not use any external repositories with kernels, then mine should be same version as the official.

---

### Post by c51 on 2015-04-10
> **Pilot6 said:**
> Latest debs are at the same place. If you did not use any external repositories with kernels, then mine should be same version as the official.
Really appreciate your work, thank you very much. Any chance to also get the latest wifi driver backported in order to be able to use the latest firmware - i.e. v12?

---

### Post by Pilot6 on 2015-04-10
I do not know which wifi driver you have. You can make a topic in Networking and send me a link. I will look at it.

---

### Post by Pilot6 on 2015-04-13
I made a ppa with Focaltech driver. It is here

ppa:hanipouspilot/focaltech-dkms

Read instructions before install pls. Users of Ubuntu 14.04 will need linux-generic-lts-vivid package.
It pulls 3.19 kernel. At the moment it is 3.19.0-12. I have some graphics issues with it. 
With 3.19.0-13 it is OK. I hope they will update the ppa soon.
And soon we wait that that package appears in Ubuntu main repository.

---

### Post by mark211 on 2015-04-17
@Pilot6, 

first of all thanks for all your help!
 
I installed your .deb files last week and everything worked great.

Now today, it no longer seems to be working. 
 
I freshly installed ubuntu and ran the .deb files, but no luck. 

if I run uname -a I get:

Linux mark-UX303LAB 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Interestingly, my package manager seems to be broken afterwards. If I run software updater I get an error: 
 
The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

I can try to use your ppa later, but I'm wondering if you have any ideas on why it's suddenly broken.

---

### Post by Pilot6 on 2015-04-17
My ppa for 14.04 won't work out of the box at the moment. Please read description of the ppa. Package works only with kernel 3.19 and requires
linux-generic-lts-vivid package. It will be in main repository in a week or two, I guess.

---

### Post by James_Read-Tannock on 2015-04-24
First time posting here, just wanted to thank you Pilot6 for doing such a good job! I'm sure there are a lot of grateful Zenbook owners :D

---

### Post by skagedal2 on 2015-04-30
Thanks a lot, Pilot6! I have an ASUS ZenBook UX303LN and I'm running Ubuntu 15.04, and using this the touchpad works perfectly. To possibly help clarify for others, these are the steps you need to do:

```

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install focaltech-dkms

```

Then reboot, or do this to get things working instantly, as documented in README:
```

sudo modprobe -r psmouse
sudo modprobe psmouse

```

---

### Post by JohannSebastianBac on 2015-05-25
Dear Pilot6

I signed in just to say thank you very beaucoup !

---

### Post by Pilot6 on 2015-05-25
You are welcome. 
And now there is no need to add kernel ppa for 14.04 users. Linux-generic-lts-vivid is in trusty-updates already.

---

### Post by David_Jacobowitz on 2015-05-27
I'm on a UX303LN. I just tried the steps below and I'm getting error messages that the focaltech-dkms package did not build. Any ideas? Where can I look to see the build messages?

david@cavalier:~$ uname -a
Linux cavalier 3.19.0-18-generic #18~14.04.1-Ubuntu SMP Wed May 20 09:38:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

david@cavalier:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 FocalTech FocalTech Touchpad in mouse emulation mode    id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

david@cavalier:~$ dmesg | grep pnp
[    0.224369] pnp: PnP ACPI init
[    0.224747] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.224947] pnp 00:06: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.224985] pnp 00:07: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.225998] pnp: PnP ACPI: found 11 devices










The 
> **skagedal2 said:**
> Thanks a lot, Pilot6! I have an ASUS ZenBook UX303LN and I'm running Ubuntu 15.04, and using this the touchpad works perfectly. To possibly help clarify for others, these are the steps you need to do:

```

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install focaltech-dkms

```

Then reboot, or do this to get things working instantly, as documented in README:
```

sudo modprobe -r psmouse
sudo modprobe psmouse

```

best,
David

---

### Post by Pilot6 on 2015-05-28
What are the error messages? I use it on 14.04 with same kernel and it builds.

You probably did not remove 3.16 kernels and it really does not build for them. But it should not worry you, if you boot with 3.19.

---

### Post by iwebseo on 2015-06-09
@[**[COLOR=#000000]skagedal2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1857843") Thanks man you are life saver. It works perfectly on Asus Zenbook UX303LN with Ubuntu 15.04 fresh out of the box.
My trackpad works now with two fingers also the settings are available in the Mouse menu. Before there were no settings for trackpad under mouse/trackpad settings.

---

### Post by armandg on 2015-08-13
Hey Pilot6,

I'm currently running Manjaro (Kernel 3.18.20-1-MANJARO) on my Asus X550JK, will I be able to use my trackpad by installing this package as well?

---

### Post by Pilot6 on 2015-08-13
As far as I know Manjaro does not use deb packages. 
You can install the driver from [https://github.com/hanipouspilot/focaltech-dkms](https://github.com/hanipouspilot/focaltech-dkms)

It should build for 3.18, I guess. Actually it is for 3.17+

---

### Post by armandg on 2015-08-13
This might be a stupid question, but how do I install the drivers? I downloaded the zip file and unzipped it.

---

### Post by Pilot6 on 2015-08-13
I am afraid moderators will kill us for off topic. You better ask this somewhere else.
Tip. Rename the folder you unzipped to /usr/src/focaltech-1.5 and run

dkms install -m focaltech -v 1.5

I will give no more tips.

---

### Post by armandg on 2015-08-13
I will stop here, you've been of good help =)
Edit: Just want you to know it worked after downloading linux headers.

---

### Post by thatoo2 on 2015-10-09
Thank you pilot6 for your help in here, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445)
I am running ubuntu 14.04 with kernel 3.19.30.
kernel 4.1.6 have been deleted
the driver focaltech-dkms is installed, The touchpad works like it was working.
 Before suspending the computer, I can deactivate and activate again the touchpad with the hotkey of my keyboard without problem.

However, the problem is sitll on. I can suspend the computer but after the  computer come back from sleeping, the touchpad is not working anymore.
You were thinking that an Elantech driver that I had instaled earler might be the problem.
How can I solve the conflict? How can I delete this Elantech driver?...

I am sorry pilot6 but it is still a bug, not "invalid", I don't bother people for support request or spam...

---

### Post by Pilot6 on 2015-10-09
You said that you did a fresh install. So there is no Elantech driver.

---

### Post by thatoo2 on 2015-10-09
As I wrote in answer 28, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445/comments/28](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445/comments/28)
I remember now, I think I tried something about elantech because I was following a tutorial for asus touchpad here [https://doc.ubuntu-fr.org/touchpad_asus](https://doc.ubuntu-fr.org/touchpad_asus) because I didn't know what to do.
I understand now it was wrong but I'm not expert, I try to solve problem by myself but sometime I don't understand the difference between elantech and Focaltech and stuff like that, it somewhat quiet complicated and not so user friendly...

So now, I am running ubuntu 14.04 with kernel 3.19.30.
kernel 4.1.6 have been deleted
the driver focaltech-dkms is installed,
 The touchpad works like it was working.
 Before suspending the computer, I can deactivate and activate again the touchpad with the hotkey of my keyboard without problem.


After suspending the computer and caming back from sleeping, the touchpad is not working anymore.
What should I do?

 Is the Elantech driver the problem, I don't know and I don;t know how to delete it.

---

### Post by Pilot6 on 2015-10-09
Please give output of

dkms status

And how did you install the Focaltech driver?

---

### Post by thatoo2 on 2015-10-09
yogo@yogo-ordi:~$ dkms status
bbswitch, 0.7, 3.13.0-65-generic, x86_64: installed
bbswitch, 0.7, 3.19.0-30-generic, x86_64: installed
focaltech, 1.5~trusty1, 3.19.0-30-generic, x86_64: installed
nvidia-355, 355.11, 3.13.0-65-generic, x86_64: installed
nvidia-355, 355.11, 3.19.0-30-generic, x86_64: installed
yogo@yogo-ordi:~$ 

When I read this page, [https://doc.ubuntu-fr.org/touchpad_asus](https://doc.ubuntu-fr.org/touchpad_asus)
I think I remember trying that (but I'm not sure anymore, I tried so many things about touchpad, nvidia settings and driver, brightness...): 
cd /usr/src/
sudo dkms remove psmouse/elantech-v6 --all
sudo wget [http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2](http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2) 
sudo tar jxvf psmouse-elantech-v7.tar.bz2 
sudo dkms add -m psmouse -v elantech-v7
sudo dkms build -m psmouse -v elantech-v7 
sudo dkms install -m psmouse -v elantech-v7

Regards,

---

### Post by Pilot6 on 2015-10-09
You do not have an Elantech driver installed.

---

### Post by thatoo2 on 2015-10-11
so there is really a bug then, no?
In here,  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504445), they made  me update the bios, but it didn't change anything.

---

### Post by thatoo2 on 2015-10-18
A developper invited me to look at this other report with Asus losing touchpad
function after suspend:

 [https://bbs.archlinux.org/viewtopic.php?id=194810](https://bbs.archlinux.org/viewtopic.php?id=194810)
 Can you try unloading and reloading i8042 module (make sure it is a
module and not compiled into kernel).
 Thanks.
 [...]



 I tried to follow the solution,
 - pm-utils was already installed
- I  created the file /etc/pm/config.d/modules
sudo gedit /etc/pm/config.d/modules
and I wrote
SUSPEND_MODULES="i8042"
- Then I tried to suspend  using "sudo pm-suspend" to suspend or the shortkey etc..
 but nothing change.
Maybe I have to write more inside /etc/pm/config.d/modules to "unload" on suspend and then "reload" on resume, no?
Maybe just the line SUSPEND_MODULES="i8042" is not enough but what should I write?
What means (make sure it is a module and not compiled into kernel)?

Someone ask me the result of  the command

lsmod | grep i8042

it doesn't show anything.

---

### Post by thatoo2 on 2015-10-30
Thanks to Harris Anggara (harrisanggara) and Daniel Drake (dsdrake)  here, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130) , I could solve my problem by adding this patch to the kernel : 
[https://marc.info/?l=linux-input&m=144312209020616&w=2](https://marc.info/?l=linux-input&m=144312209020616&w=2)

now i'm using kernel 4.2 for Ubuntu 14.04  with the patch. i changed the DMI_PRODUCT_NAME with K501LX (because that is my laptop model).

I tried directly with kernel 4.2 because before that, kernel 3.19 and so, they need a driver for my touchpad. I followed the instruction here to obtain the source of kernel 4.2 for Ubuntu 14.04, [https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide](https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide)
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
then from inside the folder you've just downloaded (cd ubuntu-trusty)
git tag -l Ubuntu-*
to know what is available for ubuntu 14.04
and then
git checkout -f -b temp Ubuntu-lts-4.2.0-6.6_14.04.1.1

After, to build the kernel, I followed this explanation, [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
fakeroot debian/rules clean
fakeroot debian/rules binary-headers binary-generic
then
cd ..
ls *.deb
    linux-cloud-tools-4.2.0-6-generic_4.2.0-6.6~14.04.1.1_amd64.deb
    linux-headers-4.2.0-6_4.2.0-6.6~14.04.1.1_all.deb
    linux-headers-4.2.0-6-generic_4.2.0-6.6~14.04.1.1_amd64.deb
    linux-image-4.2.0-6-generic_4.2.0-6.6~14.04.1.1_amd64.deb
    linux-image-extra-4.2.0-6-generic_4.2.0-6.6~14.04.1.1_amd64.deb
    linux-tools-4.2.0-6-generic_4.2.0-6.6~14.04.1.1_amd64.deb

I deleted this two files because I don't need them
    linux-cloud-tools-4.2.0-6-generic_4.2.0-6.6~14.04.1.1_amd64.deb
    linux-tools-4.2.0-6-generic_4.2.0-6.6~14.04.1.1_amd64.deb
and finally,
sudo dpkg -i linux*4.2.0-6.6~14.04.1.1*.deb
sudo reboot

Now it works nicely. The touchpad works fine, without the need to install any driver and I can suspend the activity of my computer and resume without loosing the touchpad. I hope the patch will be integrated soon and I won't loose my touchpad again with updates in the future.

Thank you everybody,
Take care, always smiling,

---

### Post by m-chrisauf on 2015-12-15
> **Pilot6 said:**
> You have a Focaltech touchpad.
It is not officially supported yet. But you can insall my build from here.

[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

I recomend 3.0.16-29 version, since it is official now.

Hello Pilot6,
I also have a problem with the arrow pointer of my Asus Zenbook UX303LN-R4203H 64 bits under Ubuntu 14.04.02 LTS (dual boot W8) which has been freezing continuously for the last 10 days. I can only work with an external bluetooth mouse. Under W8 I have no problem as the touchpad works perfectly. I am French too, a total beginner with Linux and don't master well the English  IT language. As I don't want to make a mess on my laptop, I would like to know if your above solution is valid for me too. Here is the output of dmesg | grep pnp :
marina@marina-UX303LN:~$ dmesg | grep pnp
[    0.245400] pnp: PnP ACPI init
[    0.245827] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.246060] pnp 00:06: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.246106] pnp 00:07: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.247172] pnp: PnP ACPI: found 10 devices

If it is valid, what exactly must I download of all these on your Dropbox? 
**Focaltec**


[LIST]
[*][URL="https://www.dropbox.com/sh/07642x3lziqgmz9/AACcGDFna6aoEhBdT-ZbR-Xea/next?dl=0"]next
[/URL]
[IMG]https://cf.dropboxstatic.com/static/images/icons/icon_spacer-vflN3BYt2.gif[/IMG] 
[*][stable]("https://www.dropbox.com/sh/07642x3lziqgmz9/AADmz5pR4X5ZTfRSDKmeDZo_a/stable?dl=0")


[IMG]https://cf.dropboxstatic.com/static/images/icons/icon_spacer-vflN3BYt2.gif[/IMG] 
[*][!!! SUPPORT DROPPED !!!]("https://www.dropbox.com/sh/07642x3lziqgmz9/AAAncrXK3jyV7rBle6UJ_IyLa/%21%21%21%20SUPPORT%20DROPPED%20%21%21%21?dl=0")


372 octets 
[*][README]("https://www.dropbox.com/sh/07642x3lziqgmz9/AABOZXd1JFJU3t21fDS7kneya/README?dl=0")


96 octets

Thank you for your help.
m-chrisauf 
[/LIST]

---

### Post by er-ankitgandhi2013 on 2016-10-03
Hello..

Thank you very much...It's working fine....(after reboot)

---

