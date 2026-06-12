---
title: "Webcam works on one system but not another"
date: 2011-02-22
forum: Hardware
---

### Post by pwabrahams on 2011-02-22
I have two computers, one a laptop and one a desktop, both running fully updated Kubuntu Maverick (10.10).  Both are 64-bit machines.  On both I have installed and activated the v4l repository.  Each machine has two webcams, one of which I've been moving back and forth between the machines.  That webcam shows up on each machine under **lsusb** with id 058f:3820 (Alcor Micro). 

Here's the mystery: the webcam I'm swapping back and forth produces an image under **cheese** on the laptop but not on the desktop.  On each machine the other webcam works correctly and produces an image.  On the desktop I get no error messages, but only a black image from the Alcor webcam.

What could possibly account for this?

---

### Post by MetalMusicAddict on 2011-02-22
> **pwabrahams said:**
> I have two computers, one a laptop and one a desktop, both running fully updated Kubuntu Maverick (10.10).  Both are 64-bit machines.  On both I have installed and activated the v4l repository.  Each machine has two webcams, one of which I've been moving back and forth between the machines.  That webcam shows up on each machine under **lsusb** with id 058f:3820 (Alcor Micro). 

Here's the mystery: the webcam I'm swapping back and forth produces an image under **cheese** on the laptop but not on the desktop.  On each machine the other webcam works correctly and produces an image.  On the desktop I get no error messages, but only a black image from the Alcor webcam.

What could possibly account for this?
Is the cam on the desktop plugged in through a hub or direct? (i've had this issue before)

---

### Post by pwabrahams on 2011-02-22
The nonworking one on the desktop is indeed plugged into a hub, and plugging it in directly caused it to work.   But the working one is also plugged into the hub.  Unfortunately the nonworking one has a relatively short cable, so I wouldn't be able to use it with a direct connection without an extension cable.

I wonder if there are any tricks to getting it to work with the hub.  Or, I suppose, I could just use the other one, which isn't quite as good.

---

