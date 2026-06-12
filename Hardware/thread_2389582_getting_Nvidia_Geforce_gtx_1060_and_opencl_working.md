---
title: "getting Nvidia Geforce gtx 1060 and opencl working  on Ubuntu 16.04 LTS"
date: 2018-04-18
forum: Hardware
---

### Post by paolobenve on 2018-04-18
Hi! I got a new Nvidia Geforce gtx 1060 (gigabyte), and I substituted it in my pc, previously I had an asus en210.

I got the gtx 1060 in order to use opencl with darktable, I'm seeing that it's possible in ubuntu ([https://www.phoronix.com/scan.php?page=article&item=darktable-opencl-gpu&num=1](https://www.phoronix.com/scan.php?page=article&item=darktable-opencl-gpu&num=1))

I changed the card in the pc and booted up: the card works perfectly with the nouveau driver, but the driver doesn't permit to use opencl in darktable

I did

```
sudo apt install nvidia-396
```

and rebooted: I got 640x480 resolution

Then I did

```
sudo apt purge nvidia*
```

and rebooted: everything ok (nouveau) driver

I tried with *nvidia-390* and *nvidia-384*: I got no more than 640x480, as with 396

Actually, it happened once that I could get nvidia-390 working at full resolution, but I couldn't get it any more after that.

I installed the graphic ppa:

```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

and reinstalled the nvidia package, but nothing changed.

What am I missing?

---

