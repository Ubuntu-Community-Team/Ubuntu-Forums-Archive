---
title: "Hauppauge Nova-T Stick USB2 DVB-T"
date: 2008-09-04
forum: Hardware
---

### Post by gattopi on 2008-09-04
Hi,
I have a USB PEN 
DVB  NOVA-T-Stick but not working.

I try three PC and many Linux Distribution, many Kernel, many Firmware but not work
The error is non find the Frontend


[url=http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick]http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick
[/url]
E tante altre in giro
```

lsusb 
Bus 007 Device 003: ID 2040:7070 Hauppauge
```
```
dmesg |grep dv
[   27.862655] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[  803.027868] dvb-usb: found a ':popcorn:' in cold state, will try to load a firmware
[  803.039729] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[  803.291649] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[  803.291686] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  803.292203] DVB: register adapter0/dvr0 @ minor: 5 (0x05)
[  803.309825] **dvb-usb: no frontend was attached by 'Hauppauge Nova-T Stick'**
[  803.326246] dvb-usb: schedule remote query interval to 150 msecs.
[  803.326252] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[  803.326353] usbcore: registered new interface driver dvb_usb_dib0700
```

```

 ls /dev/dvb/adapter0
demux0  dvr0  net0
```

Help me Please

---

### Post by bebraw on 2008-09-05
I have the same problem. I am currently using Hardy Heron (32 bit, kernel 2.6.24.-21-generic) and the same DVB-T stick.

Apparently we have the device with the same chip.
```

Bus 004 Device 002: ID 2040:7070 Hauppauge 

```

```

dmesg |grep dv
[   39.231781] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   40.993150] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   41.706102] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   41.706160] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   42.129738] dvb-usb: schedule remote query interval to 150 msecs.
[   42.129743] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   42.129936] usbcore: registered new interface driver dvb_usb_dib0700

```
As you can see dmesg gives different message in my case. Unfortunately I have no idea why you are missing frontend.

```

ls /dev/dvb/adapter0
demux0  dvr0  frontend0  net0

```
The last piece contains frontend which you don't seem to have due to error at dmesg.

I am using the newest version of v4l (updated yesterday) with 1.10 firmware. I copied the firmware to /lib/firmware/2.6.24-21-generic . I tried with a newer (1.20) and older firmware by replacing the old file (I changed the name of firmware to match old) but this did not help.

When tuning (scan command), it gives a bunch of errors:
```

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Jyvaskyla 
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Jyvaskyla
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 546000000 0 2 9 3 1 2 0
initial transponder 786000000 0 2 9 3 1 2 0
initial transponder 746000000 0 2 9 3 1 2 0
>>> tune to: 546000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 786000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 746000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.

```.

