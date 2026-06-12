---
title: "Ubuntu on an old Shuttle XPC SB51"
date: 2015-12-11
forum: Hardware
---

### Post by AndiNewGreen on 2015-12-11
Hi, i am very new to Ubuntu, but very greatful for any tips to a newbie :).

I have got a Shuttle XPC SB51G with the following specs:

CPU: Pentium4 3,06GHz HT
Memory: 2GB RAM, DDR333
Graphics: onboard, 256MB RAM shared
[http://www.shuttle.eu/_archive/older/en/fb51.htm](http://www.shuttle.eu/_archive/older/en/fb51.htm)

I tried Ubuntu 15.10 and 14.04.3 LTE.

The problem is, the system runs very very slow.

Booting is fast, but when i open for example the system settings window, it needs 3 seconds to show up.
It doesnt seem like a memory problem, it more seems like a graphics driver problem. If i want to move the window on the desktop, the window just follows in stop-motion.

So heres my question :-k :

Do I have to somehow implement the drivers for the mainboard ( which are all windows drivers ) to Ubuntu, or is there an easier way?

Many thx!

---

### Post by kc1di on 2015-12-11
Hello AndiNewGreen and welcome to Ubuntu,

A pentium 4 is quite old now.  I think the video card may also not be up to snuff. 
However give Lubuntu or xubuntu a try they are not so resource intensive.

---

### Post by AndiNewGreen on 2015-12-11
Many thx!

I am quite aware that this setup is out of date.

Its just that so simple things like opening a folder takes for the graphics so long to show up.
Loading wouldnt be a problem, but if i want to close the folder, it needs 3 seconds to fade away.
Its as if there is no mainboard driver installed.

Is there somewhere a way to find out if this chipset is supported?

---

### Post by weatherman2 on 2015-12-11
I know exactly what you mean about the slow performance on older computers.

You could try Lubuntu, but that requires re-installing from scratch.

Instead, in Ubuntu as you have it now, try installing Gnome Flashback - which gives you kind of an old-style interface but has worked great for me on old computers:

[http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/](http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/)

I use Gnome Flashback (Metacity) shown on that page (one of the login options) for the best performance on older computers.

---

### Post by AndiNewGreen on 2015-12-11
Cool, many thx.

Reinstalling wouldnt be no problem, absolutely not.

I have read about Lubuntu, i will try it!

Yes, this Gnome Flashback looks handy.


I will report if it works fine then.

---

### Post by matt_symes on 2015-12-11
Hi

> **AndiNewGreen said:**
> Hi, i am very new to Ubuntu, but very greatful for any tips to a newbie :).

I have got a Shuttle XPC SB51G with the following specs:

CPU: Pentium4 3,06GHz HT
Memory: 2GB RAM, DDR333
Graphics: onboard, 256MB RAM shared
[http://www.shuttle.eu/_archive/older/en/fb51.htm](http://www.shuttle.eu/_archive/older/en/fb51.htm)

I tried Ubuntu 15.10 and 14.04.3 LTE.

The problem is, the system runs very very slow.

Booting is fast, but when i open for example the system settings window, it needs 3 seconds to show up.
It doesnt seem like a memory problem, it more seems like a graphics driver problem. If i want to move the window on the desktop, the window just follows in stop-motion.

So heres my question :-k :

Do I have to somehow implement the drivers for the mainboard ( which are all windows drivers ) to Ubuntu, or is there an easier way?

Many thx!

I have a couple of similar (discontinued) shuttle boxes.

```

    description: Desktop Computer
    product: SS59V10
    vendor: Shuttle Inc
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: FS59V10
       vendor: Shuttle Inc
       physical id: 0
```

They can run Xubuntu adequately (turning off compositing helped) but don't expect any kind of Stirling performance.

The SIS graphics chipset in mine has, at times, been a pain though. SIS were never exactly open source and Linux friendly.

Kind regards

---

### Post by AndiNewGreen on 2015-12-13
Hi,

the machine runs very nice with Lubuntu, very smooth!
So it now can be used! :) ( its only for looking up datasheets on the internet for a little toolshop )

I also tried the Gnome Flashback before, very handy. I keep that in mind!

Xubuntu would also be worth a try.


Many thx to you all! :)

---

### Post by AndiNewGreen on 2015-12-25
Hi once again! ):P

So i got a dedicated Graphicscard for very cheap money to make the Shuttle PC a bit faster:

"Gainward Nvidia GeForce FX5200 128MB DVI AGP"

While this card should be a lot faster then onboard "Intel 845GE/ICH4", it is a lot slower.
Scrolling up and down on a simple google search result window is almost impossible.

I am almost sure that driver is not implemented, or at least not working right.

I tried for several hours to install the Linux Display Driver - x86 "173.14.39"
[http://www.nvidia.com/Download/driverResults.aspx/71302/en-us](http://www.nvidia.com/Download/driverResults.aspx/71302/en-us)
 with the help of verious tutorials, but with no success.

Can somebody pls tell me how this can be done. Many thx for any help!

( OS: Lubuntu 15.10 )

( perhaps this thread should then be moved to the software section )

---

### Post by mörgæs on 2015-12-26
You need to post much more information.

> **AndiNewGreen said:**
> 
Scrolling up and down on a simple google search result window is almost impossible.

Which browsers did you try? 
Did you dis- or enable soft scrolling?


> **AndiNewGreen said:**
> 
with the help of various tutorials, but with no success.

Which ones? Please describe in detail or post the links.

---

