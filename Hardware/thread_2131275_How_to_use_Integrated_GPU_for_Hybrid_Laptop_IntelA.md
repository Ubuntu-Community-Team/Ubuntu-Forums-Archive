---
title: "How to use Integrated GPU for Hybrid Laptop Intel/ATI?"
date: 2013-04-01
forum: Hardware
---

### Post by YLTO on 2013-04-01
Hi Folk! Sorry to interrupt. So here's the problem, I have Lenovo Laptop Y460 equipped with Hybrid GPU that is an Intel Integrated GPU and an ATI Radeon HD 5650 as Discrete GPU. Basically in Windows 7 I can switch the GPU either by switching the button in the laptop or directly from the software program.
[IMG]http://i.imgur.com/fD4ujWtl.png[/IMG]

What annoy me is when I install Ubuntu as Dualboot alongside my windows 7, and once I boot to Ubuntu; The Discrete GPU turn on automatically. I don't like it cause I don't need it and the worst is it could drain my battery and overheat my laptop till it get shut down automatically.


So what did I do? I read a ton of post/article about this switching thing. This led me try these "How-to in step by step"
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide)


1. I try to install ATI Catalyst driver 3 times but eventually it failed when I reboot it.
The result is
[IMG]http://i.imgur.com/l4VTVhil.jpg[/IMG]

[IMG]http://i.imgur.com/OEpRJ1Wl.jpg[/IMG]
So I choose the first option *Running in low graphics session*. But unfortunately when I got into desktop view, everything is blank including the dock and taskbar except the purple background color of ubuntu and the system also give a notice *System is corrupt*


While for the case of **Linux Mint**, when I boot into Linux Mint - My view become Command Line Interface instead of GUI. The system also give a notice *XOR Server fail to start*.


2.Another way is I try to switch off the Discrete GPU from BIOS, but sadly there is no option for Integrated GPU under the **Graphics tab**. Instead the option is only 2, either switchable graphic or Discrete GPU.


So here I am, Now I'm stuck - don't know what to do. Could you help me how to solve it? (my purpose is I just want to use the Integrated GPU).




Lenovo IdeaPad Y460 Specifications:


 - 14.0" HD Wide LED 1366x768 
 - Windows 7 Home Premium 64-bit
 - Intel Core i5 520M processor (2.40GHz, 3MB cache)
 - ATI Mobility Radeon HD 5650 with 1GB VRAM and Intel GMA HD Switchable Graphics 
 - 4GB DDR3-1066 RAM (2x 2GB) 
 - 500GB 5400RPM hard drive (Seagate 5400.6)
 - Intel Wireless Wi-Fi Link 1000BGN
 - Built-in Bluetooth v2.1+EDR
 - 8X DVD burner
 - 6-cell Li-ion battery (11.1V, 57Wh)
 - Weight: 4.98lbs
 - Dimensions: 13.4 x 0.79&#8211;1.3 x 9.25 inches

---

