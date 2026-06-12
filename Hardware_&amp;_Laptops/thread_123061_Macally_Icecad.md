---
title: "Macally Icecad"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by RagingOcelot on 2006-01-29
I can't seem to get this tablet working due to what appears to be very little interest in the linux community to form a driver for this device.  My dmesg is as follows:

[4600613.930000] usb 1-2.1: new low speed USB device using uhci_hcd and address 100
[4600614.129000] hiddev96: USB HID v1.10 Device [Macally Peripherals Macally Mini Tablet] on usb-0000:00:04.2-2.1

...so it doesn't just hitch a ride with Wacom internals or anything, unfortunately.  Should I beat a dead horse and keep trying or just ebay it and find an Aiptek or Wacom tablet?

---

### Post by joker_poker on 2006-07-17
If you look at the macally europe driver's page. 

[http://www.macally-europe.com/driversandmanuels.php?type=drivers](http://www.macally-europe.com/driversandmanuels.php?type=drivers)


The PC driver for this device is the same as the PC driver for ACecad's Flair. 

[http://www.acecad.com.tw/driver/u340-en.zip](http://www.acecad.com.tw/driver/u340-en.zip)


So iam guessing the linux driver for Acecad shud also work for this one.

[http://acecad.sourceforge.net/](http://acecad.sourceforge.net/)


I however dont have the device so nothing from personal exp.

Has anyone had better luck?

---

### Post by prussianblue.hcn on 2007-02-18
I am having the exact same problem and am very new to ubuntu I have the acecad package installed. It seems that the problem we are facing is you need to bind the macally tablet to the acecad driver. I haven't got this sorted out yet but I found a promising lead in a redhat forum here 
[http://www.fedoraforum.org/forum/archive/index.php/t-123842.html.btw](http://www.fedoraforum.org/forum/archive/index.php/t-123842.html.btw) ignore the rc.local reference. 

"terabyte
2006-09-13, 06:50 PM PDT
If anybody is interested:

The Acecad driver works, but you have to force the kernel to use it. Use sysfs to do this; you will have to write the string 2222 2520 0 0 3 0 0 usb_acecad to the new_id entry of the usb_acecad driver. You will also have to unbind the tablet from usbhid and bind it to usb_acecad (binding it may happen automatically, I am not sure at the moment). This can probably be automated with rc.local."

---

### Post by prussianblue.hcn on 2007-02-21
This comes from a redhat forum from a very kind user. I have yet to try it myself but its worth a try if you are comfortable patching your kernel which is the first step. I personally have nothing to lose since ubuntu has its own HD on my computer.But be forewarned  first follow the steps at acecad.sourceforge.net/install.html.
then:

The key was to use the acecad kernel module, and then sysfs to force it to be used for the Macally tablet. The basic idea:

modprobe acecad
cd /sys/bus/usb/devices
ls
<Now, insert your tablet.>
ls
(Something new should have appeared in the directory listing. That is the tablet device -- I'll call it 3-1:1.0, you will probably have a different number)
cd /sys/bus/usb/drivers/hiddev
cat 3-1:1.0 > unbind
cd ../usb_acecad
cat 3-1:1.0 > bind

And now, everything should work. The tablet will work as a mouse -- that was good enough for my purposes, so I left it at that. You can probably use xorg.conf to configure it as a true tablet, that will detect things like pressure, but you would have to see the tablet documentation for that. There should be a way to automate this process, if you need to -- for my purposes, the 30 seconds to took to go through sysfs was acceptable. Also, I never tried to suspend my system while the tablet was in use, I am not sure what the result would be.

Good luck,
Benjamin Kreuter

---

### Post by TygerFish on 2008-01-28
This is a dusty thread, but it's got most of the relevant information on the problem.  I've recently acquired an icecad tablet myself, and I know it works since the LED light corresponds to pen activity and the following is at the end of my dmesg output when I unplug and re-plug the tablet:
```
[ 4600.168000] usb 3-1: USB disconnect, address 3
[ 4604.208000]  usb 3-1: new low speed USB device using uhci_hcd and address 4
[ 4604.500000]  usb 3-1: configuration #1 chosen from 1 choice
[ 4604.524000]  hiddev 97: USB HID v1.10 Device [Macally Peripherals Macally Mini Tablet] on usb-0000:00:1d.2-1
```

On my Gutsy laptop, the Acecad driver/kernel module appears to be installed by default, as the following command produces no output:
```
$ sudo modprobe acecad
```

The Xorg input drivers currently have a package in the repositories and are easily installed:
```
$ xserver-xorg-input-acecad
```

Then, I added the following to my xorg.conf file, as instructed [here]("http://acecad.sourceforge.net/install.html"):
```
Section "InputDevice"
   Identifier "iceCAD"
   Driver "acecad"
   Option  "Device" "auto-dev"
EndSection
```

At this point, I restarted the X server with ctrl-alt-backspace, but the tablet still produced no input.  I checked the Xorg log:
```
$ cat /var/log/Xorg.0.log | grep cad
(II) LoadModule: "acecad"
(II) Loading /usr/lib/xorg/modules/input//acecad_drv.so
(II) Module acecad: vendor="X.Org Foundation"
(II) iceCAD: probing event devices for Acecad tablets
(WW) iceCAD: no Acecad device found (checked 20 nodes, no device name started with 'acecad')
```

So, something (the X server? the usb infrastructure? both?) isn't figuring out that the icecad needs to be treated like an acecad tablet.  Following the instructions in the last post above, I tried the following commands:
```
$ cd /sys/bus/usb/drivers/hiddev
$ cat 3-1:1.0 > unbind
bash: unbind: Permission denied
$ sudo cat 3-1:1.0 > unbind
bash: unbind: Permission denied
```

That's the part that really puzzles me!  Why can't I edit that file, even as root?  I also tried:
```
$ sudo chmod u+rwx unbind
$ sudo cat 3-1:1.0 > unbind
bash: unbind: Permission denied
```

Even stranger.  I know very little about kernel modules, drivers, and sysfs.  Can anyone offer me any help or suggestions?

---

### Post by noisesmith on 2008-03-11
> **TygerFish said:**
> This is a dusty thread, but it's got most of the relevant information on the problem.  I've recently acquired an icecad tablet myself, and I know it works since the LED light corresponds to pen activity and the following is at the end of my dmesg output when I unplug and re-plug the tablet:
```
[ 4600.168000] usb 3-1: USB disconnect, address 3
[ 4604.208000]  usb 3-1: new low speed USB device using uhci_hcd and address 4
[ 4604.500000]  usb 3-1: configuration #1 chosen from 1 choice
[ 4604.524000]  hiddev 97: USB HID v1.10 Device [Macally Peripherals Macally Mini Tablet] on usb-0000:00:1d.2-1
```

On my Gutsy laptop, the Acecad driver/kernel module appears to be installed by default, as the following command produces no output:
```
$ sudo modprobe acecad
```

The Xorg input drivers currently have a package in the repositories and are easily installed:
```
$ xserver-xorg-input-acecad
```

Then, I added the following to my xorg.conf file, as instructed [here]("http://acecad.sourceforge.net/install.html"):
```
Section "InputDevice"
   Identifier "iceCAD"
   Driver "acecad"
   Option  "Device" "auto-dev"
EndSection
```

At this point, I restarted the X server with ctrl-alt-backspace, but the tablet still produced no input.  I checked the Xorg log:
```
$ cat /var/log/Xorg.0.log | grep cad
(II) LoadModule: "acecad"
(II) Loading /usr/lib/xorg/modules/input//acecad_drv.so
(II) Module acecad: vendor="X.Org Foundation"
(II) iceCAD: probing event devices for Acecad tablets
(WW) iceCAD: no Acecad device found (checked 20 nodes, no device name started with 'acecad')
```

So, something (the X server? the usb infrastructure? both?) isn't figuring out that the icecad needs to be treated like an acecad tablet.  Following the instructions in the last post above, I tried the following commands:
```
$ cd /sys/bus/usb/drivers/hiddev
$ cat 3-1:1.0 > unbind
bash: unbind: Permission denied
$ sudo cat 3-1:1.0 > unbind
bash: unbind: Permission denied
```

That's the part that really puzzles me!  Why can't I edit that file, even as root?  I also tried:
```
$ sudo chmod u+rwx unbind
$ sudo cat 3-1:1.0 > unbind
bash: unbind: Permission denied
```

Even stranger.  I know very little about kernel modules, drivers, and sysfs.  Can anyone offer me any help or suggestions?


1) modprobe, as with a majority of the classic command line utilities, gives no output when it does not detect any errors. It would only give output if the module did not exist, or failed to load properly.

2) ```
sudo command > file
``` tries to write to the file as your current user, due to shell syntax. Your best bet is ```
sudo sh -c 'command > file'
``` if the command you want has ' characters in it, escape them, or source a file with ., or just run ```
sudo bash
```

3) I am trying to figure out what this sysfs thing is. I really want my new macally icecad to work, I have big plans for it. If I make it work on my ubuntu system, I will post how I did it here.

---

### Post by noisesmith on 2008-03-25
OK, I found some free time again.

Here is a script that will bind any icecad device plugged into your usb to the acecad driver, loading that driver if necessary
```

#!/bin/sh
# this file should be run as root, before starting your X server, if you want
# to use the X11 drivers for your tablet
# (or, optionally, restart your X server after running it)
# tested under ubuntu gutsy
#
# justin smith, noisesmith@gmail.com, 2008

# DEVICE_STRING is the string for my macally icecad, it should work for yours,
# put the contents of the modalias file for your device here, otherwise
DEVICE_STRING='usb:v2222p2520d0010dc00dsc00dp00ic03isc01ip02'
DEVICE_ALIASES=$(grep -l ${DEVICE_STRING} /sys/bus/usb/devices/[0-9]*/modalias)
if [ ${#DEVICE_ALIASES} -gt 0 ]
then
        modprobe acecad
        echo -n '2222 2520 0 0 3 0 0 usb_acecad' \
            > /sys/bus/usb/drivers/usb_acecad/new_id
        for i in ${DEVICE_ALIASES}
        do 
                DEVICE=$(echo ${i} | sed -e \
                        's,/sys/bus/usb/devices/\([^/]*\)/modalias,\1,')
                echo -n ${DEVICE} > /sys/bus/usb/drivers/usbhid/unbind
                echo -n ${DEVICE} > /sys/bus/usb/drivers/usb_acecad/bind
                exit 0
        done
else
        echo "no icecad device found"
        exit 1
fi


```

I had some wild goose chases on the way to figuring this out, for example the cat command recommended higher in the thread overwrites the special bind/unbind files with empty files, since the thing you are sending is a string, not the contents of a file.

Anyway, if you save the preceding code block, make it executable, and follow the instructions in the comment, the hard part of making your icecad work is done. You will also want the appropriate lines in your xorg.conf. I either don't have that right yet, or my stylus is broken (a battery leaked inside it). If I figure that part out, I will post the code to add to your xorg.conf as well.

Good luck.

Also, you may note a feature of sed in this script that I wish more people took advantage of: sed can figure out what symbol you are using to separate command clauses by context, so you don't have to escape hundreds of slashes for processing directory names.

---

