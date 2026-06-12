---
title: "USB Enclosure button = unount? (i.e. writing my own driver)"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by djbon2112 on 2008-02-27
Basically, I've got the Cooler Master X-craft external USB enclosure for my hard drive, and it has a button on the front that can be pressed. I assume that when this is pressed, some sort of interrupt is sent to the operating system (in Windows I believe there's software to make it do stuff). I'm looking to capture this and use it to do something (specifically, unmount the volumes on the drive via a shell script).

However, I'm a bit of a noob to Linux and C (but not to programming in general; I'm learning C as we speak anyways). Does anyone have any tips to start me out? How would I even find out what happens in the system when the button is pressed? How do I go about writing a basic driver to do this?

If anyone has any starting advice, I'm certainly looking for some! :)

If this is in the wrong category, please move it for me! Thanks!

---

### Post by djbon2112 on 2008-02-28
Just a little update, here's the item:

[http://www.coolermaster.com/products/product.php?language=en&act=detail&tbcate=32&id=69](http://www.coolermaster.com/products/product.php?language=en&act=detail&tbcate=32&id=69)

There's already Windows drivers for it, and the button is (at least in Windows) for backup software. I figure I'll ask, has anyone already written a driver to handle the button on this device? I just want it to call a shell script when pressed; if there's already a driver out there, it makes everything that much easier (I started reading O'Riley's "Linux Device Drivers" book, and am getting a little scared and overwhelmed! :p)

---

