---
title: "GrabBeeX-usb 2/ Video Grabber -NEED HELP"
date: 2009-09-26
forum: Hardware
---

### Post by Sultan-mrm on 2009-09-26
Hi,

I have video grabber usb,


[IMG]http://fl2.shopmania.org/files/photos-south-africa/1105/manhattan-hi-speed-usb-2-0-video-grabber~1104189.jpg[/IMG]

 it was working good in ubuntu 8.10,
but with ubuntu 9.04 and kernels 2.6.28.../29/30/31 no luck :(

it's reading as "ID eb1a:2800 eMPIA Technology, Inc. Terratec Cinergy 200"

and when test it with multimedia system selector is keep testing but
no video showing .


# output of lsusb :


```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID eb1a:2800 eMPIA Technology, Inc. Terratec Cinergy 200
Bus 002 Device 003: ID 064e:a117 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```



Thanks for help and sorry for bad language :)


Sultan

---

### Post by Sultan-mrm on 2009-09-27
up

---

### Post by khadar on 2009-10-04
> **Sultan-mrm said:**
> Hi,

I have video grabber usb,


[IMG]http://fl2.shopmania.org/files/photos-south-africa/1105/manhattan-hi-speed-usb-2-0-video-grabber~1104189.jpg[/IMG]

 it was working good in ubuntu 8.10,
but with ubuntu 9.04 and kernels 2.6.28.../29/30/31 no luck :(

it's reading as "ID eb1a:2800 eMPIA Technology, Inc. Terratec Cinergy 200"

and when test it with multimedia system selector is keep testing but
no video showing .


# output of lsusb :


```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID eb1a:2800 eMPIA Technology, Inc. Terratec Cinergy 200
Bus 002 Device 003: ID 064e:a117 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```



Thanks for help and sorry for bad language :)


Sultan









Install TVtime Television Viewer

:~$ sudo apt-get install tvtime


(If you have more than one video capture device like webcamera 
change the usb grabber ID in
 sudo gedit /etc/tvtime/tvtime.xml 
  <!-- This sets the default capture device to use. -->
  <option name="V4LDevice" value="/dev/video[COLOR="Red"]1[/COLOR]"/>
)

---

### Post by Sultan-mrm on 2009-10-07
thank you for your help but no luck :(

any way to disable web-cam maybe will work ?

---

