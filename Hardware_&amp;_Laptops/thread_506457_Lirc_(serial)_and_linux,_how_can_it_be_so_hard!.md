---
title: "Lirc (serial) and linux, how can it be so hard!"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by Elv13 on 2007-07-21
Hi, i made a serial (lirc) IR reciver. When i tryed to use it under linux, it did not work at all. I tryed it on one of my old laptop that still have windows on it, it worked perfectly with winirc (lirc for windows). I was under gentoo, after few week of hard time, i started to see something when i was doing cat /dev/lirc, it was seeing the remote and writing things when i pressed button. But irrecord was not able to corectly configure it...

Now i am using Ubuntu. No more luck, i get all problem one after the other. After few hack, i am able to modprobe lirc_serial, but it end there


dmesg:
[17179714.200000] lirc_dev: IR Remote Control driver registered, at major 61
[17179714.216000] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179714.216000] lirc_serial: port 03f8 already in use
[17179714.216000] lirc_serial: use 'setserial /dev/ttySX uart none'
[17179714.216000] lirc_serial: or compile the serial port driver as module and
[17179714.216000] lirc_serial: make sure this module is loaded first
[17179998.044000] lirc_serial: auto-detected active low receiver
[17179998.044000] lirc_dev: lirc_register_plugin: sample_rate: 0

i did setserial /dev/ttyS1 uart none and setserial /dev/ttyS0 uart none it is how i got the module to load

I tryed to use the cvs version, the ubuntu version, the debian version, i compiled module automatikly, manually, with debian utils, with a new kernel, with de default kernel and some other combinaison and it always do the same **** things.

When i try irrecord i get

Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.

irrecord: could not find gap.
irrecord: gap not found, can't continue

irw do nothing but start (i had to do a symlink (ln -s /dev/lirc0 /dev/lirc) to prevent it from stoping immediatelly)


I really dont know what to do now, please, help me!

---

