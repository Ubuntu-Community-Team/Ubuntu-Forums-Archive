---
title: "USB FM reciever cant load please help"
date: 2008-08-04
forum: Hardware
---

### Post by dragonneus on 2008-08-04
I am using Ubuntu 8.04 on an asus eee 701 4g laptop. The adapter is a PCear usb FM reciever. 

this is the dmesg output when plugging in

[196297.355596] usb 1-2: new full speed USB device using ohci_hcd and address 4
[196297.567794] usb 1-2: configuration #1 chosen from 1 choice
[196298.522146] usbcore: registered new interface driver hiddev
[196298.551432] hiddev96hidraw0: USB HID v1.11 Device [[www.rding.cn](www.rding.cn) RDing PCear FM Radio] on usb-0000:02:0e.0-2
[196298.551466] usbcore: registered new interface driver usbhid
[196298.551472] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[196298.587738] usbcore: registered new interface driver snd-usb-audio
[196956.547477] gnome-video-thu[21851]: segfault at 00000000 eip b720e9b5 esp b4c7edfc error 6
[198017.364060] usb 1-2: USB disconnect, address 4
[198027.302083] usb 1-2: new full speed USB device using ohci_hcd and address 5
[198027.514282] usb 1-2: configuration #1 chosen from 1 choice
[198027.565161] hiddev96hidraw0: USB HID v1.11 Device [[www.rding.cn](www.rding.cn) RDing PCear FM Radio] on usb-0000:02:0e.0-2

I don't see any available /dev/audio/dev/audio or /dev/audio0.

This works fine in windows but cant get it to work with Ubuntu with gnomeradio (ive tried gradio and a few others also) I just get an error message "cant find /dev/audio" or somthing similar. 

Any help would be greatly appreciated.

NOTE* I tried to use the pcear software with wine doesnt seem to work , I get a GUI but cant activate any of the controls.

---

### Post by rogerdean on 2008-09-19
hi there, did you manage to get this going? am thinking of buying...
cheers

---

### Post by mlord on 2008-12-01
I've got one of those exact $10 dongles here from DealExtreme.

I can play the audio with a simple "cat /dev/dsp1 > /dev/dsp", but no controls.

The USB ID looks suspiciously similar to the Silicon Labs one that is at the top of linux/drivers/media/radio/radio-si470x.c:

        /* Silicon Labs USB FM Radio Reference Design */
        { USB_DEVICE_AND_INTERFACE_INFO(0x10c4, 0x818a, USB_CLASS_HID, 0, 0) },

So I hacked in an extra line like this one:

        { USB_DEVICE_AND_INTERFACE_INFO(0x10c5, 0x819a, USB_CLASS_HID, 0, 0) },

And added a symlink in /dev/:  ln -s hidraw0 radio

Now various radio applets will start up (eg. gradio), but still no control over anything.

It's probably not far off from working, though.  Just needs some TLC.

---

### Post by mlord on 2008-12-01
Mmm.. the tuner chip is definitely an Si4701 -- I can read the markings on it with some alcohol and a magnifier.  Dunno about the USB/sound chip thoug -- they scuffed that one up really well.

---

### Post by mlord on 2008-12-01
Okay, it works!!

A couple of steps necessary to get it going.  First, patch the USBID into the driver as described above.

Then, do this:

rmmod usbhid ; modprobe radio-si470x band=0 space=0 de=0 ; modprobe usbhid

Now you can play the radio sound with this:

arecord -D hw:1,0 -r96000 -c2 -f S16_LE | artsdsp aplay -B -

And control the tuner/volume with gradio  (sudo apt-get install gradio)

-ml
modprobe

---

### Post by dragonneus on 2010-02-03
I know this post is old but I cant find that driver only the.ko of it. Im not sure exactly sure where to find or how to load the above driver pls help.

---

### Post by tsak_gr on 2010-02-07
You must install the source first

sudo apt-get install linux-source

---

