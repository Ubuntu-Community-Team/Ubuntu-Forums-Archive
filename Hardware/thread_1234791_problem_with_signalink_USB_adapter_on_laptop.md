---
title: "problem with signalink USB adapter on laptop"
date: 2009-08-08
forum: Hardware
---

### Post by ml41782 on 2009-08-08
Good Morning, 
I have an HP mini running the ubuntu remix. This laptop is dedicated for my hamradio use. 
 
I also have a desktop running ubuntu 9.04. When I plug in the signalink USB to the desktop is does work and it comes up as a /dev/dsp0 device. 
 
when I do the same thing to the laptop it doesn't work. I did a tail of the message log and this is what I get. 
 
 
[FONT=bookman old style][FONT=Arial Narrow][SIZE=2]otg1017@Michael-Lussier-K4MQF:~$ sudo tail -f /var/log/messages[/SIZE][/FONT]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.296540] usb 4-1: configuration #1 chosen from 1 choice[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.411722] usbcore: registered new interface driver hiddev[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.415448] input: Burr-Brown from TI USB Audio CODEC as /class/input/input8[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.448493] generic-usb 0003:08BB:2904.0001: input,hidraw0: USB HID v1.00 Device [Burr-Brown from TI USB Audio CODEC ] on usb-0000:00:1d.3-1/input3[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.448532] usbcore: registered new interface driver usbhid[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.448539] usbhid: v2.6:USB HID core driver[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:01 Michael-Lussier-K4MQF kernel: [ 538.569902] usbcore: registered new interface driver snd-usb-audio[/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:38 Michael-Lussier-K4MQF sudo: pam_sm_authenticate: Called [/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:38 Michael-Lussier-K4MQF sudo: pam_sm_authenticate: username = [otg1017] [/FONT][/SIZE]
[SIZE=2][FONT=bookman old style]Aug 7 08:28:38 Michael-Lussier-K4MQF sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) [/FONT][/SIZE]
 
[SIZE=2][FONT=bookman old style]Any thoughts ? Tigertronics was closed yesterday so I had no help from them. [/FONT][/SIZE][/FONT]
 
[FONT=bookman old style][FONT=Arial Narrow][SIZE=2]I just want to get my psk31 program up and running[/SIZE][/FONT][/FONT]
 
 
[FONT=bookman old style][FONT=Arial Narrow][SIZE=2]Thank you for any help[/SIZE][/FONT][/FONT]
 
[FONT=bookman old style][FONT=Arial Narrow][SIZE=2]Michael [/SIZE][/FONT][/FONT]

---

