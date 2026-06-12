---
title: "Logitech M215 wireless mouse"
date: 2010-04-27
forum: Hardware
---

### Post by eveningsky339 on 2010-04-27
[http://www.logitech.com/en-us/428/6064](http://www.logitech.com/en-us/428/6064)

I just purchased this mouse today.  The box brags that one can insert the included AA battery, plug in the USB receiver and surf happily, no software needed.

Since I had a Logitech mouse prior to this one, I didn't expect any problems.  However, the mouse I had previously was not wireless.

So, to put it simply, the mouse doesn't work.  I've gone through the whole troubleshooting process and everything appears to be in order.

---

### Post by nikhil_ on 2010-05-05
I have the same problem, here is my dmesg ouput concerning the receiver when it is plugged in:

```
[ 9347.239743] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input13
[ 9347.239919] generic-usb 0003:046D:C52F.0005: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2/input0
[ 9347.245466] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input14
[ 9347.245621] generic-usb 0003:046D:C52F.0006: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-2/input1
```

could this be an xorg driver issue? I'm quite new to this linux stuff, so this dmesg was all i could provide. Could anyone else provide in detail the exact command they need for any required output to fix this problem?

thanks.

---

### Post by Maximus_ARNP on 2010-05-20
With Ubuntu 10.04 AMD64 on Samsung N210 netbook I have no problem with the same mice. It has been simply plug and play mice.

Sincerely.

Raj.

---

### Post by rondackcpu on 2010-05-22
With either Lucid or Karmic, i386, in Dell 5160 laptop, this Wireless mouse works out of the box.  No setup, no driver, just out of the box.

CRS

---

### Post by mendhak on 2010-07-21
The M215 mouse works with Ubuntu 10.04 Lucid on a Dell Studio 15 Laptop.

I plugged the tiny USB dongle in and it worked immediately.  There was no driver setup, it just worked immediately with no delay.  

I figured I should add to this thread in case anyone else was thinking about buying this mouse.  The mouse-mouse cursor is also quite responsive so you don't notice any delays.  

On Windows you will get a "human interface device" driver setup (tried Windows 2003 and 7) so it's actually a pleasant surprise, this.

---

### Post by lilangus on 2010-08-12
I actually just bought this mouse today. I plugged it in. It seemed to be working properly at first, but now it is kinda blotchy...not very smooth at all. It doesn't work all that great. I think maybe you have to download a driver for it, but can't find one.

---

### Post by measekite on 2010-08-12
> **eveningsky339 said:**
> [http://www.logitech.com/en-us/428/6064](http://www.logitech.com/en-us/428/6064)

I just purchased this mouse today.  The box brags that one can insert the included AA battery, plug in the USB receiver and surf happily, no software needed.

Since I had a Logitech mouse prior to this one, I didn't expect any problems.  However, the mouse I had previously was not wireless.

So, to put it simply, the mouse doesn't work.  I've gone through the whole troubleshooting process and everything appears to be in order.

I read the entire thread.  Like others I do not have an answer; however, I can tell you where to begin.  You should tell others what version of Ubuntu you are using up front.

Here is your first step.  You need to find out if your mouse works with your version of Ubuntu.

Get hold of a Live CD for the version of Ubuntu.  Set you BIOS to first boot from CD and then Hard Disk.  If there is no CD in the drive then your system will boot from the hard disk.

After you boot from the CD your mouse will either work or not work.  If it does not work then return the mouse for another.

If the mouse does work then you should uninstall all software relating to mice and then boot up again.  If the problem still is there then reboot from the CD and print out the Xorg.conf file and add the mouse section to the xorg you get from the Hard Disk boot.  /etc/x11 I think.

---

### Post by sony kusumo on 2011-11-08
Hi, 

Just new to the Ubuntu stuffs, but I guess you should check what kernel are you using.
On the spec, it said that it's compatible with Linux kernel 2.6+ so I guess you should have at least Ubuntu 10.04/Lucid to use it...

Hope it helps...

---

### Post by aquariusmediaaseo on 2011-11-08
Interesting thread. I like the suggestions and views of the members. This thread contains nice information. Thanks for sharing it with me.

 [vastu consultant](http://www.vastudirection.com) | [Tarot Predictions](http://www.panditgopalsharma.com/tarot/predictions.php) | [vastu](http://www.vaastunaresh.com/) | [SEO services in delhi](http://www.aquariusmediaa.com/seo-services.html) | [Silk Fabric in USA](http://www.silkuneed.com)

---

