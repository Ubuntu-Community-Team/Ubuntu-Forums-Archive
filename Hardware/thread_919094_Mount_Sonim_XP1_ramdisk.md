---
title: "Mount Sonim XP1 ramdisk"
date: 2008-09-13
forum: Hardware
---

### Post by Magnetixx on 2008-09-13
I managed to get hold of a Sonim XP1 cellphone to play with and managed to use it as a modem and browse the web using wvdial.

The next thing is to upload ringtones (just wav files), etc. When I plug in the USB nothing happens. I tried to mount it manually, but no luck. It seems to be a Philips Ramdisk. I don't even know what type of file system it is...  

Any Ideas?

Output from dmesg:

[I][ 5184.468000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 5184.740000] usb 2-1: configuration #1 chosen from 3 choices
[ 5184.748000] cdc_acm 2-1:1.1: ttyACM0: USB ACM device
[ 5184.752000] scsi8 : SCSI emulation for USB Mass Storage devices
[ 5184.752000] usb-storage: device found at 4
[ 5184.752000] usb-storage: waiting for device to settle before scanning
[ 5189.752000] usb-storage: device scan complete
[ 5189.756000] scsi 8:0:0:0: Direct-Access     Philips  Ramdisk 0        1.0  PQ: 0 ANSI: 0
[ 5189.764000] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 5189.764000] sd 8:0:0:0: Attached scsi generic sg2 type 0
[/I]

lsusb:
[I]Bus 005 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 005 Device 002: ID 0424:2503 Standard Microsystems Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0471:1201 Philips 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  [/I]

It is Bus2 dev 4

---

### Post by Speechless on 2008-09-21
Hello

I was installed gMobileMedia and connected with cable my Sonim XP1 to PC.
Now run gMobileMedia - in preferences choice port /dev/ttyACM0, and this software recognize that is Philips Nexperia 6120 platform and connect to phone (on Sonim screen I was info "connected to PC") now programm scan phone and hang up about 50% look at the screen...

[http://www.speechless.user.icpnet.pl/zrzutekranu-1.png](http://www.speechless.user.icpnet.pl/zrzutekranu-1.png)

I dont know what next...

Regards
Krzysztof

**Update**

I installed Wammu - with Wammu I can connect to Sonim (info on Sonim screen "connected to PC") in Wammu I have info about software version 21042006.0, Producent "Philips" access to contacts from SIM card, time synchro with Ubuntu, battery level and signal, SMS messages (you can add contact but if you wanna see this contact in the phone you must turn off sonim and turn on then you will se new contact which you added)

still I dont know how to access audio and pictures 

Krzysztof

---

### Post by Magnetixx on 2008-09-22
Thanks. 

Wammu Works. I'm also struggling to upload pics, but now I can at least sync my contacts.

---

