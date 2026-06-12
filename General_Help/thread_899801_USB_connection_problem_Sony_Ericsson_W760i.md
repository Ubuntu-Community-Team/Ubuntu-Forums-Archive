---
title: "USB connection problem Sony Ericsson W760i"
date: 2008-08-24
forum: General Help
---

### Post by InSearchOf on 2008-08-24
My Hardy will not recognize my W760i as a mass storage unit (it should opo up as a memorystick), and i am therefore unable to transfer files to the memory card (M2 - i do no have a compatible cardreader on my computer). The phone is only recognized as a camera, so downloading pictures from the phone is not a problem.

Anyone got a solution for this?

-InSearchOf

---

### Post by Crafty Kisses on 2008-08-25
Post the output of > lsusb

---

### Post by InSearchOf on 2008-08-25
lsusb
-----------------------------
Bus 005 Device 008: ID 0fce:e0c6 Sony Ericsson Mobile Communications AB 
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
---------------
This output is only for about one second (when the phone restarts into mass-storage mode), and then the phone restarts over and over again.. in a loop.

---

### Post by nephre on 2008-11-06
I have the same problem :(
On Windows it works fine. It seems, that kernel looses connection to phone and tries to re-initialize, then looses again and so on...

---

### Post by akadruid on 2008-11-23
Yeah my W760i has the same problem.  Just comes up with 'Preparing for Mass Storage' and reboots each time.

I've had the same thing on Windows occasionally too, although it does normally work.

To be honest, the whole system seems pretty flaky to me, my K750i didn't need to reboot and disable the phone system just to transfer files.

Doing a bluetooth 'browse files on this device' after pairing OK causes it to crash too.

But then using the phone's web browser also crashes it, and the first one I had the GPS stopped working entirely after a week and I had to get it replaced.

It's a nice phone but buggy as anything.

---

### Post by GonZo on 2009-07-01
Same issue, but sometimes it works! Suddenly, when trying to use the phone with virtual box and windows, ubuntu detected the phone as a memory card and asked me to open with f-spot, nautilus,... I opened with nautilus and copied a file (an ubuntu theme you can find [here]("http://www.myw760.lasyk.net/subsearch/Ubuntu%20Feisty%20Fawn/2/1/W760-Themes-Ubuntu%20Feisty%20Fawn-page1.html")) and worked! After that I umounted the file system.

Unfortunately I wasn't able to mount it again.

---

### Post by GonZo on 2009-07-02
Half-fixed!

If I select "Multimedia transfer" (or similar, my phone is configured in spanish) when connecting to the usb, I can connect to the phone and navigate the filesystem. At least I can read GPS files, pictures,... Unfortunately it seems the internal memory of the phone. Just 15Mb free, so it's imposible to load music.

When connecting as "massive storage device" my phone reboots (once) and shows a message (in spanish) like "Don't disconnect the USB wire before closing the PC application", but nothing happens on my ubuntu. Apart from my lsusb output:
```

******@richard:~$ lsusb
Bus 001 Device 008: ID 0fce:e0c6 Sony Ericsson Mobile Communications AB 
(... useless stuff...)

```
And dmesg output:
```

[ 4618.770439] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
[ 4618.795547] sd 8:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4618.795556] sd 8:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4618.797916] sd 8:0:0:1: [sdg] Sense Key : No Sense [current] 
[ 4618.797922] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
[ 4618.822675] sd 8:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4618.822687] sd 8:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4618.824544] sd 8:0:0:1: [sdg] Sense Key : No Sense [current] 
[ 4618.824553] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
[ 4618.849300] sd 8:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4618.849312] sd 8:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4618.851168] sd 8:0:0:1: [sdg] Sense Key : No Sense [current] 
[ 4618.851177] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
[ 4618.899797] sd 8:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4618.899805] sd 8:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4618.913079] sd 8:0:0:1: [sdg] Sense Key : No Sense [current] 
[ 4618.913091] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
[ 4618.958053] sd 8:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4618.958064] sd 8:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4618.959935] sd 8:0:0:1: [sdg] Sense Key : No Sense [current] 
[ 4618.959945] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
[ 4618.984805] sd 8:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4618.984815] sd 8:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4618.986685] sd 8:0:0:1: [sdg] Sense Key : No Sense [current] 
[ 4618.986696] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
[ 4619.011555] sd 8:0:0:0: [sdf] Sense Key : No Sense [current] 
[ 4619.011566] sd 8:0:0:0: [sdf] Add. Sense: No additional sense information
[ 4619.014181] sd 8:0:0:1: [sdg] Sense Key : No Sense [current] 
[ 4619.014189] sd 8:0:0:1: [sdg] Add. Sense: No additional sense information
(and lots of similar lines)
```
...which seems related to this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273372]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273372")

