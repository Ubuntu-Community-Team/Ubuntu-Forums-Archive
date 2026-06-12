---
title: "AMD &quot;Unsopported Hardware&quot; watermark"
date: 2011-10-10
forum: Hardware
---

### Post by mothergoose729 on 2011-10-10
Hi, I recently installed both Ubuntu and Kubuntu 11.04 64bit on my llano system, which has an AMD a-3850 processor and an Fm1 micro atx "pro" Asus motherboard. Both times, after installing the third party ATI display drivers, I got an "AMD Unsupported Hardware" watermark in the lower right hand corner of my screen. The display driver seems to be working correctly, but obviously this watermark is kind of a big problem. 

In my own attempts to fix this, I have tried altering the watermark script,  as well as updating my drivers manually according to instructions I found on these forums. Despite copying and pasting code exactly, I have managed to do nothing but bork my system both times. I was wondering if there is a way to fix this. I wouldn't mind downgrading to Ubuntu 10.04 if I had too, or using an older display driver. I want the watermark go away, and I want the display driver to work enough for multimonitor support and hardware acceleration for media. Any help would be great. Thanks a lot.

---

### Post by coffeecat on 2011-10-10
What is the ATI GPU that you have? With my ATI Radeon HD5450 card I get perfectly adequate 3d acceleration - enough for Unity, compiz and playing HD videos at least - with the default open source driver, and setting up dual-monitors was a breeze.

---

### Post by mothergoose729 on 2011-10-10
> **coffeecat said:**
> What is the ATI GPU that you have? With my ATI Radeon HD5450 card I get perfectly adequate 3d acceleration - enough for Unity, compiz and playing HD videos at least - with the default open source driver, and setting up dual-monitors was a breeze.

Llano has a built in GPU from the 6k series. What is the open source driver? How can I install this as opposed to the proprietary drivers?

---

### Post by coffeecat on 2011-10-10
You don't install it - it comes in the box. You simply uninstall the proprietary driver and the open source one will be activated when you reboot. But before you do that - what was video performance like before you installed the proprietary driver? That was with the open source driver. Compatibility varies and the 6*** series being newer, you may or may not get good performance from the open source driver.

---

### Post by mothergoose729 on 2011-10-10
If this was the open source driver then the compatibility is not very good. It couldn't even display the full resolution of one of my monitors.

---

### Post by coffeecat on 2011-10-10
I'm sorry to hear that. I guess the GPU is too new. When 11.10 is out next week, give that a try from the live CD. It will have a newer version of the open source driver.

---

### Post by mothergoose729 on 2011-10-10
> **coffeecat said:**
> I'm sorry to hear that. I guess the GPU is too new. When 11.10 is out next week, give that a try from the live CD. It will have a newer version of the open source driver.

Hm, ok. Is there a way to try the newest version of the open source driver with 11.04?

Furthermore, might the proprietary driver linked to by ubuntu to be out of date? The 6k series has been out for well over a year, and the specific model of my integrated GPU has been out for several months.

---

### Post by coffeecat on 2011-10-10
The video driver is usually built to go with a particular version of the xserver, so you'd probably need to upgrade that as well. Three ways that I can think of, none of which I've tried so I don't know whether they will be of any help. The first would be to enable the backports repository and see if anything is offered with that. Or, one of two ppa repositories:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by SingleSpeed10 on 2011-10-20
> **coffeecat said:**
> I'm sorry to hear that. I guess the GPU is too new. When 11.10 is out next week, give that a try from the live CD. It will have a newer version of the open source driver.
I numerous issues an AMD A6-3650 (Llano) and 11.04. Although it worked, I  got no hardware acceleration (no Unity 3D), missing 1080p settings for  my Plasma monitor, etc. All is well with the upgrade to 11.1.

---

