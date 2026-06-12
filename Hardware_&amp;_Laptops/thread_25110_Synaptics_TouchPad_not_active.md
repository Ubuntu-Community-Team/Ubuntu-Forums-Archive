---
title: "Synaptics TouchPad not active"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by Jimbo Jones on 2005-04-09
Hello everyone,
I download Hoary Hedgedog liveCD to test the hardware compatibilty and I'm quite happy to see that almost everything is detected. I say "almost everything" because my touchpad is detected (I can see a line in /etc/X11/xorg.conf) but is not active by default.   I try the manipulation explained in the /etc/X11/xorg.conf to reboot xserver after I change the file (There is a thread about it in ubuntu 4.10 section) but it doesn't work more. Otherwise my USB mouse is recognized and I haven't any problem with that.
My laptop is a Toshiba A30-901 with (I think) ALPS touchpad.
Thank you very much for your help.
Jimbo

PS : I hope my english is not too awful

---

### Post by pingswept on 2005-04-10
Hello Jimbo,

I have a Sharp laptop with a Synaptics touchpad that had the same symptoms. I needed to add a kernel boot option (i8042.nomux) to get the touchpad working.

Details in my blog: [http://pingswept.org/index.php?p=57](http://pingswept.org/index.php?p=57)

---

### Post by Jimbo Jones on 2005-05-15
Thank you for your reply. I test that after I have installed ubuntu on the hard drive but it doesn't work. I also tried other things like modifying the i8042.c file and rebuild the kernel but it doesn't work more. 
Despite of that, I read that the problem come from the kernel version. So I installed kernel 2.6.8 and now I haven't any problem with the touchpad. 
But now I have problems with sound. I don't have sound anymore whereas I had it with kernel 2.6.10. 
So here is my question : what can I do to have the sound back?
When I do a "cat /proc/bus/input/devices" I can see that
> I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event2
B: EV=40001
B: SND=6
whereas with kernel 2.6.10, I had :
> I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event0
B: EV=40001
B: SND=6
Thank you very much for your reply. 
Jimbo

---

