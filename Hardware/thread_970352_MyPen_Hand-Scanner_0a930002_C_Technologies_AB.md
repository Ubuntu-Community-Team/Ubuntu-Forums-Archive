---
title: "MyPen Hand-Scanner: 0a93:0002 C Technologies AB"
date: 2008-11-04
forum: Hardware
---

### Post by thomi_ch on 2008-11-04
Hi all

I have a MyPen Handscanner by C-Channel.. [http://www.c-channel.ch](http://www.c-channel.ch)

lsusb:
Bus 002 Device 003: ID 0a93:0002 C Technologies AB

tail -f /var/log/messages
Nov  4 10:44:09 hercules kernel: [415781.770635] usb 2-1: new full speed USB device using uhci_hcd and address 4
Nov  4 10:44:09 hercules kernel: [415781.964510] usb 2-1: configuration #1 chosen from 1 choice

dmesg
[415781.770635] usb 2-1: new full speed USB device using uhci_hcd and address 4
[415781.964510] usb 2-1: configuration #1 chosen from 1 choice


Now, i'm searching for anybody who has a linux driver for this device. The device is really handy to scan bill referenz numbers and single text/number lines.

That is the information from the manufacturer:
[http://www.c-channel.ch/index.php?FormKat=2&FormProdukt=2e747822a80508a09.86289341&FormOS=13&FormButton=%A0weiter%A0&sid=9fa7d8a7b4fe7d97423eb3cba93b0118&oxid=&cl=ms_support_main&actshop=1](http://www.c-channel.ch/index.php?FormKat=2&FormProdukt=2e747822a80508a09.86289341&FormOS=13&FormButton=%A0weiter%A0&sid=9fa7d8a7b4fe7d97423eb3cba93b0118&oxid=&cl=ms_support_main&actshop=1)

.. means, no linux support :(

I have searched around the web, but get no answer...

If there is any developer who can create a driver.. i think some people are happy about it ;)

If you need more information, just post it here and i try to get it.

Thanks for time and greetings from switzerland
thomi

---

### Post by ulrichard on 2012-08-20
Hi Thomi,

did you find a solution yet?

I just bought a used myPen to start experimenting, as there still seems to be no official linux support. I asked the vendor for the status on this a few times before. No luck so far.

So I thought I just buy the cheapest one I can get and see if I can make a driver for it. I never developed any driver before, so there is a lot to learn for me, I hope. 

I just asked the vendor for as much information as they can provide.

What did you find out in the meantime?

I assume the device sends some kind of image to the computer, and then the OCR happens in software. 
But capturing with wireshark on linux doesn't get me very far. So, I'll probably set up an XP virtual machine and hope for more luck.

Rgds
Richard

---

### Post by thomi_ch on 2012-08-21
Hi Richard

Don't spent more time in this.. i do all manually ;), by hand...

I know, that there are a lot of driver developers on the linux world, maybe we just need to have time to wait and some of them will help us.

Keep in touch.. :D

Regards
thomi

---