Maybe it's posible mounting it in a traditional way (sudo mount /dev/...) but I'm not sure what options I have to use.

Using bluetooth:
Connecting it as a bluetooth device seems correct but when I try to navigate the filesystem it causes the phone to shutdown. Sometimes before shutdown I'm able to see the filesystem root: two folders with phone memory and card memory.

Still working on it.

---

### Post by GonZo on 2009-07-02
**More information,**

  you can use [Wammu]("http://wammu.eu/") to read contacts, SMS, calendar,... Wammu is in ubuntu repositories. Just download it with "Add and remove..."

**Configuration**

Phone conected with USB wire, "Phone" selected as option, start Wammu, select Autodetection, USB cable,... the autodetection took some minutes for me. Once detected, wammu saves configuration and it will not ask you again. In case autodetection fails here are my settings.

Name:       Sony Ericsson W760i
Device:     /dev/ttyACM1
Connection: at19200

**Tests**
Tested sms', contacts and calls retrieving. Contacts individual modification takes some seconds and must be done quitely: it can break connection (must reconnect the usb wire and restart wammu to solve it). Sending sms directly from ubuntu works too.

**Modem**
At least for me, when connecting as "Phone" mode, ubuntu detects the modem and launches the assistant, asks for your company (in my case is Yoigo which is listed in the assistant), and configures it automatically. Connection and navigation not tested (my desktop pc is in a room without coverage).

---

### Post by GonZo on 2009-07-03
**Bluetooth fixed!**

**after phone software update** bluetooth connection works perfectly. After pairing, Wammu is able to connect and read/write all contacts, sms',... Filesystem navigation is possible with the Ubuntu's standard bluetooth app. Nautilus shows two folders: one for phone memory and the other for memory stick. I've tested it uploading arround 700MB of music to the phone, with a transfer rate of 67 KB/s. To get the highest transfer rates it's important to set the phone  as follows, after pairing go to "My devices" in bluetooth menu, point at your computer device, select "Options" and set "Allow connection forever". The other option will ask you for every connection and file upload/download. Remember that your menu names could be different, my phone is configured in spanish and I'm suposing the english traslations. 

and rock!!:guitar:

Sony Ericsson w760i software version -> 1202-3592 R3DA028 080908
Ubuntu Jaunty 9.04 updated.

My bluetooth computer's device it's USB like [this.[IMG]http://thumbs2.ebaystatic.com/pict/2204408643408080_1.jpg[/IMG]]("http://cgi.ebay.es/MINI-BLUETOOTH-USB-NUEVO-XP-Y-VISTA-FACIL-DE-USAR_W0QQitemZ220440864340QQcmdZViewItemQQptZLH_DefaultDomain_186?hash=item33534ca654&_trksid=p3286.c0.m14&_trkparms=65%3A12%7C66%3A2%7C39%3A1%7C72%3A1315%7C240%3A1318%7C301%3A0%7C293%3A1%7C294%3A50")

[[IMG]http://img133.imageshack.us/img133/637/photoo.th.jpg[/IMG]](http://img133.imageshack.us/i/photoo.jpg/)

---

