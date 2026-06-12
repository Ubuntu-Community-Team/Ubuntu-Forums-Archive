---
title: "H87 chipset driver, usb2 port not functioning correctly"
date: 2014-06-21
forum: Hardware
---

### Post by tstack77 on 2014-06-21
I posted this in the general forum and had no responses before narrowing the problem down to hardware. I have been unable to get ir-keytable to recognize ir-remote events (ir-keytable -t
) that are passed from a usb ir-dongle to the kernel. I have tested all variants of ubuntu and fedora, specifically loading a live environment and installing only ir-keytable. On the 5 computers that I tested I can get ir events recognized immediately on each except for the Asus H87i-Plus, which is my HTPC.

To address the issue I have tried:
-updating the kernel to 3.15.1-031501-generic
-update the BIOS to latest, v2001
-disable WOL and UEFI boot (solution for others with usb issues)
-emailed Asus, yet to hear back

The one oddity is that [openelec]("http://openelec.tv/home/what-is-openelec") (a custom linux distro for xbmc) worked out of the box, events recognized in both ir-keytable and lirc. The only explanation for it working is that I *think* that they use a modified driver.

Background commands:
```
$ dmesg
[    5.530777] Registered IR keymap rc-rc6-mce
[    5.530917] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc0/input5
[    5.531006] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc0
[    5.545653] IR NEC protocol handler initialized
[    5.555646] IR RC5(x) protocol handler initialized
[    5.560062] IR RC6 protocol handler initialized
[    5.569629] IR JVC protocol handler initialized
[    5.576739] IR Sony protocol handler initialized
[    5.584535] IR SANYO protocol handler initialized
[    5.722519] mceusb 3-2:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[    5.722525] mceusb 3-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
```

```
$ lsusb
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
```

```
$ ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event5) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Enabled protocols: NEC RC-5 RC-6 JVC SONY SANYO
        Extra capabilities: <access denied>
```

```
$ lsmod | grep "rc\|ir"
ir_sanyo_decoder       12839  0
ir_sony_decoder        12713  0
ir_lirc_codec          13021  0
lirc_dev               20018  1 ir_lirc_codec
ir_mce_kbd_decoder     13359  0
ir_sharp_decoder       12716  0
ir_jvc_decoder         12751  0
ir_rc5_decoder         12710  0
ir_rc6_decoder         12874  0
ir_nec_decoder         12915  0
intel_powerclamp       19099  0
rc_rc6_mce             12502  0
rc_core                28757  13 ir_sharp_decoder,lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
crct10dif_pclmul       14268  0
crc32_pclmul           13180  0
dm_mirror              22356  0
dm_region_hash         21010  1 dm_mirror
dm_log                 18527  2 dm_region_hash,dm_mirror
```

```
$cat /proc/bus/input/devices
I: Bus=0003 Vendor=0471 Product=0815 Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)"
P: Phys=usb-0000:00:14.0-2
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc0/input8
U: Uniq=
H: Handlers=kbd event5
B: PROP=0
B: EV=100013
B: KEY=0
B: MSC=10
```

```
$ sudo ir-keytable -c
Old keytable cleared
$ sudo ir-keytable -c -p NEC,RC-5,RC-6,JVC,SONY,SANYO -t
Testing events. Please, press CTRL-C to abort.
```
Nothing happens when any buttons on any remote are tested here with the Asus H87 board. Any ideas for a solution?

Thanks

---

