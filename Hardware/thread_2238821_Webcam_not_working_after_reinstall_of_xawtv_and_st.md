---
title: "Webcam not working after reinstall of xawtv and streamer"
date: 2014-08-10
forum: Hardware
---

### Post by filiplundby on 2014-08-10
Earlier today I had my webcam working. 

After connection the device it didn't show up in /dev/video* - So I added it manually:

```
$ sudo mknod /dev/video0 c 81 0
```

And then installed xawtv and streamer:
```
$ sudo apt-get install xawtv streamer
```

I was now able to cature still images using streamer:
```
$ sudo streamer -c /dev/video0 -b 16 -o outfile.jpeg
```

For the fun of it I wanted to do everything all over to make sure I did it right. So I removed the device:
```
$ sudo rm /dev/video0
```

And uninstalled xawtv and streamer:
```
$ sudo apt-get remove xawtv streamer
```

And then installed everything again ...

But now when I try to run streamer it throws this error:
```
$ sudo streamer -c /dev/video0 -b 16 -o outfile.jpeg
files / video: JPEG (JFIF) / audio: none
v4l2: open /dev/video0: No such device or address
vid-open: failed: libv4l
no grabber device available
```


Some bouns info ...

```
$ lsusb
Bus 001 Device 003: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) STV0680 Camera
```

```
$ lsmod | grep stv0680
gspca_stv0680        12995    0
gspca_main           36692    1 gspca_stv0680
```

```
$ dmesg | tail
[  176.059019] usbcore: registered new interface driver uvcvideo
[  176.059022] USB Video Class driver (1.1.1)
[ 5355.588191] usb 1-2: USB disconnect, device number 3
[ 5358.524158] usb 1-2: new full-speed USB device number 4 using ohci-pci
[ 5358.823383] usb 1-2: New USB device found, idVendor=0553, idProduct=0202
[ 5358.823387] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5358.823389] usb 1-2: Product: USB Dual-mode Camera
[ 5358.823391] usb 1-2: Manufacturer: STMicroelectronics
[ 5358.825441] gspca_main: stv0680-2.14.0 probing 0553:0202
[ 5359.978933] gspca_main: stv0680-2.14.0 probing 0553:0202
```



Help much appreciated :KS

---

