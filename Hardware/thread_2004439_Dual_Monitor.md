---
title: "Dual Monitor"
date: 2012-06-15
forum: Hardware
---

### Post by Fustigate on 2012-06-15
I got a new PC today so I decided to install Ubuntu as a primary operating system.

I have a 19" and something like a 15", so I want to use the 19" as a primary.

The thing is, I cannot seem to select twinview nor can I find the monitor, only the 19" which is the primary.

I've got NVIDIA X Server installed. 

Thanks in advance.

---

### Post by papibe on 2012-06-15
Hi Fustigate.

Is your computer a laptop, or a desktop?
Are both monitors external, or the 15" is the laptop's DFP?

Regards.

---

### Post by Fustigate on 2012-06-15
> **papibe said:**
> Hi Fustigate.

Is your computer a laptop, or a desktop?
Are both monitors external, or the 15" is the laptop's DFP?

Regards.
It is a desktop.

They are both external.

---

### Post by papibe on 2012-06-15
You can change the layout of the monitors by dragging and dropping the monitors in the 'Nvidia X Server Settings'.

That functionality is not very responsive, and you may need to drag/drop a few times to get the desired layout.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by Fustigate on 2012-06-15
That's the thing, I can't seem to find my other monitor..

---

### Post by papibe on 2012-06-15
Could you do this?

Make sure both monitors are connected and turn on.

Then restart your computer. Once you get to the desktop, post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links in this thread.

Regards.

---

### Post by Fustigate on 2012-06-15
xorg.conf: [http://paste.ubuntu.com/1043239/](http://paste.ubuntu.com/1043239/)
Xorg.0.log: [http://paste.ubuntu.com/1043240/](http://paste.ubuntu.com/1043240/)

---

### Post by papibe on 2012-06-15
Thanks.

Your card is only reporting this monitor connected:
```
[    22.064] (--) NVIDIA(0):     Acer X193W (CRT-1)
```
Since the name 'CRT-1' was assigned, I imagine it is connected using a VGA cable.

What kind of connection does the other monitor have?
Have you try changing the cables to check if it is a cable problem?

Regards.

BTW, your configuration files does not reflect your current configuration (even with current working monitor). I would advice to generate a new one by running:
```
sudo nvidia-xconfig
```

---

### Post by Fustigate on 2012-06-15
They are both VGA leads. 

The one on the side of the back of the PC, and the one at the bottom which is straight. 

I ran the sudo command. I know both leads are working fine because I was using it for my old PC earlier.

---

### Post by papibe on 2012-06-15
> **Fustigate said:**
> They are both VGA leads. 

The one on the side of the back of the PC, and the one at the bottom which is straight.

A question just to discard an unusual situation:

Are both cables connected to your Nvidia Card?  I'm asking this because it is not possible to have dual monitors if one cable is connected to the motherboard's VGA output.

Regards.

---

### Post by Fustigate on 2012-06-15
Couldn't tell you if I'm honest. Would both be giving output? If not, then no. Which I am assuming is the problem, yes?

If it is, how would I go around that?

---

### Post by Fustigate on 2012-06-15
Would I need a DVI TO VGA lead?

---

### Post by papibe on 2012-06-15
You seem to have an Nvidia Geforce GT 520.

Nowadays, most cards have 2 outputs. One is the one that is working on the Acer monitor. There should be another output **right next** to that one. Depending on the card's manufacture, it could be a VGA, DVI, or even an HDMI output.

Connect the other monitor on *that* output if you can.

Another idea: Is is possible for you to post a picture of your computer's back side?

Regards.

---

### Post by Fustigate on 2012-06-15
Of course.
[http://i.imgur.com/SD3Dw.jpg](http://i.imgur.com/SD3Dw.jpg) (PS: Sorry for bad quality, was taken on a Blackberry!)
My main monitor is plugged in to the right of the DVI port on the bottom.

---

### Post by papibe on 2012-06-15
Thanks.

The output you need to use is the white one, located an inch, or so, to the left of one is working.

I'm pretty sure it is a DVI output, so yes, you may need either an a  DVI-to-VGA connector, or a DVI-to-VGA cable.

If either one of the monitors has an DVI input, I would go for a simple DVI cable (DVI-to-DVI).

Regards.

---

