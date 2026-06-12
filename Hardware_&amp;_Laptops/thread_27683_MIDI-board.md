---
title: "MIDI-board"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by ProbablyX on 2005-04-17
hello!

I have an M-Audio Radium 49 Midi-board, does anyone know how to get this working under Ubuntu AMD64? [update] I got the drivers installed now :) [/update]

I have installed Rosegarden, but it says that its unable to initialize the sequencer

Thanks

---

### Post by smurky on 2005-05-13
Have you modprobed snd-seq? When you say you've got the drivers installed I take it you mean that you've built the firmware, and modprobed snd-usb-audio, and hopefully also edited /etc/modprobe.d/alsa-base and /etc/asound? I'm using the Radium 61 on a P4, working beautifully. If you find that modprobe snd-seq gets Rosegarden started then add it to /etc/modules so that it will load at boot time. What does lsmod | grep snd show?

---

### Post by bobbyshane on 2006-03-30
i'm still learning here... how do you modprobe snd-seq? i'm not new to linux but i'm very new to using midi devices with linux... i have a radium 49. I got the firmware and the firmware loader and this is what happened: 

with 1.2:

root@ubuntu:/home/bobbyshane/radiumdriver/midisport-firmware-1.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking for fxload... /sbin/fxload
checking for udev version... 060
checking for /etc/udev/udev.conf... yes
checking for udev rules directory... /etc/udev/rules.d
configure: creating ./config.status
config.status: creating Makefile
root@ubuntu:/home/bobbyshane/radiumdriver/midisport-firmware-1.2# make
bash: make: command not found


and with 0.5:

root@ubuntu:/home/bobbyshane/radiumdriver/midisport_firmware-0.5# make install
bash: make: command not found

any help would be greatly appreciated... I want to use this thing with qsynth so i can use my soundfonts!

---

