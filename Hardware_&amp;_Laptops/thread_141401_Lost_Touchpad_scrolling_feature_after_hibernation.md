---
title: "Lost Touchpad scrolling feature after hibernation ?"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by Commuto on 2006-03-08
I'm a several years user of Debian, 2 days user of Ubuntu, discovering a new system and its... particularities :neutral:.

I'm running Ubuntu 5.10 . I struggled a bit get my touchpad fully running. By fully I mean especially the "page scrolling" feature. Eventually I was successful by manually replacing the usr/X11R6/lib/modules/input/synaptics_drv.o driver with a more recent one. Not so elegant but actually it worked :oops: (additional details [here](http://ubuntuforums.org/showpost.php?p=411672&postcount=9))

OK, everything is working, no what ? :mrgreen: 
Well, it isn't ! I lose the page scrolling feature everytime the laptop comes back from hibernation. Problem is I'm totally addicted to this way of using it :cry:.

Appart from that the hibernation seems to be running fine...
I nocited a "strange" line when the problem occur:
In  /var/log/Xorg.0.log :
```
(II) Synaptics touchpad driver version 0.14.0
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
**(--) Synaptics Touchpad touchpad found**
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Synaptics DeviceOff called
**(WW) Open APM failed (/dev/apm_bios) (No such file or directory)**
Synaptics DeviceOn called
**(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device**
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```
Notice X seems to find the touchpad correctly, then for an unknown reason mess with the APM and goes dark.
Laptop is a Toshiba 5105-S501. ACPI is overall very well supported.

Any clue? :-k

---

### Post by underwater on 2006-03-08
I had this problem too, but unless you are plugging in a mouse somewhere I don't know how to solve yours.

I noticed that my touchpad's scrolling would not resume if I plugged in a USB mouse either before the machine was fully booted or if I have it plugged in when I hibernate.

---

### Post by Commuto on 2006-03-08
:oops: I barely use a mouse on this laptop... :KS

---

### Post by Commuto on 2006-03-08
OK, I managed to find a USB mouse. I was able to plug it to the laptop at it worked flawlessly. Scrollwheel too :cry:, whereas no page scrolling through the touchpad :-? . Weird

---

### Post by Commuto on 2006-03-11
...bug is still here, coping with all my tries to make it understand IT WON'T HAVE THE LAST WORD! :mad: :o :mrgreen:

---

### Post by firecat53 on 2006-03-12
Try checking that the module evdev is installed. 

```
lsmod |grep evdev
```
Then if not, try 

```
sudo modprobe evdev

```
Then you can add it to your /etc/modules list or to the resume script if it doesn't come back each time.

Good luck!  Scott

---

### Post by Commuto on 2006-03-13
Thank you for your input.
evdev is indeed loaded upon cold boot:
```
me@Domain:~$ lsmod | grep evd
evdev                   9664  1

```I had the laptop hibernate and resume. As "expected" I lost the scrolling feature :neutral:,  whereas the evdev module is still listed :evil::
```
me@Domain:~$ lsmod | grep evdev
evdev                   9664  1

```I'm still a bit dubious about the "***(WW) Open APM failed (/dev/apm_bios) (No such file or directory)***" line in the /var/log/Xorg.0.log file.
As far as I know I use acpi, why does apm show up here? :???:
...Any way to prevent apm to be called upon resume?

---

### Post by Commuto on 2006-03-14
'K.... did a few more searches around to understand that this "Open APM Failed" warning is probably not an important issue:
[http://wiki.x.org/wiki/FAQWarningMessages](http://wiki.x.org/wiki/FAQWarningMessages)

Still, here is a screenshot of a diff between a "good" X start and a "bad" X start (I mean, one *with* the scrolling touchpad success and one *without* the scrolling failure).
Here :
[IMG]http://img164.imageshack.us/img164/1733/screenshot5lt.png[/IMG]

Notice the "few more lines" struggling with DeviceOff/DeviceOn for no particular reason... I just wish it kept on a classical start and stop trying the mess :D

---

