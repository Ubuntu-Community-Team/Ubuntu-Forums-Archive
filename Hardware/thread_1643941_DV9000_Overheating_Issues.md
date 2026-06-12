---
title: "DV9000 Overheating Issues"
date: 2010-12-12
forum: Hardware
---

### Post by DarkCDE on 2010-12-12
I've read about DV9000 overheating issues, but not like this...

I have an HP DV9000 I bought years ago with an Intel Dual core 2ghz, and GeForce Go 7600.

I have friends with identical computers that have been in and out of the shop for overheating issues, I thought I was one of the lucky ones that dodged the HP overheating bullet. I thought wrong :(

Two weeks ago, after installing Ubuntu I got the weird artifacts and then blank screen. Booting in windows had the same issues, so definitely hardware. I reflowed the chip the right way (liquid flux, sustained heat monitored at 180c with an IR thermometer, arctic silver, etc.).

It works great again, but the GPU still runs really hot - like 60-80c degrees hot. The funny thing, my processor is showing near freezing temps. 1-3c per core. This is the problem.

These computers control the fan speed based on the CPU temp. My fan at these temps won't run. In windows, I tricked the system into thinking the CPU temp is 60c. So my fan is running full bore. My GPU now sits at a cool 30-40c.

In Linux, it still runs hot. Is there a way in Linux to trick the BIOS into thinking my CPU is a certain temp? As far as I know, the fans on these can't be directly controlled. The BIOS takes the hardware temp that the OS reports and automatically sets the fan speed as needed.

Any help would be greatly appreciated. Ubuntu is totally unusable on this machine now. lm-sensors also doesn't seem to do what I need.

---

### Post by seannon on 2011-02-07
I am having same issues, DV9000/DV9700 series DV9820US to be specific, and the fans come on, but not soon enough, and do not ever get it to below 50C, normally it is around 70C, the hard drives also are higher than SMART suggests as the high temp of 50C, normal load for them is between 55C and 62C... this is also on "Powersave" or "800MhZ" on the scaler applets...

---

