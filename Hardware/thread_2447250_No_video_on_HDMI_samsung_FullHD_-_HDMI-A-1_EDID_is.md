---
title: "No video on HDMI samsung FullHD - HDMI-A-1: EDID is invalid"
date: 2020-07-15
forum: Hardware
---

### Post by ezerbib on 2020-07-15
I have some problems booting Ubuntu 18 or 20 with the latest kernel on some Samsung TV (fullHD not 4k) TYPE UN40ES6500F
No graphic video appear, It seams that the EDID is not read correctly and is filling with zero from the i915 driver. Result is that Xorg doesn't 

If I make a power cylce of the TV the edid is sometimes read correctly, same setup in booting well with older version of Ubuntu 16
I doubt on the latest i915 driver that can't read DDC correctly
 
I have tried other kernels than the official 5.4.0.40, same is with 5.3.0.40-lowlatency same with 4.15.0-74-generic

Some Input on how could I resolve the problem ??


My hardware :
[FONT=courier new]model name      : Intel(R) Celeron(R) N4000 CPU @ 1.10GHz[/FONT]



...
[FONT=courier new][    3.265164] Setting dangerous option enable_fbc - tainting kernel
[    3.265168] Setting dangerous option enable_guc - tainting kernel
[    3.266213] i915 0000:00:02.0: vgaarb: deactivate vga console
[    3.266313] [drm] couldn't get memory information
[    3.266323] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.266324] [drm] Driver supports precise vblank timestamp query.
[    3.266421] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.267077] [drm] Finished loading DMC firmware i915/glk_dmc_ver1_04.bin (v1.4)
[    3.270367] [drm] HuC: Loaded firmware i915/glk_huc_ver03_01_2893.bin (version 3.1)
[    3.275461] [drm] GuC: Loaded firmware i915/glk_guc_32.0.3.bin (version 32.0)
[    3.275912] [drm] CT: enabled
[    3.280497] i915 0000:00:02.0: GuC firmware version 32.0
[    3.280499] i915 0000:00:02.0: GuC submission disabled
[    3.280500] i915 0000:00:02.0: HuC enabled
[    3.282072] [drm] Initialized i915 1.6.0 20190619 for 0000:00:02.0 on minor 0
[    3.284513] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.285885] acpi device:53: registered as cooling_device3
[    3.285968] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3
[    3.299196] i915 0000:00:02.0: **[COLOR=#ff0000]HDMI-A-1: EDID is invalid:[/COLOR]**
[    3.299199]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.299200]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.299201]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.299201]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.299202]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.299203]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.299203]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.299204]  [00] ZERO 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    3.323523] usb 1-4: config 1 interface 1 altsetting 0 endpoint 0x83 has wMaxPacketSize 0, skipping
[    3.323524] usb 1-4: config 1 interface 1 altsetting 0 endpoint 0x3 has wMaxPacketSize 0, skipping
[    3.323529] usb 1-4: New USB device found, idVendor=0cf3, idProduct=e300, bcdDevice= 0.01
[    3.323530] usb 1-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.334271] [drm] Cannot find any crtc or sizes
[    3.337409] mmc0: Command Queue Engine enabled
[    3.337415] mmc0: new HS400 MMC card at address 0001
[    3.341387] mmcblk0: mmc0:0001 TA2832 29.2 GiB 
[    3.341596] mmcblk0boot0: mmc0:0001 TA2832 partition 1 4.00 MiB
[    3.341802] mmcblk0boot1: mmc0:0001 TA2832 partition 2 4.00 MiB
[    3.341899] mmcblk0rpmb: mmc0:0001 TA2832 partition 3 4.00 MiB, chardev (241:0)
[    3.344156]  mmcblk0: p1 p2 p3
[    3.383841] [drm] Cannot find any crtc or sizes

