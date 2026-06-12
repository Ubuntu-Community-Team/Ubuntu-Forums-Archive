---
title: "Seagate - FreeAgent GoFlex Desk 3TB External USB 2.0/3.0 Hard Drive"
date: 2011-08-03
forum: Hardware
---

### Post by Cardale on 2011-08-03
On my Asus G73JW ROG-A3B7M

I have a USB 3.0 slot and this drive and it doesn't show up.  When I plug it in the light turns on so it is getting power in Ubuntu.

I know the drive works because if I boot into Windows 7 it shows up.

Here is the drive - [http://www.bestbuy.com/site/Seagate+-+FreeAgent+GoFlex+Desk+3TB+External+USB+2.0/3.0+Hard+Drive+-+Black/1361508.p?id=1218252977386&skuId=1361508&cmp=RMX&ref=06&loc=01&ci_src=14110944&ci_sku=1361508](http://www.bestbuy.com/site/Seagate+-+FreeAgent+GoFlex+Desk+3TB+External+USB+2.0/3.0+Hard+Drive+-+Black/1361508.p?id=1218252977386&skuId=1361508&cmp=RMX&ref=06&loc=01&ci_src=14110944&ci_sku=1361508)

---

### Post by Cardale on 2011-08-03
Here is a 

dmesg output 

[http://pastebin.com/bJ3ZtSDB](http://pastebin.com/bJ3ZtSDB)

lspci output

[http://pastebin.com/9v9Mv8qQ](http://pastebin.com/9v9Mv8qQ)

lsusb output

[http://pastebin.com/6rAsi3zi](http://pastebin.com/6rAsi3zi)

---

### Post by Cardale on 2011-08-03
lspci -v output

[http://pastebin.com/FFYCnGMh](http://pastebin.com/FFYCnGMh)

---

### Post by Cardale on 2011-08-03
New dmesg output after modprobe -r xhci_hcd

[http://pastebin.com/yW1eAn0u](http://pastebin.com/yW1eAn0u)

---

### Post by Cardale on 2011-08-03
I found a related post to the issue.  Sorry about the multiple posts I'm just trying to be as helpful to some one who can actually fix the issue.  I have no idea where to start.

[https://bbs.archlinux.org/viewtopic.php?id=114355&p=2](https://bbs.archlinux.org/viewtopic.php?id=114355&p=2)

---

### Post by Cardale on 2011-08-04
bump

---

### Post by Cardale on 2011-08-06
bump

---

### Post by Cardale on 2011-08-12
Well with no help from any of you crazy ubuntu care bears I got it working.

For anyone else that is stuck like I was here you go for free like Adam Sandler in Bed time stories.

```
sudo gedit /etc/default/grub
```

find and change to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"
```

Reboot and plug in your device.

---

### Post by Cardale on 2011-08-14
Confirmed this works in Fedora as well by editing the grub.conf.

---

### Post by CMXILies on 2011-12-14
Killer, thanks dude.

---

### Post by mckemie on 2012-01-18
This thread seems to be about getting the drive recognized and auto-mounted.  I recently bought a couple of these at attractive prices.  11.10 had no trouble recongizing and mounting the drive.
I did have a fair amount of trouble getting it re-formated to ext4.  Using gparted rather than some other formatter seems to be the key.

Here is some interesting discussion:
[http://is.gd/0IQvgB](http://is.gd/0IQvgB)
[http://ubuntuforums.org/showthread.php?t=1536933](http://ubuntuforums.org/showthread.php?t=1536933)

There is some funny stuff going on in the hardware that Seagate will not tell us about.  Even though gparted seems to deal with the situation, it is probably best to avoid vendors that are not friendly to Linux.

---

### Post by Cardale on 2012-05-18
We are at 12.04 and still no support for this device.  Any plans?

It works with USB 2 but not USB 3

---

