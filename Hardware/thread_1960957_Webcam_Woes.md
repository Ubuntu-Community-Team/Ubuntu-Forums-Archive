---
title: "Webcam Woes"
date: 2012-04-18
forum: Hardware
---

### Post by OutlandishKnight on 2012-04-18
I just bought a new webcam. It was unbranded and very cheap, but excellent build quality, decent specs, and the design just looks awesome so for the price I thought I'd try it. 

I've pretty much established now that it *should* be compatible with Ubuntu using the uvcvideo driver. I personally, though, just can't get it to work.

I'm on 12.04 Beta 2 64 bit. The webcam itself has turned out to be a Genesys Logic one, and as I say should work with the uvcvideo driver (which of course I've activated). There are two problems which may or may not have the same cause:

1. The webcam simply not working. The lsusb command detects it fine, as does hwinfo. I have, of course, activated the driver, but still every program I tries gives either a black screen or a message saying that no camera has been found.

2. When I try to use it with a program, my wireless disconnects and won't reconnect until reboot. May sound odd, but Googling has revealed that others have had the same problem, especially those with Toshiba laptops (mine is Toshiba too). Sadly, I didn't find a solution among those results.

Any help, with either problem, would be much appreciated.

---

### Post by samigina on 2012-04-18
Hi, Please copy/paste the lsusb output so we can see the webcam chip.

---

### Post by OutlandishKnight on 2012-04-18
Hi, thanks muchly for your reply. The output is as follows, but to my admittedly inexpert eyes I'm afraid the relevant line doesn't look very informative:

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 005: ID 05e3:0512 Genesys Logic, Inc. 

---

### Post by OutlandishKnight on 2012-04-18
In case it's any more use, here's what hwinfo has to say on the matter too:

> 13: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: ADDn.r07n5zHkQVA
  Parent ID: k4bc.MrJLBLcWB9F
  SysFS ID: /devices/pci0000:00/0000:00:13.5/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: unknown
  Model: "Genesys Logic U2 EE Cam"
  Hotplug: USB
  Vendor: usb 0x05e3 "Genesys Logic, Inc."
  Device: usb 0x0512 "U2 EE Cam"
  Revision: "12.14"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Device File: /dev/input/event10
  Device Files: /dev/input/event10, /dev/input/by-id/usb-05e3_U2_EE_Cam-event-if00, /dev/input/by-path/pci-0000:00:13.5-usb-0:1:1.0-event
  Device Number: char 13:74
  Speed: 480 Mbps
  Module Alias: "usb:v05E3p0512d1214dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #4 (Hub)

---

### Post by samigina on 2012-04-18
Lets try something. You already said that you activated the driver, how did you do it?

The driver is there but it seems like is not loaded.

Type "sudo modprobe uvcvideo" in a terminal, and then "ls /dev/video*" and please paste the output.

Wich program are you using to test your webcam?

---

### Post by OutlandishKnight on 2012-04-18
Activated by typing that same command. Done it again in case, and the output is "/dev/video0"

---

### Post by samigina on 2012-04-18
What software are you using to test the camera?

Try launching the software from a terminal, You can try Cheese or Guvcview. That way we can see whats happening.

---

### Post by OutlandishKnight on 2012-04-18
Had tried a range of programs, though not Guvcview until your suggestion. Pretty much installed everything half decent I found in the Ubuntu software centre. Programs I've tested and the results are as follows (launching from terminal seems to make no difference):

Cheese: No camera detected. Wi-fi connection lost as soon as software starts, and will not reconnect until reboot.

Guvcview: Exactly the same results as Cheese.

Camorama: Refuses to open. Says it quit unexpectedly before a window actually appears. Tried opening without webcam connected just to see if there any difference, and there is. Instead of quitting unexpectedly, it refuses to open on grounds there no camera, so since it doesn't do that when it is connected I'm guessing it detects it in some form.

Kamoso: No camera detected. Wi-fi connection lost a couple of minutes after software first opens.

---

### Post by samigina on 2012-04-18
Launch them from a terminal to get the logs.

Meanwhile try starting gstreamer-properties and changing the value V4L2 to V4L in the video tab.

Edit:
I havent seen you already launched the software from a terminal, but you didnt get any messages?

---

### Post by OutlandishKnight on 2012-04-18
Thank you good sir!

The solution turned out to be surprisingly simple if only I'd known where to look. I went to the gstreamer-properties as you suggested, but v4l didn't seem to be an option. However, I fiddled around a bit more and discovered that "Device" was set to "Default," while my webcam was the other available option. Changed that, did the test. Webcam worked perfectly, so opened Cheese. Webcam still worked perfectly, and no loss of wireless connection. All seems to be fine.

EDIT: Or not (see next post).

---

### Post by samigina on 2012-04-18
Nice!

Just remember to mark the post "solved".

---

### Post by OutlandishKnight on 2012-04-18
And I've just discovered why I should double check before marking a thread as solved. Definitely a lot closer, thanks to your kind help, but I'm not quite there after all. 

If I open a software that uses the webcam once, it works fine. If I close it then reopen it stops. It once again shuts down the wireless connection, and it's no wonder if fails to detect the webcam because it also shuts down all the USB ports! They still get power, but no communication. The only thing that still works is my mouse, and that stops if I unplug it and plug back in. The same thing happens if I open gstreamer-properties now, even without opening any webcam software first.

So now I have a usable webcam, which is great progress on before, but need to reboot between every use.

---

### Post by samigina on 2012-04-18
Are you using a laptop or a desktop? It seems like a power problem, like your usb hub cant feed all the ports (Wireles and Webcam, both need a los of energy).

---

### Post by OutlandishKnight on 2012-04-18
Laptop, but plugged in.

---

### Post by samigina on 2012-04-18
Definitely a power problem. Try different ports.

Someone with the same problem, solved with a external hub:

[http://ubuntuforums.org/showthread.php?t=1846570&page=2]("http://ubuntuforums.org/showthread.php?t=1846570&page=2")

---

### Post by samigina on 2012-04-18
Someone in [this ]("http://ubuntuforums.org/showthread.php?t=1479524")post (the same problem) solved with a workaround:

> Afterwards you just need to reboot, disable the wireless by right clicking on the wireless icon and uncheck "Enable wireless". Once your wireless is manually disabled, then you can use Cheese and or gucview. With Cheese or gucview open, then you can enable your wireless. This way you will endup with a wireless connection and be able to use your camera.

---

### Post by OutlandishKnight on 2012-04-18
I owe you my thanks again. After the last time I thought it was solved, I won't mark the thread solved until I've tried everything out more thoroughly, but it really seems promising. I can open webcam applications multiple times using the workaround with no problems.

---