root@xxx:~# lspci
00:00.0 Host bridge: Intel Corporation Device 31f0 (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Device 3185 (rev 03)
00:0e.0 Audio device: Intel Corporation Device 3198 (rev 03)
00:0f.0 Communication controller: Intel Corporation Device 319a (rev 03)
00:13.0 PCI bridge: Intel Corporation Device 31d8 (rev f3)
00:13.1 PCI bridge: Intel Corporation Device 31d9 (rev f3)
00:13.2 PCI bridge: Intel Corporation Device 31da (rev f3)
00:15.0 USB controller: Intel Corporation Device 31a8 (rev 03)
00:1c.0 SD Host controller: Intel Corporation Device 31cc (rev 03)
00:1f.0 ISA bridge: Intel Corporation Device 31e8 (rev 03)
00:1f.1 SMBus: Intel Corporation Device 31d4 (rev 03)
01:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
[/FONT]

---

### Post by CatKiller on 2020-07-15
> **ezerbib said:**
> Setting dangerous option enable_fbc - tainting kernel
[    3.265168] Setting dangerous option enable_guc - tainting kernel

Loading the firmware wasn't enabled by default until recently, which might explain the difference with older versions. You should be able to try turning that off to see if it makes a difference. I can't remember exactly where the option is, but it's the guc/huc stuff. 

Otherwise you can configure your machine to ignore the EDID provided by the display and either load your own (that you've maybe acquired yourself when it's working) or simply specify the settings yourself that would normally be provided by EDID.

---

### Post by ezerbib on 2020-07-16
Thanks for your response

- Yes I tried already what you suggest yesterday

1) I removed the guc/huc loading by removing the file ** /etc/modprobe.d/i915.conf **
[SIZE=1][FONT=courier new]root@localhost:~# cat /etc/modprobe.d/i915.conf 
options i915 enable_fbc=1
options i915 enable_guc=2

[SIZE=2]but the same behavior no video was shown when powercycle the device

2) I found in the net a procedure to force the EDID to be read but same no video when powercycle the device

[/SIZE]What I Did:

[SIZE=2]After powercycle the monitor I could get the EDID read[/SIZE]

sudo mkdir -p /lib/firmware/edid
sudo cp /sys/class/drm/card0-HDMI-A-1/edid /lib/firmware/edid/edid.bin




GRUB_CMDLINE_LINUX_DEFAULT="quiet splash drm_kms_helper.edid_firmware=HDMI-A-1:edid/edid.bin"

[SIZE=2]Afterwards ran update-grub2[/SIZE]

root@:~# cat /proc/cmdline

[SIZE=2]and check that the parameter was present: "[/SIZE][/FONT][/SIZE][SIZE=1][FONT=courier new][SIZE=1][FONT=courier new]drm_kms_helper.edid_firmware=HDMI-A-1:edid/edid.bin[/FONT][/SIZE]"

[SIZE=2]Additionally I used a initramfs hook to integrate EDID within the initramfs (/etc/initramfs-tools/hooks/include-edid-data)
to make it read at the initramfs[/SIZE]

#!/bin/sh

PREREQ="udev"
prereqs()
{
   echo "$PREREQ"
}

case $1 in
prereqs)
   prereqs
   exit 0
   ;;
esac

. /usr/share/initramfs-tools/hook-functions
# Begin real processing below this line

if [ ! -e "${DESTDIR}/lib/firmware/edid" ]; then
    mkdir -p "${DESTDIR}/lib/firmware/edid"
fi

if [ -r "/lib/firmware/edid/edid.bin" ]; then
   cp "/lib/firmware/edid/edid.bin" "${DESTDIR}/lib/firmware/edid/"
fi

manual_add_modules i915 radeon
exit 0

[SIZE=2]After that, I'd made it executable and ran: [/SIZE]
update-initramfs -u

[SIZE=2]
Any other though?
Regards...

[/SIZE][SIZE=2][/SIZE]
[/FONT][/SIZE]

---

### Post by Autodave on 2020-07-16
Always try another cable and a different output (if there is another one) and a different input to the TV.

I was just talking about this a couple days ago to another user who also had a Samsung TV.  I have seen recently a few Samsung TVs with this issue.  In fact, my neighbor's Samsung took out their laptop's motherboard *twice.*  After getting their TV fixed under warranty, their display works fine again.  And their 3rd motherboard is still alive.

---

