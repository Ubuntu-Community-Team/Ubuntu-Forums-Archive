---
title: "[SOLVED] Gutsy is killing me - EVDO with U727"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by nowhere@cox.net on 2008-01-25
OK, four machines and four sets of things that used to work in Feisty that not longer work in Gutsy. Pulling my hair out... wait I have no hair left...

Anyway, latest saga, Sprint + Novatel U727 + Gutsy = no internet. I dl'ed and followed the Sprint guide which fails on the very first step. modprobe -r usbserial is fine but reloading with the vendor and product then dmesg gives no cdc_acm module entry. 

Forums all say something I can't begin to understand about Gutsy changing usb but bottom line, it doesn't work, 

Anyone done the combo I am trying to get working have some insight? I am so far behind on the work I am supposed to have done already but havent done yet because I am using Gutsy instead of Feisty I could cry. Please let me know what info I need to provide to get this going.

Thanks!
btw, Lenovo T61, Sprint card works fine in Vista but I work in Linux...HELP

---

### Post by kplaxmaster on 2008-01-25
> **nowhere@cox.net said:**
> OK, four machines and four sets of things that used to work in Feisty that not longer work in Gutsy. Pulling my hair out... wait I have no hair left...

Anyway, latest saga, Sprint + Novatel U727 + Gutsy = no internet. I dl'ed and followed the Sprint guide which fails on the very first step. modprobe -r usbserial is fine but reloading with the vendor and product then dmesg gives no cdc_acm module entry. 

Forums all say something I can't begin to understand about Gutsy changing usb but bottom line, it doesn't work, 

Anyone done the combo I am trying to get working have some insight? I am so far behind on the work I am supposed to have done already but havent done yet because I am using Gutsy instead of Feisty I could cry. Please let me know what info I need to provide to get this going.

Thanks!
btw, Lenovo T61, Sprint card works fine in Vista but I work in Linux...HELP

I am not too sure because I don't actually use this, but just a quick question which hopefully fixes what you are doing...

How come you are doing "sudo modprobe -r usbserial."  You are actually removing the module usbserial, thus unable to use it.

Try just:
```
sudo modprobe usbserial
```

This will add the usbserial module, allowing you to use it.  Note that if you try to remove it and you never actually added it, you won't get an error either.

In order to see what modules are open use:
```
sudo lsmod
```

Thus, to check if your usbserial module is loaded:
```
sudo lsmod | grep usbserial
```
And you should get a line of output stating that usbserial is loaded, with x memory, running by y user/module.

Unless you purposely don't want usbserial to be used, which I don't understand why you wouldn't want to be using it unless of coarse there is a better module that you are replacing it with, then this could be your answer.

Hope this helps.

--- EDITED (added after)

If this works for you... you will have to always manually modprobe usbserial as the super-user (sudo).

However, if you add "usbserial" to /etc/modules, it will be added automatically at bootup.  If you do add it, make sure the last line in the file is a blank line and not "usbserial."  It is usually good practice to leave a blank line in all such config files.

---

### Post by nowhere@cox.net on 2008-01-25
Thanks for the reply. Sprint has a pretty extensive guide to installing the USB modem on a linux system and it is based on Ubuntu. The first steps are to (and I don't know the proper terminology) install the vendor and product codes in the kernel since the device is newer than the distributions. So you remove the usbserial module, then add it with the vendor and product code like this:

sudo modprobe usbserial vendor=0x1410 product=0x4100 (for my device)

I get no response prompt from this command but checking lsmod I see that the usbserial is loaded and usbcore has some stuff listed including usbserial.

The instructions say to now plug in the card and check dmesg for some lines about ttyUSB0 and ttyUSB1

sudo dmesg |grep -i ttyUSB

and I should see 

usb 5-1: generic converter now attached to ttyUSB0
usb 5-1: generic converter now attached to ttyUSB1

but the dmesg command shows nothing. Trying to connect to the modem using kppp fails too of course.

I should point out that the modem also has an integrated flash card which does connect ok.  

What do you think?

Thanks a ton so far!
Eric

---

### Post by nowhere@cox.net on 2008-01-25
OK a little bit of an update. I followed a HowTo here to blacklist airprime since the author believes Gutsy's USB for this is broken. Completing that, rebooting and modprobing usbserial with my vendor and product code supplied by sprint, same stuff happens. This is the interesting part: If I eject the mini builtin in flash drive that is auto mounted, THEN dmesg will display the usb 2-1: generic converter now attached to ttyUSBx where x is 0 through 3 (4 seperate groups of "now connected" lines). 

There is still no ttyACM0 etc however and kppp cannot query the modem on any of the ttyUSB's devices.

Hope someone knows how to fix this...

Thanks,
Eric

---

### Post by nowhere@cox.net on 2008-01-25
Ok I got a connection! The U727 seems exceptionally sensitive to the order in which you do things. I have already followed this HOWTO's steps 1-5 to blacklist airprime.
(here: [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989))

Next I need to connect the USB modem, then eject the CD (readonly flashdrive) that is automounted. Then:
```
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100
```

Then I am able to query the modem on /dev/ttyUSB0. I had to be careful since there were also /dev/tty/ttyUSB0 devices listed in kppp.

I am in the process of running dslreports speed test but I had to dl java plugins and such and the 22MB required is taking 10 minutes to dl so I suspect the speed is not too good :-D

Next stop will be a speed tweaking HOWTO.

I hope this helps anyone else with this particular device get connected!

Eric

---

