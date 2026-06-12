---
title: "&quot;P&quot; button on Acer 5553G"
date: 2011-03-29
forum: Hardware
---

### Post by sha3102 on 2011-03-29
On my Acer 5553G laptop running Maveric with all available updates I want to change the default shortcut on programmable button with led in order to run start and stop script for some task (and switch on and off the led respectively). The problem is that this key is an ACPI device and it configures differently during boot up depending on the status of IGPU (on/off). I tried to collect some information which possibly can be useful for troubleshooting:
a) both IGPU and DGPU are turned on in bios, the led turns on during boot up and stays on permanently, "P" button is pressed three times:
```
$ acpi_listen
video VGA2 00000081 00000000
video VGA2 00000081 00000000
video VGA2 00000081 00000000

$ sudo showkey -s
kb mode was RAW
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
0x9c 
0xe0 0x56 0xe0 0xd6 
0xe0 0x56 0xe0 0xd6 
0xe0 0x56 0xe0 0xd6 
```The key is mapped to XF86Display

b) After turning the IGPU off, "P" button is pressed three times:
```
$ acpi_listen
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000086 00000000
video LCD 00000086 00000000
video LCD 00000086 00000000
video LCD 00000086 00000000
video LCD 00000086 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000
video LCD 00000087 00000000

$ sudo showkey -s
kb mode was RAW
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
0x9c 
0xe0 0x54 0xe0 0xd4 0xe0 0x54 0xe0 0xd4 0xe0 0x54 0xe0 0xd4 0xe0 0x54 0xe0 0xd4 0xe0 0x54 
0xe0 0xd4 
0xe0 0x4c 0xe0 0xcc 0xe0 0x4c 0xe0 0xcc 0xe0 0x4c 0xe0 0xcc 0xe0 0x4c 0xe0 0xcc 0xe0 0x4c 
0xe0 0xcc 0xe0 0x4c 0xe0 0xcc 
0xe0 0x54 0xe0 0xd4 0xe0 0x54 0xe0 0xd4 0xe0 0x54 0xe0 0xd4 0xe0 0x54 0xe0 0xd4 0xe0 0x54 
0xe0 0xd4 0xe0 0x54 0xe0 0xd4
```The key mapping toggles between XF86MonBrightnessUp and XF86MonBrightnessDown, the led on the button switches on/off during keypresses.

How should I interpret these results? The last two outputs have something incommon with situation, described in [Bug #327707]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/327707") (multiple events on one keypress). Is it a bug? 
Is it possible to influence somehow on the behaviour of this key to force it entering the mode when two scancodes preset by me are returned in a cycle (like in (b))? All troubleshooting guides, which I've read, stated, that the returned scancodes were hardware-specific and started from instructions to discover their actual values for correct mapping to keycodes.

---

