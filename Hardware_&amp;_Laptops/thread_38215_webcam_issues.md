---
title: "webcam issues"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by fackamato on 2005-05-30
Hi, I'm having some troubles with the webcam program. Here's the config:

[grab]
device = /dev/video1
text = "webcam %Y-%m-%d %H:%M:%S"

fg_red = 255
fg_green = 255
fg_blue = 255
width = 320
height = 240
delay = 3
wait = 0
input = ZC301-2
norm = pal
rotate = 0
top = 0
left = 0
bottom = -1
right = -1
quality = 75
trigger = 0
once = 0

[ftp]
host = localhost
user = fackamato
pass = password
dir  = /home/fackamato/www/webcam
file = webcam.jpg
tmp  = uploading.jpg
passive = 0
debug = 0
auto = 0
local = 1
ssh = 0

And here's what happens:

fackamato@fackamato:~/temp/camE-1.9 $ webcam
reading config file: /home/fackamato/.webcamrc
invalid input: ZC301-2

And running webcamd says:

fackamato@fackamato:~/temp/camE-1.9 $ webcamd start
Configuration file found
webcamd run, pictures are taken every 5 secondes
mv: kan inte ta status på "/home/fackamato/.webcamd/pre-webcam.jpg": Filen eller katalogen finns inte
mv: kan inte ta status på "/home/fackamato/.webcamd/webcam.jpg": Filen eller katalogen finns inte
config: invalid value for input: Television
valid choices for "input": "ZC301-2
"
ioctl: VIDIOCMCAPTURE(frame=0;height=200;width=266;format=4): Invalid argument

Any idea? This is very strange. :/

lsusb: Bus 003 Device 005: ID 046d:08a2 Logitech, Inc.
lsmod | grep usb: usbcore               119480  15 spca5xx,cpia_usb,pwc,stv680,dsbr100,ultracam,vicam,ibmcam,usbvideo,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

fackamato@fackamato:~/Desktop $ v4lctl -c /dev/video1 list
config: invalid value for input: Television
valid choices for "input": "ZC301-2
"
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
input      | choice | (null)  | ZC301-2 | ZC301-2

norm       | choice | PAL     | PAL     | PAL NTSC SECAM AUTO
bright     | int    |   32768 |       0 | range is 0 => 65535
hue        | int    |   32767 |       0 | range is 0 => 65535
color      | int    |   32767 |       0 | range is 0 => 65535
contrast   | int    |   32768 |       0 | range is 0 => 65535


Any ideas?

Kind regards, Mathias

---

