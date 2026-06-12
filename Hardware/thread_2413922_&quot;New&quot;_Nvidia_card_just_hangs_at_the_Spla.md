---
title: "&quot;New&quot; Nvidia card just hangs at the Splash Screen"
date: 2019-03-04
forum: Hardware
---

### Post by james.w.krych on 2019-03-04
Okay, I am currently using Kubuntu 18.04 LTS. I have the following Nvidia card and driver:
[FONT=monospace][COLOR=#000000]root@centurion030-Precision-WorkStation-T7500:~# ubuntu-drivers devices [/COLOR]
== /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0 == 
modalias : pci:v000010DEd000010C3sv00003842sd00001302bc03sc00i00 
vendor   : NVIDIA Corporation 
model    : GT218 [GeForce 8400 GS Rev. 3] 
driver   : nvidia-340 - distro non-free recommended 
driver   : xserver-xorg-video-nouveau - distro free builtin

[/FONT]Operating System: Linux-x86_64[FONT=monospace]
[/FONT]NVIDIA Driver Version:340.107

All is well. 

I recently bought the following Nvidia card:
[COLOR=#333333][FONT=&quot]EVGA Nvidia GeForce GT 220 1GB PCIe x16 Graphic Video Card 01G-P3-1226-LR

[/FONT][/COLOR]It should utilize the existing driver.
[https://www.nvidia.com/download/driverResults.aspx/135161/en-us](https://www.nvidia.com/download/driverResults.aspx/135161/en-us)

When I replaced the older one with this, the splash screen came up but simply remained and wouldn't go any further. I'd like to use the GeForce GT 220.

Any suggestions about this?](*,)

Respectfully,

James

---

### Post by kc1di on 2019-03-04
I would boot with the [nomodeset]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") parameter and then install the nvidia driver again. you may need to enable the [Nvidia PPA ]("https://itsfoss.com/ubuntu-official-ppa-graphics/")to get a newer driver for that card.

---

### Post by james.w.krych on 2019-03-04
And not go by the ubuntu-drivers results?

---

### Post by kc1di on 2019-03-04
You may have to reinstall the drive so the card knows it's there.

---

### Post by james.w.krych on 2019-03-04
I have done all of that and I still keep on getting the nvidia splash screen and then no further.

---

### Post by kc1di on 2019-03-04
Does a live session work?

---

### Post by james.w.krych on 2019-03-04
Sadly, I just get garbage on the screen and it locks. Removing the card.

---

### Post by artcarney on 2019-03-13
I got a new NVIDIA GPU (RTX2080) and I installed the proprietary NVIDIA 410 drivers (from NVIDIA). 

Then Ubuntu 18.04 LTS refused to boot past the "very low res" boot splash. I could get it to boot using the "recovery" kernel.

I used Grub Customizer to disable the boot splash, now when my system boots, it shows me all the startup lines (like in the "old" days before boot splash) but it boots just fine.

Now when my system boots I can tell by a visible changing of the text during bootup that the card has initialized.

Good luck!

David

---

### Post by pqwoerituytrueiwoq on 2019-03-14
It is possible the card was not seated properly or there was dust in the PCIe slot
the most i can see you needing to do is use the nomodeset option
with a card that old you should be fine using the opensource driver

---

### Post by james.w.krych on 2019-03-14
Yeah, I ended up buying a GeForce 710 and the latest driver from Nvidia worked without issue.

---

