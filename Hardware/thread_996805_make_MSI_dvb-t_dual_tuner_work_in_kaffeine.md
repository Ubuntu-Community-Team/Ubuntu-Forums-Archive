---
title: "make MSI dvb-t dual tuner work in kaffeine"
date: 2008-11-29
forum: Hardware
---

### Post by desmane on 2008-11-29
Hello people, 

I am trying to get the: 

MSI (Micro-Star Internation) DigiVox Duo (Dual View) to work. 

I'd like to tune into two different channels at the same time. 

The channel search in kaffeine works great, the signal strength is high (50 - 75%)

watching and recording works, but once I start recording, the channel list shows only the 4 channels of the recording frequency. 

How can I use the other tuner at the same time?


########################################################################

Some infos: 

```

Kubuntu 8.10 Kde 4.1
Linux andibuntu 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux

Asus Board, Ati Radeon 9600, no Composite enabled, no fglrx!

v4l, mercurial installed!
Firmware copied into /lib/firmware!

(this one: http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/)


```

```
andi@andibuntu:~$ dmesg | grep dvb
[   16.054623] dvb-usb: found a 'MSI DIGIVOX Duo' in warm state.
[   16.054737] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.623458] dvb-usb: MSI DIGIVOX Duo successfully initialized and connected.
[   16.631724] usbcore: registered new interface driver dvb_usb_af9015

```

```
andi@andibuntu:~$ lsusb
Bus 003 Device 003: ID 1462:8801 Micro Star International
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c50c Logitech, Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

(please see the verbose output in the txt-file attached!!)


```
andi@andibuntu:/dev/dvb$ ls
adapter0

```

I really hope you can help me with this!

---

### Post by desmane on 2008-12-01
anybody?

---

### Post by desmane on 2008-12-22
allright, I am a bit further, still doesnt work though: 

I did a 
```

rmmod dvb-usb-af9015
modprobe dvb-usb-af9015 dual_mode=1
```

it fails due some i2c error


Starting kaffeine gives me the second adapter:

```
andi@andibuntu:~$ kaffeine
/dev/dvb/adapter0/frontend0 : opened ( Afatech AF9013 DVB-T )
/dev/dvb/adapter1/frontend0 : opened ( Afatech AF9013 DVB-T )
0 EPG plugins loaded for device 0:0.
0 EPG plugins loaded for device 1:0.
Loaded epg data : 4063 events (126 msecs)
```

tuning a channel gives me: 

```
andi@andibuntu:~$ Tuning to: Phoenix / autocount: 0
DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory
Using DVB device 0:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 682000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
....... LOCKED.
NOUT: 1
dvbEvents 0:0 started
Tuning delay: 1117 ms
pipe opened
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
xine pipe opened /home/andi/.kaxtv.ts
```


I started recording and got very exciting cause it still displayed all other channels! 

```
Recording started: Phoenix
NOUT: 1

```

after clicking another channel (not one of the four that I can tune simultaniously), kaffeine spits out this one: 

```
Asked to stop
pipe closed
Live stopped
Tuning to: 3sat / autocount: 1
DvbCam::probe(): /dev/dvb/adapter1/ca0: : No such file or directory
Using DVB device 1:0 "Afatech AF9013 DVB-T"
tuning DVB-T to 490000000 Hz
inv:2 bw:0 fecH:2 fecL:9 mod:1 tm:1 gi:3 hier:0
........ LOCKED.
NOUT: 1
dvbEvents 1:0 started
Tuning delay: 1428 ms
pipe opened
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
xine pipe opened /home/andi/.kaxtv1.ts

```


What is going on here? Any thoughts are veerryy much appreciated!!

---

