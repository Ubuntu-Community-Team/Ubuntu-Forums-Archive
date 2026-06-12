---
title: "Asus EeePC T91MT multitouch touchscreen [Lucid 10.04]"
date: 2010-06-11
forum: Hardware
---

### Post by H3g3m0n on 2010-06-11
MAVERICK UPDATE: I have attached a multitouch-kernel-source package modified for maverick (it also includes the hid-core.c and hid-quirks.c changes. Maverick users should just install the attached package and ignore most of the following instructions except for the rotate button fix.

MAVERICK UPDATE2: [jtjs posted]("http://ubuntuforums.org/showpost.php?p=10212762&postcount=39") that there is now a [utouch PPA]("https://launchpad.net/~utouch-team/+archive/utouch") with working DKMS multitouch hid-mosart drivers for Maverick.
> sudo add-apt-repository ppa:utouch-team/utouch
sudo apt-get update
sudo apt-get install hid-mosart-dkms

If you have already installed the maverick deb below, you should probably uninstall it first. After install and reboot, check your using hid-mosart with lsmod.

MAVERICK UPDATE3: Probably not much use but while playing around I also made a multitouch-kernel-source 1.556 with the hid-mosart multitouch patches (multitouch is already in the utouch-team PPA).

--------------------------
Lucid:

Add the multitouch PPA:
```
sudo add-apt-repository ppa:chasedouglas/multitouch
sudo apt-get update 
sudo apt-get install multitouch-kernel-source
```

Edit /usr/src/multitouch-1.5/drivers/hid/hid-core.c
Comment out line 1554 so it looks like:
```
//{ HID_USB_DEVICE(USB_VENDOR_ID_ASUS, USB_DEVICE_ID_ASUS_T91MT)},
```


Edit /usr/src/multitouch-1.5/drivers/hid/usbhid/hid-quirks.c
Add the following line after "} hid_blacklist[] = {"
```
{ USB_VENDOR_ID_ASUS, USB_DEVICE_ID_ASUS_T91MT, HID_QUIRK_MULTI_INPUT },
```

Recompile the multitouch drivers (this takes a while)
```
sudo dpkg-reconfigure multitouch-kernel-source
```

Now when you reboot you should have a working touchscreen. There is also a fix for ensuring the input is correct when rotated.

Calibration can be done using the T101's eGalax calibrator:
```
cd /tmp && wget "http://www.philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-1-i386.deb" && dpkg -i eeepc-t101mt-calibrator-0.0.2-1-i386.deb
```

Then run with:
```
sudo egalax_calibrator_x11
```
Or the the &#8220;System>Administration>Calibrate touch screen&#8221; menu entry

To get the input rotation working (you also need to fix to get the silver button working in the T91MT howto), add the following to the end of /etc/acpi/rotatescreen.sh:
```
INPUTDEV="9"
ROTATION=`cat /var/lib/acpi-support/screen-rotation`
case $ROTATION in
    normal) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 0 0;;
    left) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 1
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 0;;
    right) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 1
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 0 1;;
    inverted) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0
       xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 1;;
esac
```

If you want a program for manual xrandr rotation:
```
cd /tmp && wget "http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb" && dpkg -i philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb
sudo sed -i  's/eGalax/AsusTek | tail -n 1/g' /usr/bin/touchrotate
```
Then use "touchrotate left" and such.

In one big copy'n'paste command (except for the /etc/acpi/rotatescreen.sh).
```
sudo add-apt-repository ppa:chasedouglas/multitouch
sudo apt-get update 
sudo apt-get install -y multitouch-kernel-source
sudo sed -i 's/^.*ASUS_T91MT/\/\/&/g' /usr/src/multitouch-1.5/drivers/hid/hid-core.c
sudo sed -i 's/^.*ALPS.*$/&\n\t{ USB_VENDOR_ID_ASUS, USB_DEVICE_ID_ASUS_T91MT, HID_QUIRK_MULTI_INPUT },/g' /usr/src/multitouch-1.5/drivers/hid/usbhid/hid-quirks.c
sudo dpkg-reconfigure multitouch-kernel-source
cd /tmp && wget "http://www.philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-1-i386.deb" "http://philmerk.de/dwl/deb/egalax-multitouch-driver-common.deb" && sudo dpkg -i egalax-multitouch-driver-common.deb && sudo dpkg -i eeepc-t101mt-calibrator-0.0.2-1-i386.deb
sudo sed -i  's/eGalax/AsusTek | tail -n 1/g' /usr/bin/touchrotate
echo "event=hotkey (ATKD|HOTK) 0000007b\naction=/etc/acpi/rotatescreen.sh" | sudo tee /etc/acpi/events/asus-rotate-t91
```

-----------old--------------
I have been having a go at getting the touchscreen running under Lucid now that we have a (mostly) [working video driver]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/").

I know that it should work as there is a [video of it]("http://www.youtube.com/watch?v=Ei58CkPxDr0").

Right now I can't even get the basic dev entries to show up. /dev/input/eventX (there are 1-7 but none the touchscreen according to lsinput), /dev/usb/* (usb directory doesn't exist) or /dev/hidinput devices to show up. Nothing appears in /proc/bus/input/devices, xinput list, lshw. It works fine under 9.10 using the modified evtouch drivers. The problem might be that Lucid no longer ships with HAL but I haven't yet worked out how to go about generating /dev/ nodes.

