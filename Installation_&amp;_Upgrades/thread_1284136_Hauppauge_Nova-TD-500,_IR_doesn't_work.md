---
title: "Hauppauge Nova-TD-500, IR doesn't work"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by my5082 on 2009-10-06
when I check dmesg, it looks ok, but Remote Controler doesn't work.

root@matt-desktop:/etc/lirc# dmesg | grep -i dvb
[    9.350604] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[    9.350607] usb 3-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[    9.452306] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   10.172022] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   10.172115] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.172373] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   10.400721] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   10.619275] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.619480] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   10.768057] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   10.983352] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:05:01.2/usb3/3-1/input/input6
[   10.984742] dvb-usb: schedule remote query interval to 50 msecs.
[   10.984745] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   10.984876] usbcore: registered new interface driver dvb_usb_dib0700

also, when I test with "irw" command, nothing appears.

What can I try more to get it work?

---