I just found this tip [http://ubuntuforums.org/showpost.php?p=5241978&postcount=8](http://ubuntuforums.org/showpost.php?p=5241978&postcount=8) . I will try that one out to see if it makes any difference. If that doesn't work, I will try it out with different antenna. It might be that the one provided with the device is not good enough.

Apparently someone got it working on older version of kernel. See the first message at [http://www.play.com/PC/PCs/-/667/874/-/3326726/Hauppauge-WinTV-Nova-T-Stick-USB-DVB-T-Model-294/Product.html?searchtype=genre](http://www.play.com/PC/PCs/-/667/874/-/3326726/Hauppauge-WinTV-Nova-T-Stick-USB-DVB-T-Model-294/Product.html?searchtype=genre) .

<edit>
I forgot to mention that I have added "options dvb_usb_dib0700 force_lna_activation=1" to my /etc/modprobe.d/options .
</edit>

---

### Post by bebraw on 2008-09-05
In my case the problem was the antenna. I tried it with better antenna and it just worked. Here are the steps I took to make it work:
[LIST=1]
[*]Install v4l. See case 2 at [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers) .
[*]Make sure you have copied the device firmware to /lib/firmware . Below that you should see different kernel versions. Put the file there. You can find links to recent firmwares at [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick) . Currently I use 1.10. On one mailing list it was mentioned that it would be nice to use symbolic link to current firmware version at /lib/firmware . This would save you from unnecessary copying and renaming but do as you wish.
[*]Remember to enable LNA ([http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29)).
[*]Check if scan (ie. "scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/LOCATION HERE") returns nice results. If it does not, it may be that your antenna isn't good enough.
[*]If scan works okay, you should try Kaffeine ([http://kaffeine.kde.org/](http://kaffeine.kde.org/)), Me TV ([https://launchpad.net/me-tv](https://launchpad.net/me-tv)) or perhaps even MythTV ([http://www.mythtv.org/](http://www.mythtv.org/)) .
[/LIST]

---

### Post by Euskuntu on 2008-12-06
Hi,

I have the same problem as gattopi, the usb stick is not detected by mythTV and I found out that dmesg also says there is no frontend attached to the stick. My stick model is a 1157 SL-1157-V2.2-SP according to the box.

These are the outputs I get in terminal:

> lsusb
Bus 005 Device 004: ID 2040:7070 Hauppauge

and

> [  209.416876] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[  209.448549] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[  210.157844] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[  210.157921] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  212.199722] dvb-usb: **no frontend was attached by 'Hauppauge Nova-T Stick'**
[  212.254063] dvb-usb: schedule remote query interval to 150 msecs.
[  212.254071] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.

I followed the instructions in [HTML]http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick[/HTML], the ones on [HTML]http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers[/HTML] and also the ones proposed by bebraw, having the same results in all cases.

I chose this stick because I saw in some webs that it was suitable with ubuntu, but by now I haven't been able to make it work. Please someone help me resolve this problem [-o< , I also want to watch TV on ubuntu.

gattopi: I see your first and last post was on September 4th. Have you solved the problem? How?

---

### Post by susundberg on 2009-01-21
I got mine working (also the ir-remote) on Ubuntu 8.10 by
installing:
 - kaffeine (the best player i found)
 - inputlirc

And then updating my drivers from [http://linuxtv.org/hg/v4l-dvb]("http://linuxtv.org/hg/v4l-dvb")
EDIT NOTE: I did not update my firmware. I am still using 1.10 firmware. So i made symbolic link from 1.20->1.10.


Some buttons do not work on remote (like channel+), but most important work (channelX + volume). Even the powerbutton works: pressing it will shutdown the computer in 60s. Yey.

---

### Post by devialupus on 2009-09-30
Hi I am new to linux, and just gaining my feet.
I have an EEE PC 900 with Ubuntu 9.04 loaded, I have just about got my head around updating and adding. However I cannot get my WinTV Nova-T stick to work, I have captured the firmware and updated my v4l. When I plug the stick in this is what I get in the log

usb 1-2: USB disconnect, address 2
usb 1-2: new full speed USB device using uhci_hcd and address 3
usb 1-2: configuration #1 chosen from 1 choice
dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
usb 1-2: firmware: requesting dvb-usb-dib0700-1.20.fw
dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
dib0700: firmware started successfully.
dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
dvb-usb: Hauppauge Nova-T Stick error while loading driver (-19)

So i am confused as to where to go to next?

---

### Post by tsh on 2009-10-02
My Nova-T stick has just stopped working (after a reboot - power cut this am!)

```

dmesg | grep dvb
[   17.589112] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   17.589200] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   17.787891] dvb-usb: no frontend was attached by 'Hauppauge Nova-T Stick'
[   17.840281] dvb-usb: schedule remote query interval to 150 msecs.
[   17.840288] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   17.841248] usbcore: registered new interface driver dvb_usb_dib0700
```

Now I have had problems in the past with the wrong firmware being installed.

This is the good one (for me)
```
 md5sum /lib/firmware/2.6.24-21-generic/dvb-usb-dib0700-1.10.fw
0b39b8cceb1ccdb86d6fc932149aff25  /lib/firmware/2.6.24-21-generic/dvb-usb-dib0700-1.10.fw
```

This one seems to be bad
```
md5sum /lib/firmware/dvb-usb-dib0700-1.10.fw
5878ebfcba2d8deb90b9120eb89b02da  /lib/firmware/dvb-usb-dib0700-1.10.fw
```

I can't confirm that this is the problem since it needs a cold boot - and I can't do that remotely.

---

