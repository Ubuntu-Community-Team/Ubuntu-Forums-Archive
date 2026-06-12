---
title: "PS/2 to USB Converter: problems with connecting"
date: 2012-01-29
forum: Hardware
---

### Post by the pearly gates on 2012-01-29
Hi,

I have a favorite keyboard, but it only takes PS/2 connection, which my desktop computer has none.  Not wanting to give up my favorite keyboard, I bought this *adapter*, (which is different from a converter, apparently):

[http://www.amazon.com/USB-to-PS-2-Adapter/dp/B00007AP2O/ref=sr_1_2?ie=UTF8&qid=1327884967&sr=8-2](http://www.amazon.com/USB-to-PS-2-Adapter/dp/B00007AP2O/ref=sr_1_2?ie=UTF8&qid=1327884967&sr=8-2)

Now, when I just plug in the adapter into the USB (with the keyboard disconnected to the adapter), I get inconsistent results from my /var/log/syslog.  Maybe once out of every 10 tries it'll connect successfully.

Here's the output of an unsuccessful connect:

```
Jan 29 18:54:30 duly-desktop kernel: [10065.190051] usb 5-1: new low speed USB device using ohci_hcd and address 61
Jan 29 18:54:30 duly-desktop kernel: [10065.380144] usb 5-1: unable to read config index 0 descriptor/all
Jan 29 18:54:30 duly-desktop kernel: [10065.380155] usb 5-1: can't read configurations, error -62
Jan 29 18:54:32 duly-desktop kernel: [10066.980080] usb 5-1: new low speed USB device using ohci_hcd and address 62
Jan 29 18:54:32 duly-desktop kernel: [10067.130076] usb 5-1: device descriptor read/64, error -62
Jan 29 18:54:32 duly-desktop kernel: [10067.390070] usb 5-1: device descriptor read/64, error -62
Jan 29 18:54:33 duly-desktop kernel: [10067.670069] usb 5-1: new low speed USB device using ohci_hcd and address 63
Jan 29 18:54:33 duly-desktop kernel: [10068.090079] usb 5-1: device not accepting address 63, error -62
Jan 29 18:54:33 duly-desktop kernel: [10068.260083] usb 5-1: new low speed USB device using ohci_hcd and address 64
Jan 29 18:54:34 duly-desktop kernel: [10068.680062] usb 5-1: device not accepting address 64, error -62
Jan 29 18:54:34 duly-desktop kernel: [10068.680090] hub 5-0:1.0: unable to enumerate USB device on port 1
```

And here's one of a successful connect:

```
Jan 29 18:46:49 duly-desktop kernel: [ 9604.380054] usb 5-1: device descriptor read/64, error -62
Jan 29 18:46:50 duly-desktop kernel: [ 9604.660080] usb 5-1: new low speed USB device using ohci_hcd and address 14
Jan 29 18:46:50 duly-desktop kernel: [ 9605.080058] usb 5-1: device not accepting address 14, error -62
Jan 29 18:46:50 duly-desktop kernel: [ 9605.250111] usb 5-1: new low speed USB device using ohci_hcd and address 15
Jan 29 18:46:51 duly-desktop kernel: [ 9605.670128] usb 5-1: device not accepting address 15, error -62
Jan 29 18:46:51 duly-desktop kernel: [ 9605.670159] hub 5-0:1.0: unable to enumerate USB device on port 1
Jan 29 18:47:40 duly-desktop kernel: [ 9655.020081] usb 5-1: new low speed USB device using ohci_hcd and address 16
Jan 29 18:47:40 duly-desktop kernel: [ 9655.290336] input: Generic USB K/B as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input6
Jan 29 18:47:40 duly-desktop kernel: [ 9655.290625] generic-usb 0003:13BA:0017.0007: input,hidraw4: USB HID v1.10 Keyboard [Generic USB K/B] on usb-0000:00:13.0-1/input0
Jan 29 18:47:40 duly-desktop kernel: [ 9655.295810] input: Generic USB K/B as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input7
Jan 29 18:47:40 duly-desktop kernel: [ 9655.296113] generic-usb 0003:13BA:0017.0008: input,hidraw5: USB HID v1.10 Mouse [Generic USB K/B] on usb-0000:00:13.0-1/input1
```

Could anyone provide any help as to why this is happening?  I've searched on Google and all the answers are very specific to the device and don't actually describe what's wrong.

I would appreciate it, Thanks!

---

### Post by ahallubuntu on 2012-01-29
I have a couple of these adapters - I think I have three variants.  I've noticed that they don't all work consistently.  The ones I have are "Y" adapters that let me hook up a PS/2 keyboard AND mouse to one USB port.  Sometimes I can use only one device.  Sometimes the adapter isn't recognized at all.  Seems to vary by the adapter I use and what I plug it into.  (The cheapo eBay ones I bought most recently seem to be the worst, but they do work well in some systems.)

One question: you say you are plugging in the adapter without the keyboard.  Why?  Can't you leave it plugged in with the adapter (as if it were a USB keyboard) all the time?  Or is this a laptop that you plug it into, constantly suspending/resuming and plugging the keyboard in and out without a reboot or shutdown?

From your log files, a guess might be that you are running out of USB addresses.  I had that problem years ago in an old version of Ubuntu.  It involved an external hard drive on a server, and for some reason it was re-connected often without a reboot and eventually the server would stop recognizing it without a reboot.  I did track it down to something like that, running out of USB addresses.  64 may be the limit in your case.

What version of Ubuntu are you using?

---

### Post by the pearly gates on 2012-01-29
> **ahallubuntu said:**
> I have a couple of these adapters - I think I have three variants.  I've noticed that they don't all work consistently.  The ones I have are "Y" adapters that let me hook up a PS/2 keyboard AND mouse to one USB port.  Sometimes I can use only one device.  Sometimes the adapter isn't recognized at all.  Seems to vary by the adapter I use and what I plug it into.  (The cheapo eBay ones I bought most recently seem to be the worst, but they do work well in some systems.)

One question: you say you are plugging in the adapter without the keyboard.  Why?  Can't you leave it plugged in with the adapter (as if it were a USB keyboard) all the time?  Or is this a laptop that you plug it into, constantly suspending/resuming and plugging the keyboard in and out without a reboot or shutdown?

From your log files, a guess might be that you are running out of USB addresses.  I had that problem years ago in an old version of Ubuntu.  It involved an external hard drive on a server, and for some reason it was re-connected often without a reboot and eventually the server would stop recognizing it without a reboot.  I did track it down to something like that, running out of USB addresses.  64 may be the limit in your case.

What version of Ubuntu are you using?

Thanks for the response.  

To answer your question, I could leave it plugged in all the time (I'm on a Desktop), but if I got it working and shut down my computer, wouldn't it reset each time I rebooted my computer-- i.e., it would be a random chance that it would work every time I booted my computer?

I definitely don't have 64 connections yet!  I have 1 other one, which is a hub, which connects to a mouse, that's about it.

I'm running Xubuntu 11.04.

Thanks!

---

### Post by the pearly gates on 2012-01-30
I plugged it in and was able to get it working after several times, but after I restarted it didn't work again, so it looks like that isn't a good solution :(.

Any other ideas?

---

