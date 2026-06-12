---
title: "USB Internet not recognized"
date: 2010-08-01
forum: Hardware
---

### Post by Overthere on 2010-08-01
Hi everyone,
Many thanks to all the help I've gotten so far! This place is great!

I bought a flash drive for Internet access; but the computer doesn't see it.
It seems that I have to change the usb control from storage to something else, but I don't know how, I can't even find the device when plugged in!

Thanks in advance,
brian

---

### Post by sikander3786 on 2010-08-01
Hi.
 
You have to install usb-modeswitch.

[http://packages.ubuntu.com/lucid/usb-modeswitch](http://packages.ubuntu.com/lucid/usb-modeswitch)

---

### Post by Overthere on 2010-08-01
Hi sikander,
I already did. does it matter where I put it?

(Well, even if it does, I can't move it!) Then what?

Thanks in advance!
brian

---

### Post by sikander3786 on 2010-08-01
Follow the link.

[http://ubuntuforums.org/showthread.php?t=1439356](http://ubuntuforums.org/showthread.php?t=1439356)

---

### Post by Mi11z on 2010-08-01
> **sikander3786 said:**
> Follow the link.

[http://ubuntuforums.org/showthread.php?t=1439356](http://ubuntuforums.org/showthread.php?t=1439356)

ahh beat me :)

---

### Post by sikander3786 on 2010-08-01
> **Mi11z said:**
> ahh beat me :)

Now you can say "The World Is Not Enough". :p

---

### Post by Overthere on 2010-08-01
Ok, followed link and did lsusb command and got this:

brian@brian-laptop:~$ lsusb
Bus 001 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a103 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Obviously Huawei it is. But how do I change it now?

PS: I use wicd network manager, it seems different than the one on the link you gave!


(sorry for my inexperience!)
Thanks in advance!
brian

---

### Post by sikander3786 on 2010-08-01
Seems like I pulled up yet another for you.

[http://ubuntuforums.org/showthread.php?t=1197509](http://ubuntuforums.org/showthread.php?t=1197509)

---

### Post by Overthere on 2010-08-01
> **sikander3786 said:**
> Seems like I pulled up yet another for you.

[http://ubuntuforums.org/showthread.php?t=1197509](http://ubuntuforums.org/showthread.php?t=1197509)

Thanks sikander,
but I think I'm over my head here, seeing that I am not 100% sure what commands I need to put on my pc.

Can you walk me through step-by-step? I don't want to do something wrong w/command lines..

Brian

---

### Post by sikander3786 on 2010-08-01
> **farbird said:**
> [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

how to install..

if u downloaded the [modeswitch]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.2.tar.bz2") file into your desktop

run "terminal"
"cd ~/Desktop"
"sudo mv usb_modeswitch-1.0.2.tar.bz2 /usr/src"
"cd /usr/src"
"sudo tar -xvf usb_modeswitch-1.0.2.tar.bz2"
"cd usb_modeswitch-1.0.2.tar.bz2"
"sudo make clean"
"sudo make install"

that will get your usbmodeswitch installed.

next boot into windows
download the [sniffusb exe]("http://www.pcausa.com/Utilities/UsbSnoop/SniffUSB-x86-2.0.0006.zip")

install in xp.
run the sniffusb.
plug in your 12d1:1446 stick

now in the sniffusb screen, click on the "list device not present"
you shd see 3-4 devices with the id 12d1:1446

select them all and click on "install" under "filter control" on rightside.

u shd see in the main top window that the 3-4 devices with 12d1:1446 have the "filter installed" beside their id.

now, unplug the huawei usb and plug it back in after 5seconds.
if u do that, u shd see the log file size increased.

now view the log and save the logfile into a thumbdrive.

now we restart XP and boot into ubuntu. remove the stick before ubuntu starts booting.

once ubuntu starts. plug in the thumb drive, copy the log file into your desktop.

then run terminal

"cd ~/Desktop"
"sudo gedit snifflog.log"   or whatever filename u saved before

once gedit opens up on the gnome desktop, look for this by Control-F
"TransferBufferMDL"

there should be about 8 instances of it within the log file.
the one critical is the one that appears 4 rows after the line
```
PipeHandle           = 88bced1c [**endpoint 0x00000005**]
  TransferFlags        = 00000000 (USBD_TRANSFER_DIRECTION_**OUT**, ~USBD_SHORT_TRANSFER_OK)"
```

important here is the "out".
And there must be 2 long row of numbers below the transfermdl line which looks like this
```

   00000000: 55 53 42 43 90 4e d6 8a 24 00 00 00 80 00 08 ff
   00000010: 02 44 45 56 43 48 47 00 00 00 00 00 00 00 00

```
ignore the numbers before the colon and delete the spaces between the hex numbers. Join the 2 lines up so that it shows
```
55534243904ed68a24000000800008ff024445564348470000000000000000
``` 

* take note, this is just an example*

you will also need the "pipehandle" output which will show the endpoint hex, in this example, its **endpoint 0x00000005**.

now with these details, you can then create a usbmodeswitch config file

open another terminal
"sudo gedit /etc/usb_modeswitch.conf"
clear away all the contents of this file. 
put in these lines instead
```

DefaultVendor = 0x12d1
DefaultProduct = 0x1446

MessageEndpoint = 0x05
MessageContent = "55534243904ed68a24000000800008ff024445564348470000000000000000"

```

*make sure you use your own endpoint and messengecontent here n not directly clone the example above.*

now save the file in gedit.

next plug in the huawei usb stick, run terminal

"sudo usb_modeswitch"

u shd then be able to connect after u configure the network settings of your isp [ ie 3g access point name etc ]

there is also a way to automate it.

run terminal again
"sudo gedit /etc/udev/rules.d/45-huawei1660.rules"

gedit shd open an empty file
paste this code into it
```

SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"
```

since your vendor and product id is sames mine, u can clone the code above directly.
However, if u are following this guide to get your own huawei device, not 12d1:1446, working, u shd input the original vendor,product id [ ie the one shown in lsusb before switching]

enjoy

This is the step by step guide buddy. I know about your frustration but you've gotta go through it. Linux's got the learning curve for you. Hope you enjoy.

---

