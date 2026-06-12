---
title: "Sentelic Touchpad not working"
date: 2012-04-23
forum: Hardware
---

### Post by Limator on 2012-04-23
Hi guys,

i'm using ubuntu 11.10 on my laptop. the touchpad isn't identified properly. so it's used as a regular mouse, not as a touchpad. it's a sentelic touchpad. i've installed a 3.3.2 kernel form the mainline, i tought the newest driver should work, but i don't.
when i check grep -i sentelic /boot/config-$(uname -r), it appears
CONFIG_MOUSE_PS2_SENTELIC=y
this should be ok, isn't it?

what can i do to make the touchpad working? what information do you need to help me? 

thank you in advance!

kind regards

---

### Post by Limator on 2012-04-23
Hi,

anything i can provide you that you can help me?
here is dmesg:
[http://media.cdn.ubuntu-de.org/forum/attachments/10/17/4258282-dmesg.txt](http://media.cdn.ubuntu-de.org/forum/attachments/10/17/4258282-dmesg.txt)
and here the devices:
[http://media.cdn.ubuntu-de.org/forum/attachments/10/17/4258282-devices.txt](http://media.cdn.ubuntu-de.org/forum/attachments/10/17/4258282-devices.txt)

---

### Post by miz0ooo0 on 2012-04-23
hey dude ,i had this problem with ubuntu 11.10 64bit "AMD" on dell n5110 ,recently i upgraded to ubuntu 12.04 with _32bit_ "intel",after that i had my touchpad recognized with option of 2 finger scrolling
i think that the version 32 bit is more suitable for laptops specially if you have intel processor not AMD

---

### Post by Limator on 2012-04-23
hi,

yes i'm using an 32bit intel system. but it is a intel i5 2450M with 8gb ram and nvidia gt540M optimus. so the 64bit system is the better choice for all the other hardware.

but maybe anybody knows how to transfer the 32bit advantages to the 64bit system?

---

### Post by cortman on 2012-04-23
> **miz0ooo0 said:**
> hey dude ,i had this problem with ubuntu 11.10 64bit "AMD" on dell n5110 ,recently i upgraded to ubuntu 12.04 with _32bit_ "intel",after that i had my touchpad recognized with option of 2 finger scrolling
i think that the version 32 bit is more suitable for laptops specially if you have intel processor not AMD

If your computer (laptop, desktop, whatever) has a 64 bit processor, use 64 bit; if not, use 32 bit. As far as driver support goes the 32 bit kernel is no different than the 64, AFAIK.
The reason it started working for miz0oooo0 is that they had a kernel upgrade in between 11.10 and 12.04.

OP, an upgrade to 12.04 seems to be one solution to your problem. Otherwise, there's always [this thread.]("http://ubuntuforums.org/showthread.php?t=1862078&page=5")

---

### Post by Limator on 2012-04-23
Hi,

i already tried to use 12.04, without success! that's the strange thing!

maybe it's a general problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869/comments/91](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869/comments/91)

what do you think? what could i do? what information could i provide? or maybe miz0ooo0 could provide some of his informations?

and sorry for my mistake, i'm using a 64 bit system, not a 32bit. using a 32bit kernel makes no sense for my configuration.

thank you in advance for your help!

---

### Post by cortman on 2012-04-23
Re 32 bit vs 64 bit, it really doesn't matter which one you're running. I was merely pointing out the fallacy of the previous poster's response.
Basically your problem is that your trackpad is not using its multitouch capability, but still works otherwise? If so, you may have to [http://askubuntu.com/questions/27990/how-can-i-get-multitouch-enabled-on-my-sentelic-touchpad-msi-x350-notebook]("http://askubuntu.com/questions/27990/how-can-i-get-multitouch-enabled-on-my-sentelic-touchpad-msi-x350-notebook")live with it. Sentelics support seems to be years behind synaptics.

---

