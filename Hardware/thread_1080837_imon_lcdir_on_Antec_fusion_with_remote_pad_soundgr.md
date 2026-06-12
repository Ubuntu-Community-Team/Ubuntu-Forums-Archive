---
title: "imon lcd/ir on Antec fusion with remote pad soundgraph vfd 15c9 0038 knob"
date: 2009-02-25
forum: Hardware
---

### Post by Kalibur on 2009-02-25
imon lcd remote pad soundgraph vfd 15c9 0038

Hello Good people

I recently bought a media centre case, the Antec Fusion Remote. It comes with a built in LCD screen infra red remote receiver a volume knob on the case and a remote controller. All these feature connect through a single USB interface. Using lsusb the device is indentified as 15c9:0038 Soundgraph (Remote). Ubuntu picks it up its getting it to work thats a problem, In the forums I have read countless how tos that seemed to have worked on older versions of this hardware but it doesn't work with my hardware.

In some ubuntu distro especially older ones its picked up and locked by HID and identified as a keyboard device and thats ok except it work work. The fellows that got some versions to work in the how tos started by stopping HID from locking it then using a compiled version of lirc. Which is fine but I feel there is an easier way devices like t his can be supported by linux.

I was running an install of win xp and during the setup process I could using the remote control move the mouse pointer and the remote control number pad enter numeric characters basicly the remote was working as a mouse/numeric keyboard combo using basic win xp plug and play drivers. Now the Antec case was release in 2007 several years after win Xp was released.

So my guess is this device 15c9 0038 the remote control part of it at least is following some mouse keyboard protocol that has been around for a while.
Why am I not getting semilar behaviour in ubuntu? A usb keyboard works from the box so why not this remote because basically its just an infra red keyboard mouse combo and by default ubuntu tries to load it as such its just not functional.

Can support for this type of device be included in Jaunty or other future versions

---

### Post by shabazzk on 2009-05-01
I second this notion, I just bought an Antect IR Multiedia Statoin Basic and not too sure how to get it working. Along with the receiver I purchased a Logitech Harmony 550 remote. Think I may need to compile, as I do not think LIRC supports my Specific device, since it may be new model. But I'm confident it will all work since other Antec IR receivers do.

It sucks that LIRC doesn't auto detect the IR receiver you have plugged in and configure you system appropriately. Instead, every one has to go through compiling and doing the same thing over and over. 

I'm all for using the command line, as it is usually the fastest way to install and get something working. But not for simple redundant stuff like this. What is the point of Synaptic Package Manager (SPM) if I still have to go behind it and configure the software afterwards.

Ubuntu makes Linux look inviting until you need to add functionality. It is a long way from being user friendly as windows. DANG, I NEVER thought I would compliment a Microsoft program (makes me sad:().

---

