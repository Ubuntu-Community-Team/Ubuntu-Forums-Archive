---
title: "Hauppauge WinTV-T HD not working"
date: 2014-05-05
forum: Hardware
---

### Post by djahma on 2014-05-05
I just bought [this]("http://www.hauppauge.fr/site/products/data_ministickhd.html") TV tuner: **Hauppauge WinTV-T HD** Black edition, model: **1419**
But there's no driver and it's not working (I'm using Kubuntu 14.04).

it is recognised though: ```
gman@ThinkPad:~$ lsusb
[...]
Bus 002 Device 002: ID 2040:f900 Hauppauge 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gman@ThinkPad:~$ dmesg | grep dvb
[    8.219175] usb 2-1: dvb_usb_af9035: prechip_version=83 chip_version=02 chip_type=9135
[    8.219583] usb 2-1: dvb_usb_v2: found a 'Hauppauge WinTV-MiniStick 2' in cold state
[    8.220387] usb 2-1: dvb_usb_v2: Did not find the firmware file 'dvb-usb-it9135-02.fw'. Please see linux/Documentation/dvb/ for more details on firmware-problems. Status -2
[    8.220396] dvb_usb_af9035: probe of 2-1:1.0 failed with error -2
[    8.220417] usbcore: registered new interface driver dvb_usb_af9035

```

So this product(**2040:f900**) should be handled by **dvb_usb_af9035** driver? But it is missing a firmware? ok, then google lead me to [a guy who added this hardware in a list of supported tuners ]("http://osdir.com/ml/linux-kernel/2014-02/msg00701.html")and tracking his name and **'dvb-usb-it9135-02.fw' **firmware, I downloaded [his files there]("http://blog.palosaari.fi/2014/02/linux-it9135-driver-firmwares.html") (bottom of his post).

I tried both v2 drivers/firmwares and got the tuner "working":
```
gman@ThinkPad:~$ sudo mv ./Downloads/dvb-usb-it9135-02.fw /lib/firmware/
[sudo] password for gman: 
gman@ThinkPad:~$ dmesg | grep dvb
[    8.219175] usb 2-1: dvb_usb_af9035: prechip_version=83 chip_version=02 chip_type=9135
[    8.219583] usb 2-1: dvb_usb_v2: found a 'Hauppauge WinTV-MiniStick 2' in cold state
[    8.220387] usb 2-1: dvb_usb_v2: Did not find the firmware file 'dvb-usb-it9135-02.fw'. Please see linux/Documentation/dvb/ for more details on firmware-problems. Status -2
[    8.220396] dvb_usb_af9035: probe of 2-1:1.0 failed with error -2
[    8.220417] usbcore: registered new interface driver dvb_usb_af9035
[ 1549.105002] usb 2-1: dvb_usb_af9035: prechip_version=83 chip_version=02 chip_type=9135
[ 1549.105365] usb 2-1: dvb_usb_v2: found a 'Hauppauge WinTV-MiniStick 2' in cold state
[ 1549.105427] usb 2-1: dvb_usb_v2: downloading firmware from file 'dvb-usb-it9135-02.fw'
[ 1549.206069] usb 2-1: dvb_usb_af9035: firmware version=3.42.3.3
[ 1549.206087] usb 2-1: dvb_usb_v2: found a 'Hauppauge WinTV-MiniStick 2' in warm state
[ 1549.208695] usb 2-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[ 1549.239120] usb 2-1: dvb_usb_v2: schedule remote query interval to 500 msecs
[ 1549.239129] usb 2-1: dvb_usb_v2: 'Hauppauge WinTV-MiniStick 2' successfully initialized and connected
```

Unfortunately, the tuner is not recognised in **kmplayer** and **vlc** and although I can scan channels with **kaffeine**, it's not finding any. Also, **kaffeine** recognises the tuner as a "Afatech AF9033 (DVB-T)" device.

At this point I am helpless, stuck with a tuner misidentified for another brand and model (I wouldn't care if it was working), and I can only "scan" channels with **kaffeine** but can't find a single channel...

Any idea anyone?

---

### Post by antoine-pecheur on 2015-03-12
Hi,
Hope it's not too late ;).
Sorry for the very late response. I feedback my experience with the TNT Tuner Hauppauge WinTV Ministick on XUbuntu.
I read that you've already copied the firmware to /lib/firmware/* , If you Actually did it, you're almost done with your device, you should reboot and retry the command
```
dmesg | grep dvb
```
And you may be good to go !
CU

---

### Post by djahma on 2015-03-23
Hey cheers for a late reply! that's better than no reply ;-)
So I have since moved to mint 17.1 XFCE, which should be similar to Xubuntu. I pulled the tv card out of the cupboard for a fresh try. This is what 'dmesg |grep dvb' gives me:
> gman@thinkpad:~$ dmesg |grep dvb
[    8.394534] usb 1-2: dvb_usb_af9035: prechip_version=83 chip_version=02 chip_type=9135
[    8.394906] usb 1-2: dvb_usb_v2: found a 'Hauppauge WinTV-MiniStick 2' in warm state
[    8.397573] usb 1-2: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    8.486414] usb 1-2: dvb_usb_v2: schedule remote query interval to 500 msecs
[    8.486418] usb 1-2: dvb_usb_v2: 'Hauppauge WinTV-MiniStick 2' successfully initialized and connected
[    8.486569] usbcore: registered new interface driver dvb_usb_af9035

I am running 'w_scan -ft -c FR' as i write. I'll see if a mere reboot was all it needed to work...:-\"

EDIT: scan not working, the result of the command was > ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
Any idea how to scan/discover available channels?

---