From what I see posted, the T91MT uses the Mosart driver (although [someone]("http://ubuntuforums.org/showpost.php?p=9221280&postcount=4") on the T101MT post claimed the egalax driver would also work with it but I haven't found anyone actually claiming to have the T91MT working at all on Lucid).

The mosart driver was backported to the Lucid 10.04 kernel and ships with it as hid-mosart, although there is a bit on the [ENAC kernel howto]("http://lii-enac.fr/en/projects/shareit/linux-howto.html") specific for Ubuntu 10.04 claiming that it still requires a hid.h patch.

There is a [Ubuntu multitouch-dev mailing list]("https://lists.launchpad.net/multi-touch-dev/threads.html") (unfortunately readonly) and [ppa]("https://launchpad.net/~chasedouglas/+archive/multitouch") with the ENAC drivers that where missing from 10.04 as a DKMS (mainly the egalax one). This seems to include the hid.h changes too. This seems like it would be the simplest solution since it doesn't require a kernel recompile.

But on boot neither mosart or egalax modules are autoloaded. Loading mosart manually doesn't seem to register in /var/log/messages or dmesg although it could just be silent. 'xinput list' doesn't show anything. It's loaded according to lsmod though. After loading the module nothing new shows up in dev, proc, lshw and so on.

I have also tried the [2.6.34 kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), looking at the hid.h file in source it appears to have the id's changed the way the ENAC site says so it should work without a recompile. 2.6.34 doesn't seem to be shipping with the hid-egalax module, but the mosart one is in there. I get the same problem as with the PPA packages.

There is a usbtouchscreen module, I tried modprobing that without any success. (I saw another thread saying you had to do it before usbhid but that didn't help).

There is also the official [eGalax drivers]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm"). I had a bit of a go but ran into problems (installed but didn't seem to make a kernel module, but I didn't look to closely). There are also the [pre-compiled ones]("http://art.ubuntuforums.org/showthread.php?t=1468376") the t101mt people are using. Still not sure if egalax is actually compatible with the T91MT though.

I would be happy even with single touch, I had a go at using the [modified evtouch]("http://ubuntuforums.org/showpost.php?p=8566880") source that was used for 9.10 but it no longer compiles on 10.04 (even though the shipped evtouch package still the same version number as it was in 9.10, the Ubuntu build version number is a bit different though). I might have another go later at moving the T91MT code into the Ubuntu package. Although the bug list seems to indicate that there are problems with some bits of evtouch on 10.04. Also if I did get it compiling there is still no HAL, so that would have to be worked around (unless whatever bit is supposed to be creating input device nodes kicks in).

The device does seem to be listed in lsusb, its the 2nd one (the first is the bluetooth module I believe):
```
Bus 004 Device 003: ID 0b05:b703 ASUSTek Computer, Inc. 
Bus 004 Device 002: ID 0486:0185 ASUS Computers, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 005: ID 13d3:509b IMC Networks 
Bus 001 Device 002: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**EDIT1:** I dumped a bunch of printk messages into all the functions in hid-mosart.c, dpkg-reconfigured multitouch-kernel-source functions, verified they where in hid-mosart.ko via strings, insmod'd the module and none of them fired. So obviously the driver isn't loading for whatever reason. Maybe the hid.h hack is needed outside of hid.ko and the other multitouch-kernel-source bits. Will look at recompiling the kernel later, or dumping printk's into other hid areas to see why it's not loading.  Also enabled hid_dbg, nothing in /sys/kernel/debug/hid and no new dmesg information, other than a confirm that the debug mode was on.

/sys/bus/usb/devices/4-1/ seems to be the touchscreen entry (cat /sys/bus/usb/devices/4-1/product outputs MultiTouch and the idVendor/idProduct match). There is a /sys/bus/hid/drivers/mosart directory but doesn't have anything of interest. There is also /dev/bus/usb/004 but it doesn't out put anything useful with cat (without a driver I guess it wouldn't). 

Also /sys/kernel/debug/usb shows a rawish list of all the usb devices including the drivers (which is "(none)" for the MultiTouch entry reconfirming the lack of driver loading.

---

### Post by chavi on 2010-06-14
[URL="http://ubuntuforums.org/showthread.php?t=1468376&highlight=T101MT"]
[/URL]

---

### Post by kurtharriger on 2010-06-21
I also noticed that lshal did not report the input device that is assumed to exist in other guides for T91MT.  I managed to fix this by writing the vendor and product from lsusb to usbtouchscreen/new_id.  

```

modprobe usbtouchscreen
echo 0486 0185 > /sys/bus/usb/drivers/usbtouchscreen/new_id

```

After this /dev/input/event8 was created and was able to verify input from touchscreen using evtest /dev/input/event8. I'm not sure where the best place to put this, but for now I placed it in /etc/rc.local so that its created at startup.  

The driver doesn't compile for me either and I can't seem to get it to working properly in X yet.  It looks like you have made progress on that front so maybe this little bit plus your fixes will be all thats needed to get this working.

---

### Post by H3g3m0n on 2010-06-21
That made the dev entry for me and is providing output.

The cursor is actually responding in Xorg without any further tweaks, but it's extremely buggy. It's very off coordinate wise so calibration would be needed (the usbtouchscreen modules does seem to support some raw arguments if nothing else).  

The main problem is that it seems to lag very badly. The mouse button gets stuck as being held down. It doesn't seem to be an Xorg config problem as 'cat /dev/input/event8' only outputs occasional bursts of data. The usbtouchscreen does seem to have min_press, max_press and rept_size variables in the source code, but they don't seem to be module parameters so I'm not sure how to activate them right now.

It doesn't seem to be using the mosart drivers which I believe show up as some kind of hiddev nodes.

I had a go at echoing the ids to the hiddev, usbhid which didn't seem to do anything. Then when I tried /sys/bus/hid/drivers/mosart/new_id I got a "write error: Invalid argument.".

No entries showed up in the logs from my hid-mosart printk taps so nothing is calling the module.

---

### Post by warewolf on 2010-06-29
***UPDATE*** 
Success!

There's some work to get multitouch support working in Lucid, but it isn't quite there yet.  It's sort-of half there, and half not.  Because of this, the HID device that previously worked in Karmic is blacklisted from being attached to the hiddev driver.

Here's what I did to get my touchscreen working under Lucid:

(I will fill in details on this when I get home from work this evening, but here are the highlights)

1) Add chase douglas's PPA
2) Un-blacklist the T91MT's touchscreen from hiddev
3) Recompile (dpkg-reconfigure multitouch-kernel-source)
4) Add a hal FDI file for the touchscreen from the Karmic how-to
5) Add a multitouch quirk (0x40) to the module option for usbhid (otherwise the axis's get reported incorrectly)
6) modify /etc/rc.local to rmmod and modprobe the module (I think my initrd loads usbhid before modules.conf.d gets read)
7) add the udef rules in /etc/udev/rules.d from the Karmic how-to\
8)  Adjust the /etc/acpi/ rotate screen script to flip axises/invert stuff for screen rotation (thanks to Sarvatt!)

---

### Post by jtjs on 2010-07-10
So you're saying this was done intentionally? That would explain a lot.
Thank you for figuring this out, I have been watching these threads for quite a while with some disappointment.

PS: if people are searching the forum and looking at the last post date to see if there has been anything new, they won't know about an edited post.

---

### Post by jtjs on 2010-07-11
**Please follow the instructions given by H3g3m0n in the first post, they cover everything here and more.**

[I]This is what is needed to get the touch screen working:
1) as warewolf mentioned, install chase douglas's PPA and then install multitouch-kernel-source, this is a modified version of hiddev, easier to work with than the full ubuntu kernel sources.
sudo add-apt-repository ppa:chasedouglas/multitouch
sudo apt-get update
sudo apt-get install multitouch-kernel-source
2) edit /usr/src/multitouch-1.5/drivers/hid/hid-core.c to comment out line 1554.. That is where the touchscreen has been blacklisted.
3) edit /usr/src/multitouch-1.5/drivers/hid/usbhid/hid-quirks.c to add the multi-input quirk for the T91MT, refer to the line commented out in step 2, it has the necessary identifiers.
3)recompile the multitouch-kernel-source package: sudo dpkg-reconfigure multitouch-kernel-source
4) Restart, the screen should now work.

You can get right click emulation in gnome using the accessibility options.

If you need to calibrate your screen, the egalax calibrate package that Plippo made seems to work(my screen didn't need calibrating, so I can't confirm that, but it's output suggests it does work)

I tried Plippo's twofing daemon, edited the udev rule so that it would use the t91mt's touchscreen, it does see the screen, but doesn't seem to work, perhaps it is too egalax specific to work?

Thank you warewolf for figuring this one out.[/I]

---

### Post by H3g3m0n on 2010-07-11
Ok, it's working great for me here too.

No udev rules, hal fdi, /etc/modules or xorg.conf files are needed.

The only problem was that its line 1554 not 1556 as mentioned in jtjs's post.

1554 (correct device for me):
```
//{ HID_USB_DEVICE(USB_VENDOR_ID_ASUS, USB_DEVICE_ID_ASUS_T91MT)},
```

1556:
```
//{ HID_USB_DEVICE(USB_VENDOR_ID_ASUSTEK, USB_DEVICE_ID_ASUSTEK_LCM2)},
```

Was this just a typo or are we possibly dealing with 2 different models of touchscreen?

Also doesn't seem to be using the mosart module, but whatever works...

---

### Post by jtjs on 2010-07-11
it was a typo, I'll fix my post

---

### Post by H3g3m0n on 2010-07-12
The egalax calibrate from the T101MT thread seems to work fine for me.

The touchrotate script works too (although it helps if you change the 'auto' resolver to the Asus one so you don't have to specify the input id).

I've put step by step instructions on the original post and [http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt](http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt)

---

### Post by Ozone77 on 2010-07-13
Thanks everyone for your work on this, trying to get my touchscreen working on UNR 10.04 and after following the most recent instructions here am getting a response from the touch but it always puts the cursor in the top left corner.
Running the egalax calibration registers the first touch but after that it ignores input and times out.
Any ideas?

---

### Post by jtjs on 2010-07-13
> **Ozone77 said:**
> Thanks everyone for your work on this, trying to get my touchscreen working on UNR 10.04 and after following the most recent instructions here am getting a response from the touch but it always puts the cursor in the top left corner.
Running the egalax calibration registers the first touch but after that it ignores input and times out.
Any ideas?

It seems that you missed a step, you need to add the multitouch quirk:

Edit /usr/src/multitouch-1.5/drivers/hid/usbhid/hid-quirks.c
Add the following line after "} hid_blacklist[] = {"
```
{ USB_VENDOR_ID_ASUS, USB_DEVICE_ID_ASUS_T91MT, HID_QUIRK_MULTI_INPUT },
```

---

### Post by Ozone77 on 2010-07-14
> **jtjs said:**
> It seems that you missed a step, you need to add the multitouch quirk: ...

Ah, right you are. I made a typo in that line. Thanks!

---

### Post by jtjs on 2010-07-14
> **H3g3m0n said:**
> Ok, it's working great for me here too.

No udev rules, hal fdi, /etc/modules or xorg.conf files are needed.

The only problem was that its line 1554 not 1556 as mentioned in jtjs's post.

1554 (correct device for me):
```
//{ HID_USB_DEVICE(USB_VENDOR_ID_ASUS, USB_DEVICE_ID_ASUS_T91MT)},
```

1556:
```
//{ HID_USB_DEVICE(USB_VENDOR_ID_ASUSTEK, USB_DEVICE_ID_ASUSTEK_LCM2)},
```

Was this just a typo or are we possibly dealing with 2 different models of touchscreen?

Also doesn't seem to be using the mosart module, but whatever works...

hid-mosart doesn't get used, seems quite strange to me, you would think that this should be used?

Well, maybe it's a mistake? Looking through hid-core.c, the t91mt was added to the ignore list originally, that was done by Stephane Chatty, but that excludes the module from getting loaded at all...

There is another list in hid-core.c(about 200 lines above the ignore list), one for devices that do have a specialized driver. I added the entry for the t91mt to that list, now the hid-mosart module does get loaded(before usbhid, the driver that would be used by default. The touch screen continues to function as before, but presumably through the hid-mosart driver?

I am not familiar with hiddev though, so what I am doing is mostly guessing.

One note though, MyPaint now works, it didn't work for me before. (note, I have adjusted the pressure sensitivity mapping.. I only get one level of pressure)

H3g3m0n: do you have any thoughts?

Update:
I have also tried the above with the multi input quirk disabled.. It gives me just one touchscreen device instead of two, and the calibration is.. Odd.. The pointer doesn't sit in the top left corner anymore, but I wouldn't recommend using it.. atleast not until it can be calibrated, and without the multi input quirk enabled, that calibrate script does not work.

Update 2: I don't think calibration would work on this.. It definitely seems like dragging a mouse around the screen rather than using a touchscreen. It seems that the co-ordinates are all relative, nothing that relates to any specific spot on the screen. Perhaps this is why we're all waiting for xi2?

Update 3: Using the mypaint that is modified to work with resistive touch screens(from the t101mt thread), the pressure mapping seems to be taken from the x-axis.. it is really quite funny to use...

---

### Post by H3g3m0n on 2010-07-15
> **jtjs said:**
> hid-mosart doesn't get used, seems quite strange to me, you would think that this should be used?

Well, maybe it's a mistake? Looking through hid-core.c, the t91mt was added to the ignore list originally, that was done by Stephane Chatty, but that excludes the module from getting loaded at all...

There is another list in hid-core.c(about 200 lines above the ignore list), one for devices that do have a specialized driver. I added the entry for the t91mt to that list, now the hid-mosart module does get loaded(before usbhid, the driver that would be used by default. The touch screen continues to function as before, but presumably through the hid-mosart driver?

I am not familiar with hiddev though, so what I am doing is mostly guessing.

One note though, MyPaint now works, it didn't work for me before. (note, I have adjusted the pressure sensitivity mapping.. I only get one level of pressure)

H3g3m0n: do you have any thoughts?

Update:
I have also tried the above with the multi input quirk disabled.. It gives me just one touchscreen device instead of two, and the calibration is.. Odd.. The pointer doesn't sit in the top left corner anymore, but I wouldn't recommend using it.. atleast not until it can be calibrated, and without the multi input quirk enabled, that calibrate script does not work.

Update 2: I don't think calibration would work on this.. It definitely seems like dragging a mouse around the screen rather than using a touchscreen. It seems that the co-ordinates are all relative, nothing that relates to any specific spot on the screen. Perhaps this is why we're all waiting for xi2?

Update 3: Using the mypaint that is modified to work with resistive touch screens(from the t101mt thread), the pressure mapping seems to be taken from the x-axis.. it is really quite funny to use...

From what I can see the EGALAX touchscreen has the HID_QUIRK_MULTI_INPUT enabled so it should be the same for the mosart since they are both from ENAC.

Give GIMP a go, it has pressure sensitivity and allows you to specify which axis is used for the pressure. See how many axis are listed Not sure if it will allow multi-input though :/ I think you need to set the virtual X input thing to disabled first.
Edit>Prefrences>Input>Extended input

For me using the non-mosart drivers, Gimp lists 2 AsusTek, Inc. MultiTouch devices. The first has up to 8 numbers as choices for the input axis but doesn't seem to respond to any input. The second only has 2 number but seems to respond but it won't drag for me (it just moves the cursor to the position touched then doesn't do anything).

I also note that in /dev/input have event6, event7 and event8 all listed as Asus multitouch devices in lsinput (from the input-utils package). Although only the event7 responds to touchscreen events when 'cat'ing the output directly. It might be worth checking if you have the same number with mosart and if it outputs to any of the others.

Could be worth chmod 666ing the /dev/input/event* nodes to ensure there aren't any permissions problems. Not sure if these programs read from the directly or not.

Could do with finding some program capable to reading the input from the dev input/hid nodes directly to check for multitouch event input support. I do recall seeing one posted a while ago but have no idea where now.

Also worth trying twofing again and seeing if that works now.

As for the XI2, if its working with egalax, it should be working with masart as they are basically the same drivers. Not sure why calibration is screwed. Maybe it's combining multiple devices into 1 input, so your getting the result of both the single touch and the multitouch nodes. In that case we would just need to override with an xorg.conf.

If calibration is needed, it might be worth trying the manual xinput set-prop calibration.
[https://help.ubuntu.com/community/T101MT#TOUCH](https://help.ubuntu.com/community/T101MT#TOUCH) SCREEN

I'll have a go with the mosart drivers myself later (but it probably won't be until tomorrow now).

---

### Post by jtjs on 2010-07-15
I gave twofing a whirl again yesterday(Note: you have to modify the udev rule to use the device at "0185" rather than the device id that is already specified).

Once calibration has been done, it loads, it sees the different windows on the screen, but it doesn't seem to understand the output from the t91mt's screen.

If I have time I may look at the source and possibly add some more debugging output, that is unless the things I want to add are already there..

I also tried gimp, but no luck so far.

Another thing to note, the other two asus devices listed after the t91mt in hid-core.c, those were also added by Stephane Chatty at the same time as the t91mt was added.

Also, if you look at the source to the hid-mosart driver, it was originally set to call the multi input quirk.. It seems it didn't give the desired results, and only caused problems with xi2..

**Update:**
Looking through twofingemu.c.. it grabs the first device that it finds in the xinput list.. However, as it stands, with the mosart driver loaded, I have 3 devices showing up in the xinput list.. I think the egalax folks only have one showing up. This might be causing the issues, I'll look into it more tonight.

---

### Post by jtjs on 2010-07-15
Looking at hid-mosart.c.. it doesn't emit any details about the pressure of the touch, that would explain the lack of input for that. What is odd is that the x axis of the input is being mapped by programs which listen for the sensitivity..

---

### Post by thomi_ch on 2010-09-17
Hello..

Have done all steps.. the first time with previous Kernel it worked.. but now with 2.6.32-25 i can't really use the touchscreen of my T91MT with lucid 10.04.1. It's like mirrored and other strange thing. Have tried to calibrate it, but no way...

Any idea?

Thanks for response
thomi

---

### Post by H3g3m0n on 2010-09-19
It's been working fine for me with 10.04.1.

Maybe you need to play around with the Axis inversion stuff:
```
xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 0 0

```

Change the 0's at the end to 1's depending on which axis you wan't to invert.

Otherwise give it another go from scratch.

---

### Post by thomi_ch on 2010-09-19
Hey

Have found the problem.. i had 9.10 before,.. and there evtouch was used for the touchscreen of the T91MT... A fdi file was available and the xserver-sorg-input-evtouch was installed. Have removed the fdi file and uninstalled the evtouch driver and rebooted...

Now, the axis are correct, but the calibration not. On top of the screen calibration is better but on middle and bottom of the screen the cursor is out of calibration. Have tried to calibrate it, but without success.

How can i check, which driver is used? Which input dev is used?

And how to fix that calibration issue?

Thanks for feedback
thomi

---

### Post by Goldstorm on 2010-09-23
I tried installing this a while back on 9.10 with success. It was good for a while but it was pretty buggy and not very effective. Switched back to slow as syrup Windows 7 :c and stuck with it. Now that 10.10 MM is on it's way, do you think it's worth it to install it on the T91MT?

---

### Post by H3g3m0n on 2010-09-24
> **Goldstorm said:**
> Now that 10.10 MM is on it's way, do you think it's worth it to install it on the T91MT?

Not yet, right now the Intel Poulsbo GMA500 chipset only has kernel modules that work with 10.04 (and not that well). There's no 10.10 support and it might be a while (like how 10.04 took a while).

[http://ubuntuforums.org/showthread.php?t=1229345&page=201](http://ubuntuforums.org/showthread.php?t=1229345&page=201)

EDIT: Actually it seems there is some beta support but I'm not sure how good it is:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by frahez on 2010-09-25
hi friends,
actually i have a new lenovo c315. it has multitouch screen and woks fine on windows7. My problem is that on ubuntu 10.04 the multitouch don't work.

I've been try anything for 2 weeks and no soloution. Pleace help me 

thanks.

---

### Post by lucazade on 2010-09-26
> **H3g3m0n said:**
> Not yet, right now the Intel Poulsbo GMA500 chipset only has kernel modules that work with 10.04 (and not that well). There's no 10.10 support and it might be a while (like how 10.04 took a while).

[http://ubuntuforums.org/showthread.php?t=1229345&page=201](http://ubuntuforums.org/showthread.php?t=1229345&page=201)

EDIT: Actually it seems there is some beta support but I'm not sure how good it is:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

There is 10.10 support (both kernel modules and xorg drivers) and it work pretty good like in lucid.

---

### Post by frahez on 2010-09-27
hi friend, i'm sorry i did not understand your help. the informatios is confused there
i'm using amd athlon II microprocessor and right now i try to install ubuntu 10.04 x64 bits.

If you can be more specific will be great.

PS: I sorry for the language, i speak spanish :D

---

### Post by goseph on 2010-10-02
> **lucazade said:**
> There is 10.10 support (both kernel modules and xorg drivers) and it work pretty good like in lucid.

10.10 support you say? Does that mean that 10.10 on T91mt will "just work" or will I be able to make it work as if it were 10.04 or will I have to do crazy experiments and hackery?

---

### Post by Ozone77 on 2010-10-03
> **goseph said:**
> 10.10 support you say? Does that mean that 10.10 on T91mt will "just work" or will I be able to make it work as if it were 10.04 or will I have to do crazy experiments and hackery?

I've installed the 10.10 netbook beta candidate release, everything works nicely except the touch screen.
I had to install the poulsbo drivers from here:
[https://launchpad.net/~lucazade/+archive/poulsbo-maverick]("https://launchpad.net/%7Elucazade/+archive/poulsbo-maverick")
Which worked fine first go, including 3d support.

Can't find anything yet about the touch support in maverick for this machine, so at least in the candidate release it does not "just work", sadly.

---

### Post by Goldstorm on 2010-10-10
> **Ozone77 said:**
> I've installed the 10.10 netbook beta candidate release, everything works nicely except the touch screen.
I had to install the poulsbo drivers from here:
[https://launchpad.net/~lucazade/+archive/poulsbo-maverick]("https://launchpad.net/%7Elucazade/+archive/poulsbo-maverick")
Which worked fine first go, including 3d support.

Can't find anything yet about the touch support in maverick for this machine, so at least in the candidate release it does not "just work", sadly.

When it comes to Linux my experience is that nothing "just works" but it seems like very little work was needed. So I'll try this out later this week and post my results.

---

### Post by fiftynine on 2010-10-12
It would be a pleasure to ditch win7 from my t91mt.. so if someone could find out how to get the touchscreen working without freezing issues, it would be great.

---

### Post by yatt on 2010-10-14
Since some people have mentioned Maverick, I have made a Maverick specific guide here:

[http://ubuntuforums.org/showthread.php?t=1595220](http://ubuntuforums.org/showthread.php?t=1595220)

---

### Post by kathleenhenri on 2010-10-16
> **yatt said:**
> Since some people have mentioned Maverick, I have made a Maverick specific guide here:

[http://ubuntuforums.org/showthread.php?t=1595220](http://ubuntuforums.org/showthread.php?t=1595220)


Hey, Thanks for posting your guide - but I was not able to compile the kernel. The 2 files in your instructions that are to be modified before the kernel is compiled are missing. Is something missing from the instructions?

---

### Post by H3g3m0n on 2010-10-16
I have attached a multitouch-kernel-source package, modified for maverick, to the first post (it also includes the hid-core.c and hid-quirks.c changes.).

Maverick users should just install the attached package and ignore most of the instructions except for the rotate button fix.

Not sure about calibration at this stage.

---

### Post by Hoochster on 2010-10-17
Appreciate your help on the sources.  But for Maverick, it doesn't look like you have created the sources for the actual Maverick dist in ppa.  Lucid is there but not Maverick heh.

Scratch that, now that I actually READ what you posted about downloading the attached package.  Sorry.  And thanks again.

---

### Post by Goldstorm on 2010-10-22
Installed and working ok. Still need to get the multi touch to work. But whenever I switch to portrait mode, the input doesnt change.

---

### Post by milanp on 2010-10-27
Does anybody have flawless video playback without any glitches on 10.10 with T91MT ?
Everything else worked for me, but I cannot get decent video playback on 10.10 or 10.04...

---

### Post by H3g3m0n on 2010-12-08
> **milanp said:**
> Does anybody have flawless video playback without any glitches on 10.10 with T91MT ?
Everything else worked for me, but I cannot get decent video playback on 10.10 or 10.04...

I have no major issues with video on 10.04 providing I use the vaapi version of mplayer. It is a bit of a pain to setup initially but there is a script. I couldn't get 10.10 to playback the same way without some major glitches (seemed to be a T91MT specific problem).

There are now working EMGD drivers that are somewhat better than the PSB ones (although not the Gallium3D ones we have all been hoping for). They support normal XV playback. They also support Compiz (but still no Unity).

Also for anyone subscribed to this thread, there are now proper mosart multitouch DKMS drivers in a utouch PPA, see first post. Of course there isn't much that works with multitouch right now...

---

### Post by kathleenhenri on 2010-12-10
I finally tried Maverick again - and now with the new touch and graphics drivers my t91mt is running quite well. So far, no random freeze ups and it is nice to have compiz and video playback.

The only thing not working is screen rotation and the silver rotate button, but I can happily let them go. Although I often use tablet mode, I don't need to rotate the screen for that.

Good job!

---

### Post by H3g3m0n on 2010-12-10
> **kathleenhenri said:**
> I finally tried Maverick again - and now with the new touch and graphics drivers my t91mt is running quite well. So far, no random freeze ups and it is nice to have compiz and video playback.

The only thing not working is screen rotation and the silver rotate button, but I can happily let them go. Although I often use tablet mode, I don't need to rotate the screen for that.

Good job!

Apparently adding 'xhost :local' to a login script or something similar ('xhost localhost' what what I used to use ages ago for something similar) can help fix the screen rotation. Also I think you have to remove a stray ; (or some other character) from a script script that is called by the rotate script. I might have a proper go at switching from Lucid to Maverik now most of the problems have been fixed, and write up something.

My main concern is that the EMGD drivers pull in an experimental version of Xorg which could cause problems in the long run with future Ubuntu upgrades and so forth but Natty isn't too far off anyway (which will be *another* problem since Unity doesn't work with either EMGD or PSB drivers, but I'm already using the 2D-EFL version of the old netbook-launcher so it's not such a major issue for me personally.).

---

### Post by razzac11 on 2010-12-15
Hi I am confused on how to edit the kernel ? it says permission denied when i save it. is there a specific place to edit the text? please help?

---

### Post by H3g3m0n on 2010-12-15
> **razzac11 said:**
> Hi I am confused on how to edit the kernel ? it says permission denied when i save it. is there a specific place to edit the text? please help?

You need root level access. Try typing 'gksudo gedit /thepath/thefiletoedit'

---

### Post by razzac11 on 2010-12-16
wow thanks, that helped! :p

---

### Post by davidea on 2010-12-25
hi!
i've a cando 10.1 touchscreen with usbid 2087:0a02
i've managed your multitouch-kernel-source-maverick.tar.gz to make it working.
after the installation i've modified the file

/usr/src/multitouch-1.555/drivers/hid/hid-ids.h

to use my usbid

the line 131 from

```
#define USB_DEVICE_ID_CANDO_MULTI_TOUCH 0x0a01

```
to

```
#define USB_DEVICE_ID_CANDO_MULTI_TOUCH 0x0a02
```

and now it's like a sharm!!!!
may we add a second line instead to modify this?

after this patch, i've recompiled all with

```
sudo dpkg-reconfigure multitouch-kernel-source
```

where this file came from?
may we add this usbid for the other people?

---

### Post by christophermluna on 2011-02-07
I've installed multitouch via the PPA, and this was at the beginning of a clean install, mostly following the guide you posted on the eeePC Wiki, but I don't think I've got multitouch support.  I tried to install the multitouch daemon, but it won't work, and I've used evtest to try to see if the screen is reading two fingers with no luck.

Is there something I can do to test to see if the multitouch is working?  For example, is there some way to just activate two-finger scrolling on the screen, or even just something I could do from the command line to make sure it's working?

---

### Post by H3g3m0n on 2011-02-08
> **christophermluna said:**
> I've installed multitouch via the PPA, and this was at the beginning of a clean install, mostly following the guide you posted on the eeePC Wiki, but I don't think I've got multitouch support.  I tried to install the multitouch daemon, but it won't work, and I've used evtest to try to see if the screen is reading two fingers with no luck.

Is there something I can do to test to see if the multitouch is working?  For example, is there some way to just activate two-finger scrolling on the screen, or even just something I could do from the command line to make sure it's working?

I don't think evtest sorts out the fingers.

Try installing mtdev-tools.

There is 'gesturetest 0 0 0xffffffff'. Which should let you detect pinch's and such.

Also 'sudo mtdev-test /dev/input/event4'. 1 finger should have a id of 00 and with 2 fingers you should get both 00 and 01.

There are a bunch of tools on:
[https://wiki.ubuntu.com/Multitouch/](https://wiki.ubuntu.com/Multitouch/)

I tried GUI testing tools (mtview and ucube) without success. ucube didn't work on the crappy GMA500, mtview 1.1.1 and 1.1.0 both required a newer version of mtdev than was in mavericks repos.

To get multitouch scrolling and zoom you probably want to look at installing ginn. Personally I have found it simpler to just use singletouch gestures with something like easystroke bound to pagedown

---

### Post by jtjs on 2011-02-08
twofing should work, so long as you edit the rules file to point it at the correct device, since twofing was written with the t101mt in mind. There should be another post regarding 10.10 and twofing on the t91mt if you do a search.

---

### Post by christophermluna on 2011-02-08
@H3g3m0n
Thanks for the reply.  I'll check out the stuff you've posted.  I have been using single-touch gestures with mutlitouch since I bought the T91MT, but when I saw on this thread that someone said they got multitouch working I thought I would try it out and see how difficult it would be to accomplish.

@jtjs
Yeah, I edited the rule and compiled, but nothing seemed to happen.  I was following another post where someone else had the same problem, and on that post it turned out that there were no multitouch events being registered, so I though that the problem might have been with the my installation of the driver itself and wondered if there was a better way to test the driver itself.

---

