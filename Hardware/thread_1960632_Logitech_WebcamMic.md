---
title: "Logitech Webcam/Mic"
date: 2012-04-17
forum: Hardware
---

### Post by linxlvr on 2012-04-17
Hi all. I must be overlooking something, but I am pulling my hair out at this point. I was unable to get my Logitech webcam working. I was running debian, couldn't get it there, decided to try Lubuntu.

Went to the ubuntu forums, found a simillar thread, 

[http://ubuntuforums.org/showthread.php?t=1842059&highlight=logitech+mic](http://ubuntuforums.org/showthread.php?t=1842059&highlight=logitech+mic)

doesn't work for me, but this is the output I got.

~$ lsusb | grep -i logitech
Bus 002 Device 003: ID 046d:081a Logitech, Inc. 
~$ 

Decided to try "several layers lower" and got this out:

~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfcff8000 irq 45
 1 [U0x46d0x81a    ]: USB-Audio - USB Device 0x46d:0x81a
                      USB Device 0x46d:0x81a at usb-0000:00:1d.7-2, high speed
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe8fc000 irq 16

~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x46d0x81a [USB Device 0x46d:0x81a], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

None the less, when trying several permutations of the following, I get nothing.

arecord hw:1,2 -d 10 /tmp/test-mic.wav
aplay /tmp/test-mic.wav

I really don't know where to go from here.
Any help would be appreciated.
--
dw

---

