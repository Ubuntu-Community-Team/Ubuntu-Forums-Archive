---
title: "Hooking up a second external display on my HP box, with NVidia G84GLM"
date: 2015-11-27
forum: Hardware
---

### Post by Cbhihe on 2015-11-27
I want to add a second external display to my laptop hw configuration and I do not know whether it is possible. 
I look for advice focussing on that question: is it possible and if so, how ?

I run Trusty 14.04 LTS X86_64 Desktop on an HP8510w laptop.****It has a dedicated 2GB memory
GPU with VGA compatible controller NVIDIA Corporation G84GLM [Quadro FX 570M] (rev a1) 
My kernel driver in use is: nouveau.

In addition to my laptop 15.4" internal display, I also have an external display connected to a VGA port. The external display extends my laptop integrated display.
I also have an unused HDMI port.

My questions are: 
[B]- Can I add a third display  (or second external display) to further extend my laptop integrated display ? 
- Can my hardware handle that ? 
- Can Ubuntu 14.04 handle that ?[/B]
- If the answer is (Y,Y,Y), how should I proceed ?

Tx -ced

---

### Post by brian-mccumber on 2015-11-27
You could just hook up the third monitor and find out for yourself. It would be quicker than waiting for a response and I don't think it would mess anything up, it will work or it won't. It would probably work better if you use the Nvidia driver for your card tho instead of the basic graphics driver.

---

### Post by Cbhihe on 2015-11-27
Yay ! 
If someone could just lend me 200 unit$ so I can go buy an HDMI monitor and try it out for size... And if it does not work, well... I could still keep using it as a hurricane size paper-press I suppose.
 
More seriously, you may well be right, Brian,  that I will get little in the way of an answer, (so far nothing) but I am trying to avoid having to buy a external monitor, just to ***try*** it. I am hoping somebody will read this, who has had some experience in that area.

BTW, I did contact NVIDIA to see if the G84GLM [Quadro FX 570M] GPU is 3-monitor capable. No answer.

Any help welcome !

---

### Post by brian-mccumber on 2015-11-28
Well shoot man, I was under the impression you already had the hardware. I did a little research for you using google and it seems that people have had success using the vga/dvi and the hdmi to run two external monitors and the laptop monitor at the same time. But like I said in the previous post I made, you will probably be better off using proprietary Nvidia drivers for your particular graphics chip instead of the generic nouveau driver. I have also seen some laptop setups that are running two vga monitors and a laptop display by utilizing the built in vga port for one external monitor and a vga to usb adapter for the other external monitor and the examples I viewed were using older laptops too. The USB adapter comes with a driver disk but the example I looked at was running Windows but there is an application for Linux that will allow you to install Windows drivers in Ubuntu if there are no available Linux drivers for the usb to vga adapter. I used this application to install Windows drivers for my USB wireless card. I think the usb to vga adapter will be less expensive than springing for a hdmi monitor. There are alot of configurations that would possibly work for this, if you were to use google to search you may find a cost effective solution that will work for your particular setup. It may require a little work to get it set up but it is quite possible to get two monitors and your laptop display to work together which will in effect give you three monitors to work on.

---

### Post by Cbhihe on 2015-11-28
Thank you Brian. 
A) I have looked at the possibility you mentioned to drive an external monitor with a USB-VGA adapter, base on a solution normally rolled out for M$ Windoze. For me it is not the most logical very first hack to think up though. I favor Linux native solutions. Faced with the lack of something both viable AND Linux, I will definitely look at that possibility with more of a tingle in my eye at some point. Right now, 

B) As far as using Nvidia rather than Nouveau drivers, again you're mostly right as nearly all benchmark tests (on Lx 14.10 and later), I have seen for later generation Nvidia chips with reclocking, show that  Nvidia drivers are far superior. 
Notwithstanding, with my legacy GPU and 14.04, I have no gamer's demands on rendering performance and for me my nouveau based on X.Org X Server functions perfectly well. In fact I find it is more stable than the latest available Nvidia proprietary driver (version 340.96) for my Quadro FX 570M] (rev a1). I did download and try the latest Nvidia driver and finally opted out to go back to nouveau. 
(I only wish I could code so fast that I would run into keyboard buffer speed or image rendering problems from vim with nouveau... That would no doubt add a couple of zeros to my salary !) 

Back to my issue:
**Does anyone out there have direct experience with hooking a VGA monitor + a HDMI monitor to one laptop in desktop-extend mode (so that the end result are three monitors driven by one quadro GPU) ?**

---

