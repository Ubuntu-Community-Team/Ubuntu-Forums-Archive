---
title: "Fn Keys Samsung Series 9 90X3A not working"
date: 2011-05-07
forum: Hardware
---

### Post by coleman_ian on 2011-05-07
I'm running Ubuntu 10.10 32bit.

I have no response from the following function keys on my Samsung Series 9 laptop when I run the command

sudo /lib/udev/keymap -i input/event4

and by no response I mean there's no text come up in the terminal to indicate that a key was pressed.

(using keyboard definitions from /usr/include/linux/input.h with their #define values)

Fn F6 (something to do with powersaving, a leaf and a battery, maybe KEY_BATTERY 236)

Fn F7 (KEY_KBDILLUMDOWN 229)
Fn F8 (KEY_KBDILLUMUP 230)

Fn F12 (KEY_WLAN 238)

Additionally, I'm finding that the following buttons are not releasing (they continue to be 'pressed' after the key is no longer pressed)

Fn F2 (KEY_BRIGHTNESSDOWN 224)
Fn F3 (KEY_BRIGHTNESSUP 225)

Interestingly, and perhaps related, when I close the laptop lid and the system suspends, the keyboard backlights stay on.

Other resources that I have tried to use but have not come to conclusions are:

[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

/usr/share/doc/udev/README.keymap.txt


The samsung devices listed in /lib/udev/keymaps are
/lib/udev/keymaps/samsung-sq1us
/lib/udev/keymaps/samsung-sx20s
/lib/udev/keymaps/samsung-other


The details of samsung-other is

0x74 prog1 # User key
0x75 www
0x78 mail
0x82 switchvideomode # Fn+F4 CRT/LCD (high keycode: "displaytoggle")
0x83 battery # Fn+F2
0x84 prog1 # Fn+F5 backlight on/off
0x86 wlan # Fn+F9
0x88 brightnessup # Fn-Up
0x89 brightnessdown # Fn-Down
0xB1 prog2 # Fn+F7 run Samsung Magic Doctor (keypressed event is generated twice)
0xB3 prog3 # Fn+F8 switch power mode (battery/dynamic/performance)
0xB4 wlan # Fn+F9 (X60P)
0xF7 f22 # Fn+F10 Touchpad on
0xF9 f22 # Fn+F10 Touchpad off

If anyone can help with a resolution to this it would be appreciated.




Edit:

I loaded the ubuntu 11.04 live cd and observed the following messages:

For Fn F6
got scan code event 0x8D without a keycode event

Fn F7
got scan code event 0x97 without a keycode event

Fn F8
got scan code event 0x96 without a keycode event

Fn F12
got scan code event 0xD5 without a keycode event

---

### Post by jeppo on 2011-06-11
Same issue here with 11.04, Samsung 9 Series.  Looks like you got to the same place as me with this, any further luck?

---

### Post by coleman_ian on 2011-10-17
I created a new keymap file using the following command

```
sudo nano /lib/udev/keymaps/samsung-90X3A
```

and put the following content in it

```
0x96 kbdillumup #Fn-F8
0x97 kbdillumdown #Fn-F7
```

Then I edited the keymap rule file

```
sudo nano /lib/udev/rules.d/95-keymap.rules
```

and added the following line

```
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="90X3A", RUN+="keymap $name samsung-90X3A"
```

at line 139, or as shown in the extract below

```
...

ENV{DMI_VENDOR}=="MAXDATA", ATTR{[dmi/id]product_name}=="Pro 7000*", RUN+="keymap $name maxdata-pro_7000"

ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", RUN+="keymap $name samsung-other"
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="*SX20S*", RUN+="keymap $name samsung-sx20s"
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="SQ1US", RUN+="keymap $name samsung-sq1us"
ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="90X3A", RUN+="keymap $name samsung-90X3A"

ENV{DMI_VENDOR}=="TOSHIBA", ATTR{[dmi/id]product_name}=="SATELLITE A100", RUN+="keymap $name toshiba-satellite_a100"
...
```

The following command now shows the correct key code for each scan code when Fn+F7 or Fn+F8 is pressed, but the keyboard backlight is unaffected, so this is apparently only part of the step toward solving the problem.

```
sudo /lib/udev/keymap -i input/event4
```

Anyone got any other ideas on where to go from here?

---

### Post by l0b0 on 2011-10-17
Same issue on Ubuntu 11.04 64 bit. I wrote the following mail to linux-hotplug, but it never reached the mailing list. I tried three times, with or without attachments, and contacted the list admin, but no reply, and no entry in the list archives. Any tips on how to get through to the list? Anyway, for the record, here's the last attempt:

I've tried following the guides at [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting) and /usr/share/doc/udev/README.keymap.txt.gz, and following are the files I ended up with. After copying the map file and modifying /lib/udev/rules.d/95-keymap.rules I get the correct key names from ```
sudo /lib/udev/keymap -i input/event4
```, but none of them do anything at all. How do I make sure that at least wlan and kbdillumup/down work?

```
$ /lib/udev/findkeyboards
AT keyboard: input/event4
$ cat /sys/class/dmi/id/sys_vendor
SAMSUNG ELECTRONICS CO., LTD.
$ cat /sys/class/dmi/id/product_name
90X3A
```

samsung-90x3a.txt:
```
0xCE prog1 # Fn+F1 Unknown
0x8D prog3 # Fn+F6 Economy mode
0x97 kbdillumdown # Fn+F7 Keyboard background light down
0x96 kbdillumup # Fn+F8 Keyboard background light up
0xD5 wlan # Fn+F12 Wifi on/off
```

udev-db.txt:
```
P: /devices/LNXSYSTM:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00
E: MODALIAS=acpi:LNXSYSTM:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:00
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:01
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:02
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:03
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:04
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:05
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:05
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:06
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:06
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:07
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:07
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXPWRBN:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00
E: DRIVER=button
E: MODALIAS=acpi:LNXPWRBN:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
E: PRODUCT=19/0/1/0
E: NAME="Power Button"
E: PHYS="LNXPWRBN/button/input0"
E: PROP=0
E: EV=3
E: KEY=100000 0 0 0
E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
N: input/event3
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
E: MAJOR=13
E: MINOR=67
E: DEVNAME=/dev/input/event3
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: XKBVARIANT=dvorak-alt-intl
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/LNXSYSTM:00/device:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/ACPI0003:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/ACPI0003:00
E: DRIVER=ac
E: MODALIAS=acpi:ACPI0003:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ADP1
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ADP1
E: POWER_SUPPLY_NAME=ADP1
E: POWER_SUPPLY_ONLINE=0
E: SUBSYSTEM=power_supply

P: /devices/LNXSYSTM:00/device:00/INT340E:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/INT340E:00
E: MODALIAS=acpi:INT340E:PNP0C02:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00
E: DRIVER=pci_root
E: MODALIAS=acpi:PNP0A08:PNP0A03:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00
E: DRIVER=video
E: MODALIAS=acpi:LNXVIDEO:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:33
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:33
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:34
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:34
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:35
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:35
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:36
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:36
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:37
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:37
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:38
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:38
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:39
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:39
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:3a
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:3a
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
E: PRODUCT=19/0/6/0
E: NAME="Video Bus"
E: PHYS="LNXVIDEO/video/input0"
E: PROP=0
E: EV=3
E: KEY=3e000b 0 0 0 0 0 0 0
E: MODALIAS=input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6
N: input/event6
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6
E: MAJOR=13
E: MINOR=70
E: DEVNAME=/dev/input/event6
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: XKBVARIANT=dvorak-alt-intl
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:01
E: MODALIAS=acpi:PNP0C02:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/INT0800:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/INT0800:00
E: MODALIAS=acpi:INT0800:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/INT3F0D:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/INT3F0D:00
E: MODALIAS=acpi:INT3F0D:PNP0C02:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0000:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0000:00
E: MODALIAS=acpi:PNP0000:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0100:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0100:00
E: MODALIAS=acpi:PNP0100:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0103:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0103:00
E: MODALIAS=acpi:PNP0103:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0200:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0200:00
E: MODALIAS=acpi:PNP0200:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0303:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0303:00
E: MODALIAS=acpi:PNP0303:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0B00:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0B00:00
E: MODALIAS=acpi:PNP0B00:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C02:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C02:00
E: MODALIAS=acpi:PNP0C02:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C04:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C04:00
E: MODALIAS=acpi:PNP0C04:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00
E: DRIVER=ec
E: MODALIAS=acpi:PNP0C09:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/ACPI0008:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/ACPI0008:00
E: MODALIAS=acpi:ACPI0008:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/ACPI0008:00/PNP0C14:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/ACPI0008:00/PNP0C14:00
E: DRIVER=wmi
E: MODALIAS=acpi:PNP0C14:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/PNP0C0A:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/PNP0C0A:00
E: DRIVER=battery
E: MODALIAS=acpi:PNP0C0A:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/PNP0C0A:00/power_supply/BAT1
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C09:00/PNP0C0A:00/power_supply/BAT1
E: POWER_SUPPLY_NAME=BAT1
E: POWER_SUPPLY_STATUS=Discharging
E: POWER_SUPPLY_PRESENT=1
E: POWER_SUPPLY_TECHNOLOGY=Li-ion
E: POWER_SUPPLY_CYCLE_COUNT=0
E: POWER_SUPPLY_VOLTAGE_MIN_DESIGN=7400000
E: POWER_SUPPLY_VOLTAGE_NOW=7435000
E: POWER_SUPPLY_CURRENT_NOW=1825000
E: POWER_SUPPLY_CHARGE_FULL_DESIGN=6300000
E: POWER_SUPPLY_CHARGE_FULL=6300000
E: POWER_SUPPLY_CHARGE_NOW=1638000
E: SUBSYSTEM=power_supply
E: POWER_SUPPLY_MANUFACTURER=SAMSUNG Electronics

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0F13:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0F13:00
E: MODALIAS=acpi:PNP0F13:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:07
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:07
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:08
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:08
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:09
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:09
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0a
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0a
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0b
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0b
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0c
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0c
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0d
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0d
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0e
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/device:05/device:06/device:0e
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:12
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:12
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:13
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:13
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:14
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:14
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:15
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:15
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:16
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:16
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:17
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10/device:11/device:17
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:18
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:18
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/device:1a
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/device:1a
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1d
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1d
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1d/device:1e
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1d/device:1e
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1f
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1f
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1f/device:20
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1f/device:20
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:21
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:21
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:21/device:22
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:21/device:22
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/device:24
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/device:24
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25/device:26
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25/device:26
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27/device:28
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27/device:28
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29/device:2a
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29/device:2a
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2c
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2c
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/device:2e
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/device:2e
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2f
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2f
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:30
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:30
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:31
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:31
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:32
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:32
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C01:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C01:00
E: MODALIAS=acpi:PNP0C01:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00
E: DRIVER=button
E: MODALIAS=acpi:PNP0C0C:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
E: PRODUCT=19/0/1/0
E: NAME="Power Button"
E: PHYS="PNP0C0C/button/input0"
E: PROP=0
E: EV=3
E: KEY=100000 0 0 0
E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1
N: input/event1
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1
E: MAJOR=13
E: MINOR=65
E: DEVNAME=/dev/input/event1
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: XKBVARIANT=dvorak-alt-intl
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00
E: DRIVER=button
E: MODALIAS=acpi:PNP0C0D:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
E: PRODUCT=19/0/5/0
E: NAME="Lid Switch"
E: PHYS="PNP0C0D/button/input0"
E: PROP=0
E: EV=21
E: SW=1
E: MODALIAS=input:b0019v0000p0005e0000-e0,5,kramlsfw0,
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0/event0
N: input/event0
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0/event0
E: MAJOR=13
E: MINOR=64
E: DEVNAME=/dev/input/event0
E: SUBSYSTEM=input
E: ID_INPUT=1
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00
E: DRIVER=button
E: MODALIAS=acpi:PNP0C0E:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
E: PRODUCT=19/0/3/0
E: NAME="Sleep Button"
E: PHYS="PNP0C0E/button/input0"
E: PROP=0
E: EV=3
E: KEY=4000 0 0 0 0
E: MODALIAS=input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2
N: input/event2
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2
E: MAJOR=13
E: MINOR=66
E: DEVNAME=/dev/input/event2
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: XKBVARIANT=dvorak-alt-intl
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:00
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:01
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:02
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:03
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:04
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:05
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:05
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:06
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:06
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:07
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:07
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/LNXPOWER:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/LNXPOWER:00
E: DRIVER=power
E: MODALIAS=acpi:LNXPOWER:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/LNXPOWER:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/LNXPOWER:01
E: DRIVER=power
E: MODALIAS=acpi:LNXPOWER:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/LNXPOWER:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/LNXPOWER:02
E: DRIVER=power
E: MODALIAS=acpi:LNXPOWER:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/LNXPOWER:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/LNXPOWER:03
E: DRIVER=power
E: MODALIAS=acpi:LNXPOWER:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/LNXPOWER:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/LNXPOWER:04
E: DRIVER=power
E: MODALIAS=acpi:LNXPOWER:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/LNXTHERM:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/LNXTHERM:00
E: DRIVER=thermal
E: MODALIAS=acpi:LNXTHERM:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/LNXTHERM:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/LNXTHERM:01
E: DRIVER=thermal
E: MODALIAS=acpi:LNXTHERM:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/PNP0C0B:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/PNP0C0B:00
E: DRIVER=fan
E: MODALIAS=acpi:PNP0C0B:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/PNP0C0B:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/PNP0C0B:01
E: DRIVER=fan
E: MODALIAS=acpi:PNP0C0B:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/PNP0C0B:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/PNP0C0B:02
E: DRIVER=fan
E: MODALIAS=acpi:PNP0C0B:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/PNP0C0B:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/PNP0C0B:03
E: DRIVER=fan
E: MODALIAS=acpi:PNP0C0B:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:3b/PNP0C0B:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:3b/PNP0C0B:04
E: DRIVER=fan
E: MODALIAS=acpi:PNP0C0B:
E: SUBSYSTEM=acpi

P: /devices/breakpoint
E: UDEV_LOG=3
E: DEVPATH=/devices/breakpoint
E: SUBSYSTEM=event_source

P: /devices/cpu
E: UDEV_LOG=3
E: DEVPATH=/devices/cpu
E: SUBSYSTEM=event_source

P: /devices/pci0000:00/0000:00:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:00.0
E: DRIVER=agpgart-intel
E: PCI_CLASS=60000
E: PCI_ID=8086:0104
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:00.0
E: MODALIAS=pci:v00008086d00000104sv0000144Dsd0000C098bc06sc00i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:02.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0
E: DRIVER=i915
E: PCI_CLASS=30000
E: PCI_ID=8086:0116
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:02.0
E: MODALIAS=pci:v00008086d00000116sv0000144Dsd0000C098bc03sc00i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:02.0/drm/card0
N: dri/card0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0
E: MAJOR=226
E: MINOR=0
E: DEVNAME=/dev/dri/card0
E: DEVTYPE=drm_minor
E: SUBSYSTEM=drm
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1
E: SUBSYSTEM=drm

P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/i2c-14
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/i2c-14
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1
E: SUBSYSTEM=drm

P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
E: SUBSYSTEM=drm

P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
E: SUBSYSTEM=drm

P: /devices/pci0000:00/0000:00:02.0/drm/controlD64
N: dri/controlD64
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/controlD64
E: MAJOR=226
E: MINOR=64
E: DEVNAME=/dev/dri/controlD64
E: DEVTYPE=drm_minor
E: SUBSYSTEM=drm

P: /devices/pci0000:00/0000:00:02.0/graphics/fb0
N: fb0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/graphics/fb0
E: MAJOR=29
E: MINOR=0
E: DEVNAME=/dev/fb0
E: SUBSYSTEM=graphics

P: /devices/pci0000:00/0000:00:02.0/i2c-0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-0
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-1
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-10
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-10
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-11
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-11
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-12
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-12
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-13
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-13
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-2
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-3
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-4
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-5
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-6
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-7
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-7
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-8
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-8
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:02.0/i2c-9
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-9
E: SUBSYSTEM=i2c

P: /devices/pci0000:00/0000:00:16.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:16.0
E: PCI_CLASS=78000
E: PCI_ID=8086:1C3A
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:16.0
E: MODALIAS=pci:v00008086d00001C3Asv0000144Dsd0000C098bc07sc80i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1a.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0
E: DRIVER=ehci_hcd
E: PCI_CLASS=C0320
E: PCI_ID=8086:1C2D
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1a.0
E: MODALIAS=pci:v00008086d00001C2Dsv0000144Dsd0000C098bc0Csc03i20
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1a.0/usb1
N: bus/usb/001/001
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1
E: MAJOR=189
E: MINOR=0
E: DEVNAME=/dev/bus/usb/001/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: BUSNUM=001
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.38-11-generic_ehci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.38-11-generic\x20ehci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=EHCI_Host_Controller
E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
E: ID_MODEL_ID=0002
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.38-11-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1a.0
E: ID_SERIAL_SHORT=0000:00:1a.0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1
N: bus/usb/001/002
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1
E: MAJOR=189
E: MINOR=1
E: DEVNAME=/dev/bus/usb/001/002
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=8087/24/0
E: TYPE=9/0/1
E: BUSNUM=001
E: DEVNUM=002
E: SUBSYSTEM=usb
E: ID_VENDOR=8087
E: ID_VENDOR_ENC=8087
E: ID_VENDOR_ID=8087
E: ID_MODEL=0024
E: ID_MODEL_ENC=0024
E: ID_MODEL_ID=0024
E: ID_REVISION=0000
E: ID_SERIAL=8087_0024
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4
N: bus/usb/001/003
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4
E: MAJOR=189
E: MINOR=2
E: DEVNAME=/dev/bus/usb/001/003
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=2232/1009/9
E: TYPE=239/2/1
E: BUSNUM=001
E: DEVNUM=003
E: SUBSYSTEM=usb
E: ID_VENDOR=123
E: ID_VENDOR_ENC=123
E: ID_VENDOR_ID=2232
E: ID_MODEL=WebCam_SC-13HDL10931N
E: ID_MODEL_ENC=WebCam\x20SC-13HDL10931N
E: ID_MODEL_ID=1009
E: ID_REVISION=0009
E: ID_SERIAL=123_WebCam_SC-13HDL10931N
E: ID_BUS=usb
E: ID_USB_INTERFACES=:0e0100:0e0200:

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0
E: DEVTYPE=usb_interface
E: DRIVER=uvcvideo
E: PRODUCT=2232/1009/9
E: TYPE=239/2/1
E: INTERFACE=14/1/0
E: MODALIAS=usb:v2232p1009d0009dcEFdsc02dp01ic0Eisc01ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5
E: PRODUCT=3/2232/1009/9
E: NAME="WebCam SC-13HDL10931N"
E: PHYS="usb-0000:00:1a.0-1.4/button"
E: PROP=0
E: EV=3
E: KEY=100000 0 0 0 0 0 0
E: MODALIAS=input:b0003v2232p1009e0009-e0,1,kD4,ramlsfw
E: SUBSYSTEM=input

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5/event5
N: input/event5
S: input/by-id/usb-123_WebCam_SC-13HDL10931N-event-if00
S: input/by-path/pci-0000:00:1a.0-usb-0:1.4:1.0-event
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5/event5
E: MAJOR=13
E: MINOR=69
E: DEVNAME=/dev/input/event5
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: ID_VENDOR=123
E: ID_VENDOR_ENC=123
E: ID_VENDOR_ID=2232
E: ID_MODEL=WebCam_SC-13HDL10931N
E: ID_MODEL_ENC=WebCam\x20SC-13HDL10931N
E: ID_MODEL_ID=1009
E: ID_REVISION=0009
E: ID_SERIAL=123_WebCam_SC-13HDL10931N
E: ID_TYPE=video
E: ID_BUS=usb
E: ID_USB_INTERFACES=:0e0100:0e0200:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=uvcvideo
E: ID_PATH=pci-0000:00:1a.0-usb-0:1.4:1.0
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: XKBVARIANT=dvorak-alt-intl
E: DEVLINKS=/dev/input/by-id/usb-123_WebCam_SC-13HDL10931N-event-if00 /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.4:1.0-event

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/video4linux/video0
N: video0
S: v4l/by-id/usb-123_WebCam_SC-13HDL10931N-video-index0
S: v4l/by-path/pci-0000:00:1a.0-usb-0:1.4:1.0-video-index0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/video4linux/video0
E: MAJOR=81
E: MINOR=0
E: DEVNAME=/dev/video0
E: SUBSYSTEM=video4linux
E: ID_V4L_VERSION=2
E: ID_V4L_PRODUCT=WebCam SC-13HDL10931N
E: ID_V4L_CAPABILITIES=:capture:
E: ID_VENDOR=123
E: ID_VENDOR_ENC=123
E: ID_VENDOR_ID=2232
E: ID_MODEL=WebCam_SC-13HDL10931N
E: ID_MODEL_ENC=WebCam\x20SC-13HDL10931N
E: ID_MODEL_ID=1009
E: ID_REVISION=0009
E: ID_SERIAL=123_WebCam_SC-13HDL10931N
E: ID_TYPE=video
E: ID_BUS=usb
E: ID_USB_INTERFACES=:0e0100:0e0200:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=uvcvideo
E: ID_PATH=pci-0000:00:1a.0-usb-0:1.4:1.0
E: DEVLINKS=/dev/v4l/by-id/usb-123_WebCam_SC-13HDL10931N-video-index0 /dev/v4l/by-path/pci-0000:00:1a.0-usb-0:1.4:1.0-video-index0
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1
E: DEVTYPE=usb_interface
E: DRIVER=uvcvideo
E: PRODUCT=2232/1009/9
E: TYPE=239/2/1
E: INTERFACE=14/2/0
E: MODALIAS=usb:v2232p1009d0009dcEFdsc02dp01ic0Eisc02ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: PRODUCT=8087/24/0
E: TYPE=9/0/1
E: INTERFACE=9/0/0
E: MODALIAS=usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.0/usbmon/usbmon1
N: usbmon1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usbmon/usbmon1
E: MAJOR=252
E: MINOR=1
E: DEVNAME=/dev/usbmon1
E: SUBSYSTEM=usbmon

P: /devices/pci0000:00/0000:00:1b.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0
E: DRIVER=HDA Intel
E: PCI_CLASS=40300
E: PCI_ID=8086:1C20
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1b.0
E: MODALIAS=pci:v00008086d00001C20sv0000144Dsd0000C098bc04sc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1b.0/sound/card0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
E: SUBSYSTEM=sound
E: SOUND_INITIALIZED=1
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_MODEL_FROM_DATABASE=6 Series Chipset Family High Definition Audio Controller
E: ID_BUS=pci
E: ID_VENDOR_ID=0x8086
E: ID_MODEL_ID=0x1c20
E: ID_PATH=pci-0000:00:1b.0
E: SOUND_FORM_FACTOR=internal

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
N: snd/hwC0D0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
E: MAJOR=116
E: MINOR=6
E: DEVNAME=/dev/snd/hwC0D0
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D3
N: snd/hwC0D3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D3
E: MAJOR=116
E: MINOR=5
E: DEVNAME=/dev/snd/hwC0D3
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
E: PRODUCT=0/0/0/0
E: NAME="HDA Intel PCH Mic"
E: PHYS="ALSA"
E: PROP=0
E: EV=21
E: SW=10
E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw4,
E: SUBSYSTEM=input

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input8/event8
N: input/event8
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8/event8
E: MAJOR=13
E: MINOR=72
E: DEVNAME=/dev/input/event8
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_PATH=pci-0000:00:1b.0
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
E: PRODUCT=0/0/0/0
E: NAME="HDA Intel PCH Headphone"
E: PHYS="ALSA"
E: PROP=0
E: EV=21
E: SW=4
E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw2,
E: SUBSYSTEM=input

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input9/event9
N: input/event9
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9/event9
E: MAJOR=13
E: MINOR=73
E: DEVNAME=/dev/input/event9
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_PATH=pci-0000:00:1b.0
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
N: snd/pcmC0D0c
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
E: MAJOR=116
E: MINOR=4
E: DEVNAME=/dev/snd/pcmC0D0c
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
N: snd/pcmC0D0p
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
E: MAJOR=116
E: MINOR=3
E: DEVNAME=/dev/snd/pcmC0D0p
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D3p
N: snd/pcmC0D3p
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D3p
E: MAJOR=116
E: MINOR=2
E: DEVNAME=/dev/snd/pcmC0D3p
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
N: snd/controlC0
S: snd/by-path/pci-0000:00:1b.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
E: MAJOR=116
E: MINOR=7
E: DEVNAME=/dev/snd/controlC0
E: SUBSYSTEM=sound
E: ID_PATH=pci-0000:00:1b.0
E: DEVLINKS=/dev/snd/by-path/pci-0000:00:1b.0
E: TAGS=:udev-acl:

P: /devices/pci0000:00/0000:00:1c.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0
E: DRIVER=pcieport
E: PCI_CLASS=60400
E: PCI_ID=8086:1C10
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1c.0
E: MODALIAS=pci:v00008086d00001C10sv0000144Dsd0000C098bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:01:00.0
E: DRIVER=iwlagn
E: PCI_CLASS=28000
E: PCI_ID=8086:0091
E: PCI_SUBSYS_ID=8086:5201
E: PCI_SLOT_NAME=0000:01:00.0
E: MODALIAS=pci:v00008086d00000091sv00008086sd00005201bc02sc80i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ieee80211/phy0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ieee80211/phy0
E: SUBSYSTEM=ieee80211

P: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ieee80211/phy0/rfkill1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ieee80211/phy0/rfkill1
E: RFKILL_NAME=phy0
E: RFKILL_TYPE=wlan
E: RFKILL_STATE=1
E: SUBSYSTEM=rfkill

P: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan1
E: DEVTYPE=wlan
E: INTERFACE=wlan1
E: IFINDEX=3
E: SUBSYSTEM=net
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_MODEL_FROM_DATABASE=Centrino Advanced-N 6230
E: ID_BUS=pci
E: ID_VENDOR_ID=0x8086
E: ID_MODEL_ID=0x0091
E: ID_MM_CANDIDATE=1

P: /devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1c.3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3
E: DRIVER=pcieport
E: PCI_CLASS=60400
E: PCI_ID=8086:1C16
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1c.3
E: MODALIAS=pci:v00008086d00001C16sv0000144Dsd0000C098bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.3/0000:02:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:02:00.0
E: DRIVER=r8169
E: PCI_CLASS=20000
E: PCI_ID=10EC:8168
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:02:00.0
E: MODALIAS=pci:v000010ECd00008168sv0000144Dsd0000C098bc02sc00i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/eth1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/eth1
E: INTERFACE=eth1
E: IFINDEX=2
E: SUBSYSTEM=net
E: ID_VENDOR_FROM_DATABASE=Realtek Semiconductor Co., Ltd.
E: ID_MODEL_FROM_DATABASE=RTL8111/8168B PCI Express Gigabit Ethernet controller
E: ID_BUS=pci
E: ID_VENDOR_ID=0x10ec
E: ID_MODEL_ID=0x8168
E: ID_MM_CANDIDATE=1

P: /devices/pci0000:00/0000:00:1c.3/pci_bus/0000:02
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/pci_bus/0000:02
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1c.4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.4
E: DRIVER=pcieport
E: PCI_CLASS=60400
E: PCI_ID=8086:1C18
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1c.4
E: MODALIAS=pci:v00008086d00001C18sv0000144Dsd0000C098bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.4/0000:03:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:03:00.0
E: DRIVER=xhci_hcd
E: PCI_CLASS=C0330
E: PCI_ID=1033:0194
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:03:00.0
E: MODALIAS=pci:v00001033d00000194sv0000144Dsd0000C098bc0Csc03i30
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3
N: bus/usb/003/001
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3
E: MAJOR=189
E: MINOR=256
E: DEVNAME=/dev/bus/usb/003/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=1d6b/3/206
E: TYPE=9/0/3
E: BUSNUM=003
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.38-11-generic_xhci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.38-11-generic\x20xhci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=xHCI_Host_Controller
E: ID_MODEL_ENC=xHCI\x20Host\x20Controller
E: ID_MODEL_ID=0003
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.38-11-generic_xhci_hcd_xHCI_Host_Controller_0000:03:00.0
E: ID_SERIAL_SHORT=0000:03:00.0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:

P: /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: PRODUCT=1d6b/3/206
E: TYPE=9/0/3
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0003d0206dc09dsc00dp03ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usbmon/usbmon3
N: usbmon3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usbmon/usbmon3
E: MAJOR=252
E: MINOR=3
E: DEVNAME=/dev/usbmon3
E: SUBSYSTEM=usbmon

P: /devices/pci0000:00/0000:00:1c.4/pci_bus/0000:03
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.4/pci_bus/0000:03
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1d.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0
E: DRIVER=ehci_hcd
E: PCI_CLASS=C0320
E: PCI_ID=8086:1C26
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1d.0
E: MODALIAS=pci:v00008086d00001C26sv0000144Dsd0000C098bc0Csc03i20
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1d.0/usb2
N: bus/usb/002/001
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2
E: MAJOR=189
E: MINOR=128
E: DEVNAME=/dev/bus/usb/002/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: BUSNUM=002
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.38-11-generic_ehci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.38-11-generic\x20ehci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=EHCI_Host_Controller
E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
E: ID_MODEL_ID=0002
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.38-11-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1d.0
E: ID_SERIAL_SHORT=0000:00:1d.0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1
N: bus/usb/002/002
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1
E: MAJOR=189
E: MINOR=129
E: DEVNAME=/dev/bus/usb/002/002
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=8087/24/0
E: TYPE=9/0/1
E: BUSNUM=002
E: DEVNUM=002
E: SUBSYSTEM=usb
E: ID_VENDOR=8087
E: ID_VENDOR_ENC=8087
E: ID_VENDOR_ID=8087
E: ID_MODEL=0024
E: ID_MODEL_ENC=0024
E: ID_MODEL_ID=0024
E: ID_REVISION=0000
E: ID_SERIAL=8087_0024
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3
N: bus/usb/002/003
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3
E: MAJOR=189
E: MINOR=130
E: DEVNAME=/dev/bus/usb/002/003
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=8086/189/6919
E: TYPE=224/1/1
E: BUSNUM=002
E: DEVNUM=003
E: SUBSYSTEM=usb
E: ID_VENDOR=8086
E: ID_VENDOR_ENC=8086
E: ID_VENDOR_ID=8086
E: ID_MODEL=0189
E: ID_MODEL_ENC=0189
E: ID_MODEL_ID=0189
E: ID_REVISION=6919
E: ID_SERIAL=8086_0189
E: ID_BUS=usb
E: ID_USB_INTERFACES=:e00101:

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0
E: DEVTYPE=usb_interface
E: DRIVER=btusb
E: PRODUCT=8086/189/6919
E: TYPE=224/1/1
E: INTERFACE=224/1/1
E: MODALIAS=usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0
E: DEVTYPE=host
E: SUBSYSTEM=bluetooth

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/rfkill50
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/rfkill50
E: RFKILL_NAME=hci0
E: RFKILL_TYPE=bluetooth
E: RFKILL_STATE=0
E: SUBSYSTEM=rfkill

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1
E: DEVTYPE=usb_interface
E: DRIVER=btusb
E: PRODUCT=8086/189/6919
E: TYPE=224/1/1
E: INTERFACE=224/1/1
E: MODALIAS=usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: PRODUCT=8087/24/0
E: TYPE=9/0/1
E: INTERFACE=9/0/0
E: MODALIAS=usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
N: usbmon2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
E: MAJOR=252
E: MINOR=2
E: DEVNAME=/dev/usbmon2
E: SUBSYSTEM=usbmon

P: /devices/pci0000:00/0000:00:1f.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.0
E: PCI_CLASS=60100
E: PCI_ID=8086:1C49
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1f.0
E: MODALIAS=pci:v00008086d00001C49sv0000144Dsd0000C098bc06sc01i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1f.2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2
E: DRIVER=ahci
E: PCI_CLASS=10601
E: PCI_ID=8086:1C03
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1f.2
E: MODALIAS=pci:v00008086d00001C03sv0000144Dsd0000C098bc01sc06i01
E: SUBSYSTEM=pci
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_MODEL_FROM_DATABASE=6 Series Chipset Family 6 port SATA AHCI Controller

P: /devices/pci0000:00/0000:00:1f.2/ata1/ata_port/ata1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/ata_port/ata1
E: SUBSYSTEM=ata_port

P: /devices/pci0000:00/0000:00:1f.2/ata1/link1/ata_link/link1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/link1/ata_link/link1
E: SUBSYSTEM=ata_link

P: /devices/pci0000:00/0000:00:1f.2/ata1/link1/dev1.0/ata_device/dev1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/link1/dev1.0/ata_device/dev1.0
E: SUBSYSTEM=ata_device

P: /devices/pci0000:00/0000:00:1f.2/ata2/ata_port/ata2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata2/ata_port/ata2
E: SUBSYSTEM=ata_port

P: /devices/pci0000:00/0000:00:1f.2/ata2/link2/ata_link/link2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata2/link2/ata_link/link2
E: SUBSYSTEM=ata_link

P: /devices/pci0000:00/0000:00:1f.2/ata2/link2/dev2.0/ata_device/dev2.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata2/link2/dev2.0/ata_device/dev2.0
E: SUBSYSTEM=ata_device

P: /devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
E: SUBSYSTEM=ata_port

P: /devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
E: SUBSYSTEM=ata_link

P: /devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
E: SUBSYSTEM=ata_device

P: /devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
E: SUBSYSTEM=ata_port

P: /devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
E: SUBSYSTEM=ata_link

P: /devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
E: SUBSYSTEM=ata_device

P: /devices/pci0000:00/0000:00:1f.2/ata5/ata_port/ata5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata5/ata_port/ata5
E: SUBSYSTEM=ata_port

P: /devices/pci0000:00/0000:00:1f.2/ata5/link5/ata_link/link5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata5/link5/ata_link/link5
E: SUBSYSTEM=ata_link

P: /devices/pci0000:00/0000:00:1f.2/ata5/link5/dev5.0/ata_device/dev5.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata5/link5/dev5.0/ata_device/dev5.0
E: SUBSYSTEM=ata_device

P: /devices/pci0000:00/0000:00:1f.2/ata6/ata_port/ata6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata6/ata_port/ata6
E: SUBSYSTEM=ata_port

P: /devices/pci0000:00/0000:00:1f.2/ata6/link6/ata_link/link6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata6/link6/ata_link/link6
E: SUBSYSTEM=ata_link

P: /devices/pci0000:00/0000:00:1f.2/ata6/link6/dev6.0/ata_device/dev6.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata6/link6/dev6.0/ata_device/dev6.0
E: SUBSYSTEM=ata_device

P: /devices/pci0000:00/0000:00:1f.2/host0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
E: DEVTYPE=scsi_target
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
E: DEVTYPE=scsi_device
E: DRIVER=sd
E: MODALIAS=scsi:t-0x00
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
N: sda
S: disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900
S: disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
E: MAJOR=8
E: MINOR=0
E: DEVNAME=/dev/sda
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_ATA=1
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=SAMSUNG_MZMPA128HMFU-00000
E: ID_MODEL_ENC=SAMSUNG\x20MZMPA128HMFU-00000\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=AXM170Q1
E: ID_SERIAL=SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900
E: ID_SERIAL_SHORT=S0R5NYAB525900
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_ROTATION_RATE_RPM=0
E: ID_SCSI_COMPAT=SATA_SAMSUNG_MZMPA12S0R5NYAB525900
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_PART_TABLE_TYPE=dos
E: UDISKS_PRESENTATION_NOPOLICY=0
E: UDISKS_PARTITION_TABLE=1
E: UDISKS_PARTITION_TABLE_SCHEME=mbr
E: UDISKS_PARTITION_TABLE_COUNT=4
E: UDISKS_ATA_SMART_IS_AVAILABLE=1
E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900 /dev/disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
N: sda1
S: disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part1
S: disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part1
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1
S: disk/by-uuid/059f3e88-896e-41c0-aee2-c9567a028138
S: root
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
E: MAJOR=8
E: MINOR=1
E: DEVNAME=/dev/sda1
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_ATA=1
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=SAMSUNG_MZMPA128HMFU-00000
E: ID_MODEL_ENC=SAMSUNG\x20MZMPA128HMFU-00000\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=AXM170Q1
E: ID_SERIAL=SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900
E: ID_SERIAL_SHORT=S0R5NYAB525900
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_ROTATION_RATE_RPM=0
E: ID_SCSI_COMPAT=SATA_SAMSUNG_MZMPA12S0R5NYAB525900
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_PART_TABLE_TYPE=dos
E: ID_FS_UUID=059f3e88-896e-41c0-aee2-c9567a028138
E: ID_FS_UUID_ENC=059f3e88-896e-41c0-aee2-c9567a028138
E: ID_FS_VERSION=1.0
E: ID_FS_TYPE=ext4
E: ID_FS_USAGE=filesystem
E: UDISKS_PRESENTATION_NOPOLICY=0
E: UDISKS_PARTITION=1
E: UDISKS_PARTITION_SCHEME=mbr
E: UDISKS_PARTITION_NUMBER=1
E: UDISKS_PARTITION_TYPE=0x83
E: UDISKS_PARTITION_SIZE=49999249408
E: UDISKS_PARTITION_FLAGS=boot
E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
E: UDISKS_PARTITION_OFFSET=1048576
E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part1 /dev/disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part1 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1 /dev/disk/by-uuid/059f3e88-896e-41c0-aee2-c9567a028138 /dev/root

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
N: sda2
S: disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part2
S: disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part2
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
E: MAJOR=8
E: MINOR=2
E: DEVNAME=/dev/sda2
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_ATA=1
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=SAMSUNG_MZMPA128HMFU-00000
E: ID_MODEL_ENC=SAMSUNG\x20MZMPA128HMFU-00000\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=AXM170Q1
E: ID_SERIAL=SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900
E: ID_SERIAL_SHORT=S0R5NYAB525900
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_ROTATION_RATE_RPM=0
E: ID_SCSI_COMPAT=SATA_SAMSUNG_MZMPA12S0R5NYAB525900
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_PART_TABLE_TYPE=dos
E: UDISKS_PRESENTATION_NOPOLICY=0
E: UDISKS_PARTITION=1
E: UDISKS_PARTITION_SCHEME=mbr
E: UDISKS_PARTITION_NUMBER=2
E: UDISKS_PARTITION_TYPE=0x05
E: UDISKS_PARTITION_SIZE=78033978368
E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
E: UDISKS_PARTITION_OFFSET=50001345536
E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part2 /dev/disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part2 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5
N: sda5
S: disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part5
S: disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part5
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5
S: disk/by-uuid/82c506f3-e452-421b-b024-da0195edf00a
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5
E: MAJOR=8
E: MINOR=5
E: DEVNAME=/dev/sda5
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_ATA=1
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=SAMSUNG_MZMPA128HMFU-00000
E: ID_MODEL_ENC=SAMSUNG\x20MZMPA128HMFU-00000\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=AXM170Q1
E: ID_SERIAL=SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900
E: ID_SERIAL_SHORT=S0R5NYAB525900
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_ROTATION_RATE_RPM=0
E: ID_SCSI_COMPAT=SATA_SAMSUNG_MZMPA12S0R5NYAB525900
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_PART_TABLE_TYPE=dos
E: ID_FS_UUID=82c506f3-e452-421b-b024-da0195edf00a
E: ID_FS_UUID_ENC=82c506f3-e452-421b-b024-da0195edf00a
E: ID_FS_VERSION=2
E: ID_FS_TYPE=swap
E: ID_FS_USAGE=other
E: UDISKS_PRESENTATION_NOPOLICY=0
E: UDISKS_PARTITION=1
E: UDISKS_PARTITION_SCHEME=mbr
E: UDISKS_PARTITION_NUMBER=5
E: UDISKS_PARTITION_TYPE=0x82
E: UDISKS_PARTITION_SIZE=9999220736
E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
E: UDISKS_PARTITION_OFFSET=50001346560
E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part5 /dev/disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part5 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5 /dev/disk/by-uuid/82c506f3-e452-421b-b024-da0195edf00a

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6
N: sda6
S: disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part6
S: disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part6
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6
S: disk/by-uuid/95c57892-2007-4aea-baac-2a76263c147c
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6
E: MAJOR=8
E: MINOR=6
E: DEVNAME=/dev/sda6
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_ATA=1
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=SAMSUNG_MZMPA128HMFU-00000
E: ID_MODEL_ENC=SAMSUNG\x20MZMPA128HMFU-00000\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=AXM170Q1
E: ID_SERIAL=SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900
E: ID_SERIAL_SHORT=S0R5NYAB525900
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=6
E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_ROTATION_RATE_RPM=0
E: ID_SCSI_COMPAT=SATA_SAMSUNG_MZMPA12S0R5NYAB525900
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_PART_TABLE_TYPE=dos
E: ID_FS_UUID=95c57892-2007-4aea-baac-2a76263c147c
E: ID_FS_UUID_ENC=95c57892-2007-4aea-baac-2a76263c147c
E: ID_FS_VERSION=1.0
E: ID_FS_TYPE=ext4
E: ID_FS_USAGE=filesystem
E: UDISKS_PRESENTATION_NOPOLICY=0
E: UDISKS_PARTITION=1
E: UDISKS_PARTITION_SCHEME=mbr
E: UDISKS_PARTITION_NUMBER=6
E: UDISKS_PARTITION_TYPE=0x83
E: UDISKS_PARTITION_SIZE=68033708032
E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
E: UDISKS_PARTITION_OFFSET=60001615872
E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_MZMPA128HMFU-00000_S0R5NYAB525900-part6 /dev/disk/by-id/scsi-SATA_SAMSUNG_MZMPA12S0R5NYAB525900-part6 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6 /dev/disk/by-uuid/95c57892-2007-4aea-baac-2a76263c147c

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
N: bsg/0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
E: MAJOR=253
E: MINOR=0
E: DEVNAME=/dev/bsg/0:0:0:0
E: SUBSYSTEM=bsg

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
E: SUBSYSTEM=scsi_device

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
E: SUBSYSTEM=scsi_disk

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
N: sg0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
E: MAJOR=21
E: MINOR=0
E: DEVNAME=/dev/sg0
E: SUBSYSTEM=scsi_generic

P: /devices/pci0000:00/0000:00:1f.2/host1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host4/scsi_host/host4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/scsi_host/host4
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host5
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host5/scsi_host/host5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host5/scsi_host/host5
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.3
E: PCI_CLASS=C0500
E: PCI_ID=8086:1C22
E: PCI_SUBSYS_ID=144D:C098
E: PCI_SLOT_NAME=0000:00:1f.3
E: MODALIAS=pci:v00008086d00001C22sv0000144Dsd0000C098bc0Csc05i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/pci_bus/0000:00
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/pci_bus/0000:00
E: SUBSYSTEM=pci_bus

P: /devices/platform/Fixed MDIO bus.0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/Fixed MDIO bus.0
E: MODALIAS=platform:Fixed MDIO bus
E: SUBSYSTEM=platform

P: /devices/platform/Fixed MDIO bus.0/mdio_bus/0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/Fixed MDIO bus.0/mdio_bus/0
E: SUBSYSTEM=mdio_bus

P: /devices/platform/eisa.0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/eisa.0
E: MODALIAS=platform:eisa
E: SUBSYSTEM=platform

P: /devices/platform/i8042
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042
E: DRIVER=i8042
E: MODALIAS=platform:i8042
E: SUBSYSTEM=platform

P: /devices/platform/i8042/serio0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio0
E: DRIVER=atkbd
E: SERIO_TYPE=06
E: SERIO_PROTO=00
E: SERIO_ID=00
E: SERIO_EXTRA=00
E: MODALIAS=serio:ty06pr00id00ex00
E: SUBSYSTEM=serio
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/platform/i8042/serio0/input/input4
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio0/input/input4
E: PRODUCT=11/1/1/ab41
E: NAME="AT Translated Set 2 keyboard"
E: PHYS="isa0060/serio0/input0"
E: PROP=0
E: EV=120013
E: KEY=500f 2000403 3803078 f870d001 feffffdf fbefffff ffffffff fffffffe
E: MSC=10
E: LED=7
E: MODALIAS=input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw
E: SUBSYSTEM=input

P: /devices/platform/i8042/serio0/input/input4/event4
N: input/event4
S: input/by-path/platform-i8042-serio-0-event-kbd
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio0/input/input4/event4
E: MAJOR=13
E: MINOR=68
E: DEVNAME=/dev/input/event4
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: ID_INPUT_KEYBOARD=1
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-0
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: XKBVARIANT=dvorak-alt-intl
E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-0-event-kbd
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.

P: /devices/platform/i8042/serio1
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1
E: DRIVER=psmouse
E: SERIO_TYPE=01
E: SERIO_PROTO=00
E: SERIO_ID=00
E: SERIO_EXTRA=00
E: MODALIAS=serio:ty01pr00id00ex00
E: SUBSYSTEM=serio

P: /devices/platform/i8042/serio1/input/input7
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input7
E: PRODUCT=11/2/7/1b1
E: NAME="SynPS/2 Synaptics TouchPad"
E: PHYS="isa0060/serio1/input0"
E: PROP=5
E: EV=b
E: KEY=6420 0 10000 0 0 0 0 0 0 0 0
E: ABS=11000003
E: MODALIAS=input:b0011v0002p0007e01B1-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,1C,mlsfw
E: SUBSYSTEM=input

P: /devices/platform/i8042/serio1/input/input7/event7
N: input/event7
S: input/by-path/platform-i8042-serio-1-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input7/event7
E: MAJOR=13
E: MINOR=71
E: DEVNAME=/dev/input/event7
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_TOUCHPAD=1
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-1
E: DMI_VENDOR=SAMSUNG ELECTRONICS CO., LTD.
E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-event-mouse

P: /devices/platform/i8042/serio1/input/input7/mouse0
N: input/mouse0
S: input/by-path/platform-i8042-serio-1-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input7/mouse0
E: MAJOR=13
E: MINOR=32
E: DEVNAME=/dev/input/mouse0
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_TOUCHPAD=1
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-1
E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-mouse

P: /devices/platform/pcspkr
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/pcspkr
E: MODALIAS=platform:pcspkr
E: SUBSYSTEM=platform

P: /devices/platform/reg-dummy
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/reg-dummy
E: MODALIAS=platform:reg-dummy
E: SUBSYSTEM=platform

P: /devices/platform/regulatory.0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/regulatory.0
E: MODALIAS=platform:regulatory
E: SUBSYSTEM=platform

P: /devices/platform/serial8250
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250
E: DRIVER=serial8250
E: MODALIAS=platform:serial8250
E: SUBSYSTEM=platform

P: /devices/platform/serial8250/tty/ttyS0
N: ttyS0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
E: MAJOR=4
E: MINOR=64
E: DEVNAME=/dev/ttyS0
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS1
N: ttyS1
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
E: MAJOR=4
E: MINOR=65
E: DEVNAME=/dev/ttyS1
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS10
N: ttyS10
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS10
E: MAJOR=4
E: MINOR=74
E: DEVNAME=/dev/ttyS10
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS11
N: ttyS11
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS11
E: MAJOR=4
E: MINOR=75
E: DEVNAME=/dev/ttyS11
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS12
N: ttyS12
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS12
E: MAJOR=4
E: MINOR=76
E: DEVNAME=/dev/ttyS12
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS13
N: ttyS13
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS13
E: MAJOR=4
E: MINOR=77
E: DEVNAME=/dev/ttyS13
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS14
N: ttyS14
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS14
E: MAJOR=4
E: MINOR=78
E: DEVNAME=/dev/ttyS14
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS15
N: ttyS15
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS15
E: MAJOR=4
E: MINOR=79
E: DEVNAME=/dev/ttyS15
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS16
N: ttyS16
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS16
E: MAJOR=4
E: MINOR=80
E: DEVNAME=/dev/ttyS16
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS17
N: ttyS17
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS17
E: MAJOR=4
E: MINOR=81
E: DEVNAME=/dev/ttyS17
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS18
N: ttyS18
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS18
E: MAJOR=4
E: MINOR=82
E: DEVNAME=/dev/ttyS18
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS19
N: ttyS19
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS19
E: MAJOR=4
E: MINOR=83
E: DEVNAME=/dev/ttyS19
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS2
N: ttyS2
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
E: MAJOR=4
E: MINOR=66
E: DEVNAME=/dev/ttyS2
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS20
N: ttyS20
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS20
E: MAJOR=4
E: MINOR=84
E: DEVNAME=/dev/ttyS20
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS21
N: ttyS21
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS21
E: MAJOR=4
E: MINOR=85
E: DEVNAME=/dev/ttyS21
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS22
N: ttyS22
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS22
E: MAJOR=4
E: MINOR=86
E: DEVNAME=/dev/ttyS22
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS23
N: ttyS23
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS23
E: MAJOR=4
E: MINOR=87
E: DEVNAME=/dev/ttyS23
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS24
N: ttyS24
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS24
E: MAJOR=4
E: MINOR=88
E: DEVNAME=/dev/ttyS24
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS25
N: ttyS25
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS25
E: MAJOR=4
E: MINOR=89
E: DEVNAME=/dev/ttyS25
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS26
N: ttyS26
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS26
E: MAJOR=4
E: MINOR=90
E: DEVNAME=/dev/ttyS26
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS27
N: ttyS27
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS27
E: MAJOR=4
E: MINOR=91
E: DEVNAME=/dev/ttyS27
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS28
N: ttyS28
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS28
E: MAJOR=4
E: MINOR=92
E: DEVNAME=/dev/ttyS28
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS29
N: ttyS29
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS29
E: MAJOR=4
E: MINOR=93
E: DEVNAME=/dev/ttyS29
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS3
N: ttyS3
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
E: MAJOR=4
E: MINOR=67
E: DEVNAME=/dev/ttyS3
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS30
N: ttyS30
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS30
E: MAJOR=4
E: MINOR=94
E: DEVNAME=/dev/ttyS30
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS31
N: ttyS31
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS31
E: MAJOR=4
E: MINOR=95
E: DEVNAME=/dev/ttyS31
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS4
N: ttyS4
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS4
E: MAJOR=4
E: MINOR=68
E: DEVNAME=/dev/ttyS4
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS5
N: ttyS5
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS5
E: MAJOR=4
E: MINOR=69
E: DEVNAME=/dev/ttyS5
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS6
N: ttyS6
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS6
E: MAJOR=4
E: MINOR=70
E: DEVNAME=/dev/ttyS6
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS7
N: ttyS7
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS7
E: MAJOR=4
E: MINOR=71
E: DEVNAME=/dev/ttyS7
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS8
N: ttyS8
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS8
E: MAJOR=4
E: MINOR=72
E: DEVNAME=/dev/ttyS8
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/serial8250/tty/ttyS9
N: ttyS9
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS9
E: MAJOR=4
E: MINOR=73
E: DEVNAME=/dev/ttyS9
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/platform/vboxdrv.0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/vboxdrv.0
E: DRIVER=vboxdrv
E: MODALIAS=platform:vboxdrv
E: SUBSYSTEM=platform

P: /devices/pnp0/00:00
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:00
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:01
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:01
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:02
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:02
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:03
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:03
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:04
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:04
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:05
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:05
E: DRIVER=system
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:06
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:06
E: DRIVER=rtc_cmos
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:06/rtc/rtc0
N: rtc0
S: rtc
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:06/rtc/rtc0
E: MAJOR=254
E: MINOR=0
E: DEVNAME=/dev/rtc0
E: SUBSYSTEM=rtc
E: DEVLINKS=/dev/rtc

P: /devices/pnp0/00:07
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:07
E: DRIVER=system
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:08
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:08
E: DRIVER=i8042 kbd
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:09
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:09
E: DRIVER=i8042 aux
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:0a
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:0a
E: DRIVER=system
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:0b
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:0b
E: DRIVER=system
E: SUBSYSTEM=pnp

P: /devices/software
E: UDEV_LOG=3
E: DEVPATH=/devices/software
E: SUBSYSTEM=event_source

P: /devices/tracepoint
E: UDEV_LOG=3
E: DEVPATH=/devices/tracepoint
E: SUBSYSTEM=event_source

P: /devices/virtual/backlight/acpi_video0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/backlight/acpi_video0
E: SUBSYSTEM=backlight

P: /devices/virtual/bdi/0:20
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/0:20
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/0:21
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/0:21
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:0
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:1
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:10
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:10
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:11
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:12
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:13
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:13
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:14
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:14
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:15
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:15
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:2
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:3
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:4
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:5
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:6
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:7
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:8
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:9
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:0
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:1
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:2
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:3
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:4
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:5
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:6
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:7
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/8:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/8:0
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/default
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/default
E: SUBSYSTEM=bdi

P: /devices/virtual/block/loop0
N: loop0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop0
E: MAJOR=7
E: MINOR=0
E: DEVNAME=/dev/loop0
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/loop1
N: loop1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop1
E: MAJOR=7
E: MINOR=1
E: DEVNAME=/dev/loop1
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/loop2
N: loop2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop2
E: MAJOR=7
E: MINOR=2
E: DEVNAME=/dev/loop2
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/loop3
N: loop3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop3
E: MAJOR=7
E: MINOR=3
E: DEVNAME=/dev/loop3
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/loop4
N: loop4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop4
E: MAJOR=7
E: MINOR=4
E: DEVNAME=/dev/loop4
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/loop5
N: loop5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop5
E: MAJOR=7
E: MINOR=5
E: DEVNAME=/dev/loop5
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/loop6
N: loop6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop6
E: MAJOR=7
E: MINOR=6
E: DEVNAME=/dev/loop6
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/loop7
N: loop7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop7
E: MAJOR=7
E: MINOR=7
E: DEVNAME=/dev/loop7
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: UDISKS_PRESENTATION_NOPOLICY=1

P: /devices/virtual/block/ram0
N: ram0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram0
E: MAJOR=1
E: MINOR=0
E: DEVNAME=/dev/ram0
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram1
N: ram1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram1
E: MAJOR=1
E: MINOR=1
E: DEVNAME=/dev/ram1
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram10
N: ram10
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram10
E: MAJOR=1
E: MINOR=10
E: DEVNAME=/dev/ram10
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram11
N: ram11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram11
E: MAJOR=1
E: MINOR=11
E: DEVNAME=/dev/ram11
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram12
N: ram12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram12
E: MAJOR=1
E: MINOR=12
E: DEVNAME=/dev/ram12
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram13
N: ram13
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram13
E: MAJOR=1
E: MINOR=13
E: DEVNAME=/dev/ram13
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram14
N: ram14
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram14
E: MAJOR=1
E: MINOR=14
E: DEVNAME=/dev/ram14
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram15
N: ram15
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram15
E: MAJOR=1
E: MINOR=15
E: DEVNAME=/dev/ram15
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram2
N: ram2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram2
E: MAJOR=1
E: MINOR=2
E: DEVNAME=/dev/ram2
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram3
N: ram3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram3
E: MAJOR=1
E: MINOR=3
E: DEVNAME=/dev/ram3
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram4
N: ram4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram4
E: MAJOR=1
E: MINOR=4
E: DEVNAME=/dev/ram4
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram5
N: ram5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram5
E: MAJOR=1
E: MINOR=5
E: DEVNAME=/dev/ram5
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram6
N: ram6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram6
E: MAJOR=1
E: MINOR=6
E: DEVNAME=/dev/ram6
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram7
N: ram7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram7
E: MAJOR=1
E: MINOR=7
E: DEVNAME=/dev/ram7
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram8
N: ram8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram8
E: MAJOR=1
E: MINOR=8
E: DEVNAME=/dev/ram8
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/block/ram9
N: ram9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram9
E: MAJOR=1
E: MINOR=9
E: DEVNAME=/dev/ram9
E: DEVTYPE=disk
E: SUBSYSTEM=block

P: /devices/virtual/dmi/id
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/dmi/id
E: MODALIAS=dmi:bvnPhoenixTechnologiesLtd.:bvr05HL:bd05/20/2011:svnSAMSUNGELECTRONICSCO.,LTD.:pn90X3A:pvr0.1:rvnSAMSUNGELECTRONICSCO.,LTD.:rn90X3A:rvrFAB1:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:
E: SUBSYSTEM=dmi

P: /devices/virtual/graphics/fbcon
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/graphics/fbcon
E: SUBSYSTEM=graphics

P: /devices/virtual/hwmon/hwmon0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/hwmon/hwmon0
E: SUBSYSTEM=hwmon

P: /devices/virtual/input/mice
N: input/mice
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/mice
E: MAJOR=13
E: MINOR=63
E: DEVNAME=/dev/input/mice
E: SUBSYSTEM=input

P: /devices/virtual/mem/full
N: full
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/full
E: MAJOR=1
E: MINOR=7
E: DEVNAME=/dev/full
E: DEVMODE=0666
E: SUBSYSTEM=mem

P: /devices/virtual/mem/kmsg
N: kmsg
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/kmsg
E: MAJOR=1
E: MINOR=11
E: DEVNAME=/dev/kmsg
E: SUBSYSTEM=mem

P: /devices/virtual/mem/mem
N: mem
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/mem
E: MAJOR=1
E: MINOR=1
E: DEVNAME=/dev/mem
E: SUBSYSTEM=mem

P: /devices/virtual/mem/null
N: null
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/null
E: MAJOR=1
E: MINOR=3
E: DEVNAME=/dev/null
E: DEVMODE=0666
E: SUBSYSTEM=mem

P: /devices/virtual/mem/oldmem
N: oldmem
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/oldmem
E: MAJOR=1
E: MINOR=12
E: DEVNAME=/dev/oldmem
E: SUBSYSTEM=mem

P: /devices/virtual/mem/port
N: port
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/port
E: MAJOR=1
E: MINOR=4
E: DEVNAME=/dev/port
E: SUBSYSTEM=mem

P: /devices/virtual/mem/random
N: random
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/random
E: MAJOR=1
E: MINOR=8
E: DEVNAME=/dev/random
E: DEVMODE=0666
E: SUBSYSTEM=mem

P: /devices/virtual/mem/urandom
N: urandom
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/urandom
E: MAJOR=1
E: MINOR=9
E: DEVNAME=/dev/urandom
E: DEVMODE=0666
E: SUBSYSTEM=mem

P: /devices/virtual/mem/zero
N: zero
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/zero
E: MAJOR=1
E: MINOR=5
E: DEVNAME=/dev/zero
E: DEVMODE=0666
E: SUBSYSTEM=mem

P: /devices/virtual/misc/agpgart
N: agpgart
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/agpgart
E: MAJOR=10
E: MINOR=175
E: DEVNAME=/dev/agpgart
E: SUBSYSTEM=misc

P: /devices/virtual/misc/cpu_dma_latency
N: cpu_dma_latency
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/cpu_dma_latency
E: MAJOR=10
E: MINOR=59
E: DEVNAME=/dev/cpu_dma_latency
E: SUBSYSTEM=misc

P: /devices/virtual/misc/device-mapper
N: mapper/control
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/device-mapper
E: MAJOR=10
E: MINOR=236
E: DEVNAME=/dev/mapper/control
E: SUBSYSTEM=misc

P: /devices/virtual/misc/ecryptfs
N: ecryptfs
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/ecryptfs
E: MAJOR=10
E: MINOR=61
E: DEVNAME=/dev/ecryptfs
E: SUBSYSTEM=misc

P: /devices/virtual/misc/fuse
N: fuse
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/fuse
E: MAJOR=10
E: MINOR=229
E: DEVNAME=/dev/fuse
E: SUBSYSTEM=misc

P: /devices/virtual/misc/hpet
N: hpet
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/hpet
E: MAJOR=10
E: MINOR=228
E: DEVNAME=/dev/hpet
E: SUBSYSTEM=misc

P: /devices/virtual/misc/kvm
N: kvm
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/kvm
E: MAJOR=10
E: MINOR=232
E: DEVNAME=/dev/kvm
E: SUBSYSTEM=misc
E: TAGS=:udev-acl:

P: /devices/virtual/misc/mcelog
N: mcelog
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/mcelog
E: MAJOR=10
E: MINOR=227
E: DEVNAME=/dev/mcelog
E: SUBSYSTEM=misc

P: /devices/virtual/misc/network_latency
N: network_latency
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/network_latency
E: MAJOR=10
E: MINOR=58
E: DEVNAME=/dev/network_latency
E: SUBSYSTEM=misc

P: /devices/virtual/misc/network_throughput
N: network_throughput
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/network_throughput
E: MAJOR=10
E: MINOR=57
E: DEVNAME=/dev/network_throughput
E: SUBSYSTEM=misc

P: /devices/virtual/misc/pktcdvd
N: pktcdvd/control
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/pktcdvd
E: MAJOR=10
E: MINOR=60
E: DEVNAME=/dev/pktcdvd/control
E: SUBSYSTEM=misc

P: /devices/virtual/misc/psaux
N: psaux
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/psaux
E: MAJOR=10
E: MINOR=1
E: DEVNAME=/dev/psaux
E: SUBSYSTEM=misc

P: /devices/virtual/misc/rfkill
N: rfkill
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/rfkill
E: MAJOR=10
E: MINOR=62
E: DEVNAME=/dev/rfkill
E: SUBSYSTEM=misc
E: TAGS=:udev-acl:

P: /devices/virtual/misc/snapshot
N: snapshot
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/snapshot
E: MAJOR=10
E: MINOR=231
E: DEVNAME=/dev/snapshot
E: SUBSYSTEM=misc

P: /devices/virtual/misc/tun
N: net/tun
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/tun
E: MAJOR=10
E: MINOR=200
E: DEVNAME=/dev/net/tun
E: SUBSYSTEM=misc

P: /devices/virtual/misc/uinput
N: uinput
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/uinput
E: MAJOR=10
E: MINOR=223
E: DEVNAME=/dev/uinput
E: SUBSYSTEM=misc

P: /devices/virtual/misc/vboxdrv
N: vboxdrv
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/vboxdrv
E: MAJOR=10
E: MINOR=56
E: DEVNAME=/dev/vboxdrv
E: SUBSYSTEM=misc

P: /devices/virtual/misc/vboxnetctl
N: vboxnetctl
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/vboxnetctl
E: MAJOR=10
E: MINOR=55
E: DEVNAME=/dev/vboxnetctl
E: SUBSYSTEM=misc

P: /devices/virtual/misc/vga_arbiter
N: vga_arbiter
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/vga_arbiter
E: MAJOR=10
E: MINOR=63
E: DEVNAME=/dev/vga_arbiter
E: SUBSYSTEM=misc

P: /devices/virtual/net/lo
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/net/lo
E: INTERFACE=lo
E: IFINDEX=1
E: SUBSYSTEM=net
E: ID_MM_CANDIDATE=1

P: /devices/virtual/net/vboxnet0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/net/vboxnet0
E: INTERFACE=vboxnet0
E: IFINDEX=4
E: SUBSYSTEM=net
E: ID_MM_CANDIDATE=1

P: /devices/virtual/ppp/ppp
N: ppp
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/ppp/ppp
E: MAJOR=108
E: MINOR=0
E: DEVNAME=/dev/ppp
E: SUBSYSTEM=ppp

P: /devices/virtual/regulator/regulator.0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/regulator/regulator.0
E: SUBSYSTEM=regulator

P: /devices/virtual/sound/seq
N: snd/seq
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/sound/seq
E: MAJOR=116
E: MINOR=1
E: DEVNAME=/dev/snd/seq
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/virtual/sound/timer
N: snd/timer
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/sound/timer
E: MAJOR=116
E: MINOR=33
E: DEVNAME=/dev/snd/timer
E: SUBSYSTEM=sound
E: TAGS=:udev-acl:

P: /devices/virtual/thermal/cooling_device0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device0
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device1
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device2
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device3
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device4
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device5
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device6
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device7
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device8
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device9
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/thermal_zone0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/thermal_zone0
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/thermal_zone1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/thermal_zone1
E: SUBSYSTEM=thermal

P: /devices/virtual/tty/console
N: console
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/console
E: MAJOR=5
E: MINOR=1
E: DEVNAME=/dev/console
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/ptmx
N: ptmx
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/ptmx
E: MAJOR=5
E: MINOR=2
E: DEVNAME=/dev/ptmx
E: DEVMODE=0666
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty
N: tty
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty
E: MAJOR=5
E: MINOR=0
E: DEVNAME=/dev/tty
E: DEVMODE=0666
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty0
N: tty0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty0
E: MAJOR=4
E: MINOR=0
E: DEVNAME=/dev/tty0
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty1
N: tty1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty1
E: MAJOR=4
E: MINOR=1
E: DEVNAME=/dev/tty1
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty10
N: tty10
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty10
E: MAJOR=4
E: MINOR=10
E: DEVNAME=/dev/tty10
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty11
N: tty11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty11
E: MAJOR=4
E: MINOR=11
E: DEVNAME=/dev/tty11
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty12
N: tty12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty12
E: MAJOR=4
E: MINOR=12
E: DEVNAME=/dev/tty12
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty13
N: tty13
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty13
E: MAJOR=4
E: MINOR=13
E: DEVNAME=/dev/tty13
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty14
N: tty14
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty14
E: MAJOR=4
E: MINOR=14
E: DEVNAME=/dev/tty14
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty15
N: tty15
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty15
E: MAJOR=4
E: MINOR=15
E: DEVNAME=/dev/tty15
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty16
N: tty16
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty16
E: MAJOR=4
E: MINOR=16
E: DEVNAME=/dev/tty16
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty17
N: tty17
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty17
E: MAJOR=4
E: MINOR=17
E: DEVNAME=/dev/tty17
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty18
N: tty18
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty18
E: MAJOR=4
E: MINOR=18
E: DEVNAME=/dev/tty18
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty19
N: tty19
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty19
E: MAJOR=4
E: MINOR=19
E: DEVNAME=/dev/tty19
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty2
N: tty2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty2
E: MAJOR=4
E: MINOR=2
E: DEVNAME=/dev/tty2
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty20
N: tty20
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty20
E: MAJOR=4
E: MINOR=20
E: DEVNAME=/dev/tty20
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty21
N: tty21
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty21
E: MAJOR=4
E: MINOR=21
E: DEVNAME=/dev/tty21
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty22
N: tty22
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty22
E: MAJOR=4
E: MINOR=22
E: DEVNAME=/dev/tty22
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty23
N: tty23
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty23
E: MAJOR=4
E: MINOR=23
E: DEVNAME=/dev/tty23
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty24
N: tty24
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty24
E: MAJOR=4
E: MINOR=24
E: DEVNAME=/dev/tty24
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty25
N: tty25
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty25
E: MAJOR=4
E: MINOR=25
E: DEVNAME=/dev/tty25
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty26
N: tty26
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty26
E: MAJOR=4
E: MINOR=26
E: DEVNAME=/dev/tty26
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty27
N: tty27
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty27
E: MAJOR=4
E: MINOR=27
E: DEVNAME=/dev/tty27
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty28
N: tty28
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty28
E: MAJOR=4
E: MINOR=28
E: DEVNAME=/dev/tty28
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty29
N: tty29
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty29
E: MAJOR=4
E: MINOR=29
E: DEVNAME=/dev/tty29
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty3
N: tty3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty3
E: MAJOR=4
E: MINOR=3
E: DEVNAME=/dev/tty3
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty30
N: tty30
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty30
E: MAJOR=4
E: MINOR=30
E: DEVNAME=/dev/tty30
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty31
N: tty31
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty31
E: MAJOR=4
E: MINOR=31
E: DEVNAME=/dev/tty31
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty32
N: tty32
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty32
E: MAJOR=4
E: MINOR=32
E: DEVNAME=/dev/tty32
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty33
N: tty33
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty33
E: MAJOR=4
E: MINOR=33
E: DEVNAME=/dev/tty33
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty34
N: tty34
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty34
E: MAJOR=4
E: MINOR=34
E: DEVNAME=/dev/tty34
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty35
N: tty35
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty35
E: MAJOR=4
E: MINOR=35
E: DEVNAME=/dev/tty35
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty36
N: tty36
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty36
E: MAJOR=4
E: MINOR=36
E: DEVNAME=/dev/tty36
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty37
N: tty37
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty37
E: MAJOR=4
E: MINOR=37
E: DEVNAME=/dev/tty37
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty38
N: tty38
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty38
E: MAJOR=4
E: MINOR=38
E: DEVNAME=/dev/tty38
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty39
N: tty39
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty39
E: MAJOR=4
E: MINOR=39
E: DEVNAME=/dev/tty39
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty4
N: tty4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty4
E: MAJOR=4
E: MINOR=4
E: DEVNAME=/dev/tty4
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty40
N: tty40
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty40
E: MAJOR=4
E: MINOR=40
E: DEVNAME=/dev/tty40
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty41
N: tty41
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty41
E: MAJOR=4
E: MINOR=41
E: DEVNAME=/dev/tty41
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty42
N: tty42
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty42
E: MAJOR=4
E: MINOR=42
E: DEVNAME=/dev/tty42
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty43
N: tty43
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty43
E: MAJOR=4
E: MINOR=43
E: DEVNAME=/dev/tty43
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty44
N: tty44
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty44
E: MAJOR=4
E: MINOR=44
E: DEVNAME=/dev/tty44
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty45
N: tty45
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty45
E: MAJOR=4
E: MINOR=45
E: DEVNAME=/dev/tty45
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty46
N: tty46
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty46
E: MAJOR=4
E: MINOR=46
E: DEVNAME=/dev/tty46
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty47
N: tty47
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty47
E: MAJOR=4
E: MINOR=47
E: DEVNAME=/dev/tty47
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty48
N: tty48
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty48
E: MAJOR=4
E: MINOR=48
E: DEVNAME=/dev/tty48
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty49
N: tty49
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty49
E: MAJOR=4
E: MINOR=49
E: DEVNAME=/dev/tty49
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty5
N: tty5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty5
E: MAJOR=4
E: MINOR=5
E: DEVNAME=/dev/tty5
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty50
N: tty50
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty50
E: MAJOR=4
E: MINOR=50
E: DEVNAME=/dev/tty50
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty51
N: tty51
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty51
E: MAJOR=4
E: MINOR=51
E: DEVNAME=/dev/tty51
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty52
N: tty52
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty52
E: MAJOR=4
E: MINOR=52
E: DEVNAME=/dev/tty52
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty53
N: tty53
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty53
E: MAJOR=4
E: MINOR=53
E: DEVNAME=/dev/tty53
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty54
N: tty54
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty54
E: MAJOR=4
E: MINOR=54
E: DEVNAME=/dev/tty54
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty55
N: tty55
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty55
E: MAJOR=4
E: MINOR=55
E: DEVNAME=/dev/tty55
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty56
N: tty56
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty56
E: MAJOR=4
E: MINOR=56
E: DEVNAME=/dev/tty56
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty57
N: tty57
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty57
E: MAJOR=4
E: MINOR=57
E: DEVNAME=/dev/tty57
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty58
N: tty58
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty58
E: MAJOR=4
E: MINOR=58
E: DEVNAME=/dev/tty58
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty59
N: tty59
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty59
E: MAJOR=4
E: MINOR=59
E: DEVNAME=/dev/tty59
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty6
N: tty6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty6
E: MAJOR=4
E: MINOR=6
E: DEVNAME=/dev/tty6
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty60
N: tty60
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty60
E: MAJOR=4
E: MINOR=60
E: DEVNAME=/dev/tty60
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty61
N: tty61
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty61
E: MAJOR=4
E: MINOR=61
E: DEVNAME=/dev/tty61
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty62
N: tty62
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty62
E: MAJOR=4
E: MINOR=62
E: DEVNAME=/dev/tty62
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty63
N: tty63
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty63
E: MAJOR=4
E: MINOR=63
E: DEVNAME=/dev/tty63
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty7
N: tty7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty7
E: MAJOR=4
E: MINOR=7
E: DEVNAME=/dev/tty7
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty8
N: tty8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty8
E: MAJOR=4
E: MINOR=8
E: DEVNAME=/dev/tty8
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/tty9
N: tty9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty9
E: MAJOR=4
E: MINOR=9
E: DEVNAME=/dev/tty9
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/tty/ttyprintk
N: ttyprintk
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/ttyprintk
E: MAJOR=5
E: MINOR=3
E: DEVNAME=/dev/ttyprintk
E: SUBSYSTEM=tty
E: ID_MM_CANDIDATE=1

P: /devices/virtual/usbmon/usbmon0
N: usbmon0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/usbmon/usbmon0
E: MAJOR=252
E: MINOR=0
E: DEVNAME=/dev/usbmon0
E: SUBSYSTEM=usbmon

P: /devices/virtual/vc/vcs
N: vcs
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs
E: MAJOR=7
E: MINOR=0
E: DEVNAME=/dev/vcs
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs1
N: vcs1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs1
E: MAJOR=7
E: MINOR=1
E: DEVNAME=/dev/vcs1
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs2
N: vcs2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs2
E: MAJOR=7
E: MINOR=2
E: DEVNAME=/dev/vcs2
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs3
N: vcs3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs3
E: MAJOR=7
E: MINOR=3
E: DEVNAME=/dev/vcs3
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs4
N: vcs4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs4
E: MAJOR=7
E: MINOR=4
E: DEVNAME=/dev/vcs4
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs5
N: vcs5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs5
E: MAJOR=7
E: MINOR=5
E: DEVNAME=/dev/vcs5
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs6
N: vcs6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs6
E: MAJOR=7
E: MINOR=6
E: DEVNAME=/dev/vcs6
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs63
N: vcs63
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs63
E: MAJOR=7
E: MINOR=63
E: DEVNAME=/dev/vcs63
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcs8
N: vcs8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs8
E: MAJOR=7
E: MINOR=8
E: DEVNAME=/dev/vcs8
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa
N: vcsa
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa
E: MAJOR=7
E: MINOR=128
E: DEVNAME=/dev/vcsa
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa1
N: vcsa1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa1
E: MAJOR=7
E: MINOR=129
E: DEVNAME=/dev/vcsa1
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa2
N: vcsa2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa2
E: MAJOR=7
E: MINOR=130
E: DEVNAME=/dev/vcsa2
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa3
N: vcsa3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa3
E: MAJOR=7
E: MINOR=131
E: DEVNAME=/dev/vcsa3
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa4
N: vcsa4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa4
E: MAJOR=7
E: MINOR=132
E: DEVNAME=/dev/vcsa4
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa5
N: vcsa5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa5
E: MAJOR=7
E: MINOR=133
E: DEVNAME=/dev/vcsa5
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa6
N: vcsa6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa6
E: MAJOR=7
E: MINOR=134
E: DEVNAME=/dev/vcsa6
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa63
N: vcsa63
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa63
E: MAJOR=7
E: MINOR=191
E: DEVNAME=/dev/vcsa63
E: SUBSYSTEM=vc

P: /devices/virtual/vc/vcsa8
N: vcsa8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa8
E: MAJOR=7
E: MINOR=136
E: DEVNAME=/dev/vcsa8
E: SUBSYSTEM=vc

P: /devices/virtual/vtconsole/vtcon0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vtconsole/vtcon0
E: SUBSYSTEM=vtconsole

P: /devices/virtual/vtconsole/vtcon1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vtconsole/vtcon1
E: SUBSYSTEM=vtconsole

P: /devices/virtual/wmi/C5819D7C-7C31-4CBF-B831-0BA025B81D22
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/wmi/C5819D7C-7C31-4CBF-B831-0BA025B81D22
E: MODALIAS=wmi:C5819D7C-7C31-4CBF-B831-0BA025B81D22
E: SUBSYSTEM=wmi
```

---

### Post by coleman_ian on 2011-10-17
Some info about this at hotplug

[http://www.spinics.net/lists/hotplug/msg05148.html]("http://www.spinics.net/lists/hotplug/msg05148.html")

I will look into this some more later.

---

### Post by vaijab on 2012-02-11
I wrote a couple of blog posts about this issue, see links below:
[http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/](http://jablonskis.org/2012/linux-and-samsung-series-laptop-9-fn-keys/)
[http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/](http://jablonskis.org/2011/fedora-16-linux-on-samsung-series-9-np900x3a/)

Hope you find your answers. 

Thanks,
zooz

---

