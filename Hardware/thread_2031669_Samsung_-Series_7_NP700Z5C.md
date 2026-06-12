---
title: "Samsung -Series 7 NP700Z5C"
date: 2012-07-22
forum: Hardware
---

### Post by IcePik on 2012-07-22
I am looking at the Samsung Series 7 NP700Z5C as a replacement for my current laptop.

[http://www.bestbuy.com/site/Samsung+-+15.6%26%2334%3B+Series+7+Laptop+-+8GB+Memory+-+1TB+Hard+Drive+-+Silver/5575679.p?id=1218665501364&skuId=5575679](http://www.bestbuy.com/site/Samsung+-+15.6%26%2334%3B+Series+7+Laptop+-+8GB+Memory+-+1TB+Hard+Drive+-+Silver/5575679.p?id=1218665501364&skuId=5575679)

Some of the specs are as below:
Intel® Core™ i7-3615QM Processor
8GB DDR3 Memory
1TB HDD with ExpressCache Technology, 8GB(I believe this is a 8 GB SSD on the motherbord)
NVIDIA GeForce GT 640 M Graphics

I would like to know if anyone here has this laptop and whether everything works ok out of the box, if not what did you need to tweak to get things started?

Here are a few questions i have:
- How long dose the battery last for?
- Can I run the Intel 4000 graphics processor inbuilt in the processor instead of the NVIDIA card to save on battery performance?
- Can I mount the 8GB SSD as a /boot or a swap partition?


Love to hear from anyone who has one of these laptops and thanks in advance to anyone who can help me.

---

### Post by tuxpower on 2012-07-26
I bought one of these beasts a few weeks ago, and if you can live with the quirks, it's a very nice machine. It also gets very warm on your lap, so be careful.

To answer your questions:

>- How long dose the battery last for?

Under Windows 7 I've seen it go as far as six hours, and under Ubuntu for about four. Charge the battery all the way up and use the BIOS Battery Calibration to drain it all the way down to zero first.

>- Can I run the Intel 4000 graphics processor inbuilt in the 
>processor instead of the NVIDIA card to save on battery 
>performance?

You really don't have a choice here, as the graphics on the Samsung laptops are really only switchable under Windows, leaving the Intel graphics your only option.

>- Can I mount the 8GB SSD as a /boot or a swap partition?

I would not as Windows uses it as Express Cache to speed it up. I'd leave it alone. I've read of individuals trying to use it and losing data when rebooting back into Windows.

Now for the quirks:

1) Booting from a CD/DVD/USB stick requires you to press the F10 key when the machine powers on. What I've found works is to place the bootable media into the machine, power it off, and then power it back on. When the BIOS screen appears, press F10 two or three times until a menu pops up. You can then select the bootable media and proceed from there.

2) The touchpad is really a 'clickpad', similar to that on a Mac. You'll need to tell xorg about it and fix the buttons. I found this works:

 [http://askubuntu.com/questions/165356/x11-ignoring-options-in-configuration-for-input-device](http://askubuntu.com/questions/165356/x11-ignoring-options-in-configuration-for-input-device)

tho you'll have to change Identifier to "ETPS/2 Elantech Touchpad".

Good luck!

---

### Post by tcolar on 2012-08-07
I have one of those for a month+ now and i like it a lot.

I had to tweak quite a few things, I have an extensive howto here:

[http://wiki.colar.net/ubuntu_12_04_on_samsung_series_7_chronos_laptop](http://wiki.colar.net/ubuntu_12_04_on_samsung_series_7_chronos_laptop)

---

### Post by crayzeewulf on 2012-10-21
[B][FONT="Arial Black"][SIZE="4"]*** Warning ***: It is possible to brick this laptop!!!
[/SIZE][/FONT][/B]
Please see this bug related to UEFI booting Ubuntu on this laptop. I have bricked one of these laptops due to this bug.

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

---

