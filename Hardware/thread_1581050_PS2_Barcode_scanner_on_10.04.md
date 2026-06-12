---
title: "PS2 Barcode scanner on 10.04"
date: 2010-09-24
forum: Hardware
---

### Post by lessless on 2010-09-24
Hi! I'm in trouble with LABAU LP  150 laser scanner for barcode. It is connected to ps/2 keyboard port, and has also a "mother" connector on which keyboard is plugged in.
So, as i  undesrtand it must send just ascii codes to the any input window, just like keyboard do.
I can register event with xev 

MappingNotify event, serial 30, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 34, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 35, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 36, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

but, in generall, no any markable input is produced.

so, something is happening, but i need to make it work in they way it is supposed to be - to   read barcodes and produce the data for barcode reading program, and it doesn't do that.
help me please.

---

### Post by lessless on 2010-09-24
updt. also everytime i scan something new line in /var/log/messages appear


input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input6

---

