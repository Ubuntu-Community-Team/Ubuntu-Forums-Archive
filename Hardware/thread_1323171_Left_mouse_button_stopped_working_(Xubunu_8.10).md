---
title: "Left mouse button stopped working (Xubunu 8.10)"
date: 2009-11-11
forum: Hardware
---

### Post by TimKraemer on 2009-11-11
Hi @ all,

The left mousebutton of my touchpad (Samsung R50 Laptop, Xubuntu 8.10) stopped working. It simply does not react to any clicks. The movement of the cursor and right button are not affected. 

I can't recall to have changed anything in the configuration of my system recently. Thus, I assumed that it is simply broken physically (my laptop is rather old). I've been using a Logitech USB mouse as a replacement for the last couple of weeks. But sometimes the left mouse button on my USB mouse stops working too.

Just for a test I tried to change my settings from right-handed mouse to left-handed mouse. As a consequence the right mouse button stopped working and the left one was OK (on the touchpad as well as on my USB mouse). So it can't really be a hardware problem.

I looked forward to Ubuntu 9.10, and hoped that this would solve the matter, but the problem remains. When I boot Ubuntu 9.10 from CD, it's exactly the same problem. On my Touchpad as well as USB mouse the left mouse button does not work. As I really want to upgrade to 9.10, I want to find a solution for this annoying problem. 

I already looked into my xorg.conf file but the sections for input devices are commented out. And it says that HAL is now used for input devices (I used 7.10  before and updated the system to 8.10). I assume the problem lies in somewhere HAL. I read that HAL config files can be found in /etc/hal/fdi/policy , but there are only two files (preferences.fdi,shmconfig.fdi) which do not mention any input devices.

I'm a bit helpless where to start looking for a solution. 

Does anyone have a hint where to start? Logfiles, config files, anything?


All the best,

Tim

Edit: If it helps, a "grep -B 5 mouse /proc/bus/input/devices" turns out the following devices:
> I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
--
I: Bus=0003 Vendor=046d Product=c51b Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
--
I: Bus=0011 Vendor=0002 Product=0007 Version=25b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse2 event10 

Can it be that the first entry somehow causes the problems?

---

### Post by TimKraemer on 2009-11-11
I've solved the Problem.

My first guess was right: I assumed that the first of the three devices ("Macintosh mouse button emulation") was somehow responsible for depriving me of my mouse buttons. "Macintosh mouse button emulation" probably means that you only have one button.

The solution was to tell HAL to ignore that device (who needs a macintosh emulation anyway???). Simply create a file like 10-blacklist.fdi in the directory /etc/hal/fdi/preprobe. In this file you post

> <?xml version="1.0" encoding="UTF-8"?>

<!--  15/12/2008 by BJ  
    *Match* devices you want to blacklist and *merge* info.ignore to true
       Get the necessary info to match with hal-device    
-->

<deviceinfo version="0.2">
    <device>
        <match key="info.category" contains="input">
            <match key="input.product" contains="Macintosh">
                <merge key="info.ignore" type="bool">true</merge>
            </match>
        </match>
    </device>
</deviceinfo>

That piece of code tell HAL to ignore all input devices that have "Macintosh" in the identifying string.

Credit goes to:
[http://bbs.archlinux.org/viewtopic.php?id=60986](http://bbs.archlinux.org/viewtopic.php?id=60986)

---

### Post by bluezeak on 2010-04-30
As far as I can tell, you saved my left mouse button - thank you :).

---

### Post by da_buddar on 2010-07-21
I have a acer aspire 5100 running the latest unbuntu (32bit) i recently installed the requested files by update manager. While this was installing my touch pad refused to work, selecting everything and only being able to move the cursor and press the right button. 

 installed a USB mouse and that didn't work first time, now it seems to work but only the left button...so i have to use the combination.

This only happened after the lastest updates through update manager.

How do I roll back the update or how do i keep the updates and make things work.

Please bare in mind that i'm very new to linux and will need the same level of assistance as a grandmother

---

