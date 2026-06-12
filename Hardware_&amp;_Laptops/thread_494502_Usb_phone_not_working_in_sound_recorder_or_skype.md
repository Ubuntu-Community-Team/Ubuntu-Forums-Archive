---
title: "Usb phone not working in sound recorder or skype"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by bsawler on 2007-07-07
Hi all, 

I have a hp dv2000 laptop running feisty.  I previously installed feisty  and could not get my sound (intel) to work but my usb phone worked with skype (i.e. I could selection the Generic USB from the skype options).  Got frustrated, reformatted and reinstalled feisty and got my sound to work following this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Now, I plugged in the usb phone and I do not have the choice to select the Generic USB device anymore in skype or sound recorder.  

So unplugged the phone and then plug it back in and ran "dmesg" with the following:
```
[ 7751.200000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 7751.356000] usb 3-1: configuration #1 chosen from 1 choice
[ 7751.364000] input: Generic USB Audio Device    as /class/input/input8
[ 7751.364000] input: USB HID v1.00 Device [Generic USB Audio Device   ] on usb-0000:00:1d.1-1
[ 7751.476000] usbcore: registered new interface driver xpad
[ 7751.476000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[ 7802.116000] usb 3-1: USB disconnect, address 3
[ 8092.660000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 8092.812000] usb 3-1: configuration #1 chosen from 1 choice
[ 8092.820000] input: Generic USB Audio Device    as /class/input/input9
[ 8092.820000] input: USB HID v1.00 Device [Generic USB Audio Device   ] on usb-0000:00:1d.1-1
```

Then I removed the usb and ran "dmesg" again:
```
[ 8151.388000] usb 3-1: USB disconnect, address 4
```

As a newbie, it appears that it is finding the usb, but why can I not the option to select this? 

I plug this same phone into my desktop (feisty) and it works fine, so it is not drivers etc. 

Thanks in advance.
Bradley

---

### Post by bsawler on 2007-07-12
Bump!!!

I have been looking everywhere, but cannot find anything close.  This is not a good sign, cause this is ultimately the most important thing for me. 

On a default installation, I get no sound out of the speakers.  When I plug in the usb phone, it works.  But without sound, I cannot hear the phone ring! 

So I played around and get the sound working, and since the sound is working, when I plug in the usb phone, I do not get an option to select the Generic USB Phone anywheres, so now I cannot use Skype, which is the most important thing, cause everything else is working (sort of'ish). 

Any input would be great. 

Thanks,

---

