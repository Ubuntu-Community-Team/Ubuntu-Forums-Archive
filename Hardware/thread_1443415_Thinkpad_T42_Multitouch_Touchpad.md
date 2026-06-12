---
title: "Thinkpad T42 Multitouch Touchpad"
date: 2010-03-31
forum: Hardware
---

### Post by hurdevan on 2010-03-31
I came across [_this_]("http://www.ibm.com/developerworks/opensource/library/os-touchpad/#resources") article about multitouch for Touchpad Devices and I though that was pretty cool. The site provides a [_list_]("http://web.telia.com/~u89404340/touchpad/compatibility.txt") of hardware compatible computers and mine, IBM Thinkpad T42,just happened to there. 

I was wandering if anybody else has been successful in doing what the article talks about and if so, then how?

The article uses the program synclient allot and I know other people have had issues getting this to work easily; however, I have had an issue that that is the same and yet different.

I am trying to get the option -m for synclient(synclient -m 100)to work properly and I get that common error.
```
Can't access shared memory area. SHMConfig disabled?
```
Everything else works just dandy; but, that one option just gives me the hee-bee-jeebies. 

I have tried to configure my Xorg to:
```
Section "Device"
    Identifier     "Configured Video Device"
    Option         "AccelMethod" "UXA"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    InputDevice    "Synaptics" "SendCoreEvents"
EndSection

Section "InputDevice"
Identifier "Synaptics"
Driver "synaptics"
Option "SHMConfig" "on"

``` 

I have also added the following line the my fstab file without wonderful success.
```
tmpfs /dev/shm tmpfs defaults 0 0
```

Everything else works just dandy except when it comes to 'synclient -m 100'. If there is anybody else who is willing to enlighten me of my hee-bee-jeebies then PLEASE step forward.

Thanks


Artlical:
[http://www.ibm.com/developerworks/opensource/library/os-touchpad/#resources](http://www.ibm.com/developerworks/opensource/library/os-touchpad/#resources)
Hardware list:
[http://web.telia.com/~u89404340/touchpad/compatibility.txt](http://web.telia.com/~u89404340/touchpad/compatibility.txt)

---

### Post by hurdevan on 2010-03-31
*BUMP*

How does one go about enabling SHMConfig for Ubuntu 10.04?

I have heard of editing the Xorg file and adding to the fstab file. I Also heard that you don't need to do those things for the latest Ubunut version but just create a file here "/etc/hal/fdi/policy" and put this in it:

fix-finger.fdi:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.touchpad">
<merge key="input.x11_driver" type="string">synaptics</merge>
<merge key="input.x11_options.SHMConfig" type="string">true</merge>
<merge key="input.x11_options.FingerLow" type="string">40</merge>
<merge key="input.x11_options.FingerHigh" type="string">50</merge>
</match>
</device>
</deviceinfo>
```

Alas nothing has rendered the desired results. Surely someone out there is running 10.04 and was smart enough to fix this problem?

Anybody? 

Also I'm not sure to look for errors. I check the log viewer and did not get any results looking for "SHMConfig" or "synaptics". Not sure if thats a good thing or bad thing?

---

### Post by dmarinov on 2010-08-06
Did you figure this out? I just got a thikpad t410 yesterday, and I'm running into the same issue. I'd appreciate it if you could post how you were able to work around it.

---

### Post by hurdevan on 2010-08-06
No I did not.

To sum it up there should be away to do this because it works in ubuntu 8.04. Once upon a time, the drivers were started from Xorg but that is no the case and since then it has not worked. I guess there were not enough people who cared to fix it.

I hope that it will be fixed on of these days because I can't figure out how to do it.

---

