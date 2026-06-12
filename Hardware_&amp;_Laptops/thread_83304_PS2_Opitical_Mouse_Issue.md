---
title: "PS/2 Opitical Mouse Issue"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by RockinRodent on 2005-10-28
Greetings

I am trying out the live version of Ubuntu, to see if it will suite my needs. When I boot up, my optical mouse will not work. It's a 2 button wheel mouse. It seems that the wheel is working. I've noticed that the laser isn't on when Ubuntu is running.

Another question about Ubuntu in general...does wifi work with it? If I like it, I'll install it. But I need it to work with WIFI. Both a wifi card, and a USB wifi device, if possible.

Thanks.

---

### Post by JasonH on 2005-10-28
I've heard that Breezy works fine with WiFi, but I started in Hoary so I had to do a few workarounds to get mine to work (I decided to keep everything through the upgrade, to much work to lose).

---

### Post by anan_uk on 2005-10-30
I'm running Ubuntu on my laptop...
and everything works fine...

but i would like to use my optical mouse on PS/2 port instead of my touchpad(which seems to get first priority) :( 

Please help....

---

### Post by Effect on 2005-11-01
This is a problem for me. I'm using a Micro Innovations optical mouse that connects via the PS/2 port. I've noticed that with any version of Linux since I got it causes the laser/light inside to just go off whenever a Linux OS boots up causing me to pull it out of the computer and back in when I reboot to start up Windows (don't have any problem with the mouse here). 

I could use my other mouse but that's really my laptop mouse and I'd like to stop using that anyway since I've been using it for so long. This really is a kicker for me. Any help with this? Is it something about the Linux kernel that doesn't care for this stype of optical mouse? 

That's the only connection I can think of between the different versions of Linux I tried this mouse on(PClinuxOS, Ubuntu, Mephis, Fedora Core 4).

---

### Post by Schmots on 2005-11-01
Have one of those ps/2 to usb adapters... my usb optical mouse works just fine on my laptop.

---

### Post by Effect on 2005-11-01
Is that what it takes to get it working?

---

### Post by greenwom on 2005-11-02
The adapter gets it to work, from some googling I've found that the PS/2 port doesn't doesn't have the "brains" by itself.  That wasn't much help.  I've tried looking through the repositories to see if there was a package that addressed this but nothing....  I'll post my answer when (if) I find it.

---

### Post by ionophore on 2005-11-03
Try taking a look at the contents of /dev/input/ and see if there are any mice-like entries in there.  For example, i have a "mouse0" file in that directory.  If you have such a file (or something similar) try doing a:

cat/dev/input/mouse0   (or whatever particular mouse-like file you have)

When you move the mouse you should get garbage on the screen.  That will indicate that the system is getting input from that port.  That would be my first step.  If you do get garbage when you move thr mouse it's probably an X configuration issue.  See here:

[http://www.x.org/X11R6.8.2/doc/mouse.html](http://www.x.org/X11R6.8.2/doc/mouse.html)

---

