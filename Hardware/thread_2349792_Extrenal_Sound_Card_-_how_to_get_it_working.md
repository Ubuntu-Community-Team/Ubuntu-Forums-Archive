---
title: "Extrenal Sound Card - how to get it working?"
date: 2017-01-18
forum: Hardware
---

### Post by 171742 on 2017-01-18
Hello,

I got ubuntu 16.6. on an acer aspirev3-371-series. 

I bought this external sound card:

[http://www.ebay.de/itm/192015744450?_trksid=p2060353.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT](http://www.ebay.de/itm/192015744450?_trksid=p2060353.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT)


If I plug it in only the red light comes on blinking. Other USb: Red light stable. But still in the controls of the system I cant get any signal of the microphone whatsover. This is what the log says:


```
DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=494988 PROTO=UDP SPT=8612 DPT=8610 LEN=24
Jan 18 16:43:22 e-NC10 kernel: [ 846.140682] [UFW BLOCK] IN=wlan1 OUT= MAC= SRC=fe80:0000:0000:0000:6257:18ff:fe15:4cb2 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=883940 PROTO=UDP SPT=8612 DPT=8612 LEN=24
Jan 18 16:43:22 e-NC10 kernel: [ 846.140702] [UFW BLOCK] IN=wlan1 OUT= MAC= SRC=fe80:0000:0000:0000:6257:18ff:fe15:4cb2 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=494988 PROTO=UDP SPT=8612 DPT=8610 LEN=24
Jan 18 16:43:28 e-NC10 kernel: [ 851.665958] usb 2-1: new full-speed USB device number 10 using xhci_hcd
Jan 18 16:43:28 e-NC10 kernel: [ 851.797418] usb 2-1: New USB device found, idVendor=1b3f, idProduct=2008
Jan 18 16:43:28 e-NC10 kernel: [ 851.797422] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan 18 16:43:28 e-NC10 kernel: [ 851.797425] usb 2-1: Product: USB Audio Device
Jan 18 16:43:28 e-NC10 kernel: [ 851.797427] usb 2-1: Manufacturer: GeneralPlus
Jan 18 16:43:28 e-NC10 kernel: [ 851.807309] input: GeneralPlus USB Audio Device as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.3/0003:1B3F:2008.0007/input/input19
Jan 18 16:43:28 e-NC10 kernel: [ 851.862235] hid-generic 0003:1B3F:2008.0007: input,hidraw1: USB HID v2.01 Device [GeneralPlus USB Audio Device] on usb-0000:00:14.0-1/input3
Jan 18 16:43:28 e-NC10 mtp-probe: checking bus 2, device 10: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1"
Jan 18 16:43:28 e-NC10 mtp-probe: bus: 2, device: 10 was not an MTP device
Jan 18 16:43:28 e-NC10 systemd-udevd[3752]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 2' failed with exit code 99.
Jan 18 16:43:28 e-NC10 rtkit-daemon[1511]: Supervising 4 threads of 1 processes of 1 users.
Jan 18 16:43:28 e-NC10 rtkit-daemon[1511]: Successfully made thread 3767 of process 1510 (n/a) owned by '1000' RT at priority 5.
Jan 18 16:43:28 e-NC10 rtkit-daemon[1511]: Supervising 5 threads of 1 processes of 1 users.
Jan 18 16:43:28 e-NC10 rtkit-daemon[1511]: Supervising 5 threads of 1 processes of 1 users.
Jan 18 16:43:28 e-NC10 rtkit-daemon[1511]: Successfully made thread 3768 of process 1510 (n/a) owned by '1000' RT at priority 5.
Jan 18 16:43:28 e-NC10 rtkit-daemon[1511]: Supervising 6 threads of 1 processes of 1 users.
Jan 18 16:43:28 e-NC10 kernel: [ 852.069117] [UFW BLOCK] IN=wlan1 OUT= MAC= SRC=fe80:0000:0000:0000:6257:18ff:fe15:4cb2 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=883940 PROTO=UDP SPT=8612 DPT=8612 LEN=24
Jan 18 16:43:28 e-NC10 kernel: [ 852.069144] [UFW BLOCK] IN=wlan1 OUT= MAC= SRC=fe80:0000:0000:0000:6257:18ff:fe15:4cb2 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=494988 PROTO=UDP SPT=8612 DPT=8610 LEN=24
Jan 18 16:43:28 e-NC10 kernel: [ 852.079317] [UFW BLOCK] IN=wlan1 OUT= MAC= SRC=fe80:0000:0000:0000:6257:18ff:fe15:4cb2 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=883940 PROTO=UDP SPT=8612 DPT=8612 LEN=24
Jan 18 16:43:28 e-NC10 kernel: [ 852.079339] [UFW BLOCK] IN=wlan1 OUT= MAC= SRC=fe80:0000:0000:0000:6257:18ff:fe15:4cb2 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=494988 PROTO=UDP SPT=8612 DPT=8610 LEN=24
Jan 18 16:43:30 e-NC10 kernel: [ 854.143118] [UFW BLOCK] IN=wlan1 OUT= MAC=60:57:18:15:4c:b2:00:24:fe:71:7e:98:08:00 SRC=192.168.178.1 DST=192.168.178.93 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=58832 DF PROTO=TCP SPT=3862 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0
Jan 18 16:43:33 e-NC10 kernel: [ 857.112211] [UFW BLOCK] IN=wlan1 OUT= MAC=60:57:18:15:4c:b2:00:24:fe:71:7e:98:08:00 SRC=192.168.178.1 DST=192.168.178.93 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=58834 DF PROTO=TCP SPT=3862 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0
Jan 18 16:44:04 e-NC10 kernel: [ 887.525359] [UFW BLOCK] IN=wlan1 OUT= MAC=60:57:18:15:4c:b2:00:24:fe:71:7e:98:08:00 SRC=192.168.178.1 DST=192.168.178.93 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38239 DF PROTO=TCP SPT=3863 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0
Jan 18 16:44:13 e-NC10 kernel: [ 896.536668] [UFW BLOCK] IN=wlan1 OUT= MAC=60:57:18:15:4c:b2:00:24:fe:71:7e:98:08:00 SRC=192.168.178.1 DST=192.168.178.93 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38243 DF PROTO=TCP SPT=3863 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0 
```


China Noname Mic seems to do nothing as well:
```
Jan 18 17:05:10 e-NC10 whoopsie[912]: [17:05:10] Uploading /var/crash/_usr_bin_gnome-system-log.1000.crash.
Jan 18 17:05:15 e-NC10 kernel: [ 2158.222022] [UFW BLOCK] IN=wlan1 OUT= MAC=60:57:18:15:4c:b2:00:24:fe:71:7e:98:08:00 SRC=192.168.178.1 DST=192.168.178.93 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=51908 DF PROTO=TCP SPT=4028 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0
Jan 18 17:05:17 e-NC10 kernel: [ 2161.191719] [UFW BLOCK] IN=wlan1 OUT= MAC=60:57:18:15:4c:b2:00:24:fe:71:7e:98:08:00 SRC=192.168.178.1 DST=192.168.178.93 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=51910 DF PROTO=TCP SPT=4028 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0
Jan 18 17:05:35 e-NC10 kernel: [ 2178.599815] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:01:00:90:a9:ce:84:7b:08:00 SRC=192.168.178.2 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=11819 PROTO=2
Jan 18 17:05:52 e-NC10 kernel: [ 2195.598560] [UFW BLOCK] IN=wlan1 OUT= MAC=60:57:18:15:4c:b2:00:24:fe:71:7e:98:08:00 SRC=192.168.178.1 DST=192.168.178.93 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=39070 DF PROTO=TCP SPT=4030 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0 
```


My aim is to reduce background sounds when making a video. I got a horrible static there. The log is about my only trick, I am pretty much a rookie. So easy please!

Thanks!

---

### Post by QIII on 2017-01-18
Hello!

Please use the default color and font.

Also, please enclose terminal commands and output in code tags:

1.  Click the # button above the text input box, place your cursor between the code tags and then type or paste your text.

2.  Type or paste your text, highlight it and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

