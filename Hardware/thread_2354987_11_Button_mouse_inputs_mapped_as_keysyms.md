---
title: "11 Button mouse inputs mapped as keysyms"
date: 2017-03-08
forum: Hardware
---

### Post by thomas-rudmin on 2017-03-08
I bought a new mouse for gaming and I'm running into some issues with the mapping of 3 thumb buttons.  As I understand, a standard mouse is recognized as having 5 buttons, left, right, scroll up, scroll down, and mouse wheel click.  My mouse therefore has 11 buttons, two of which change the sensitivity up and down respectively (they work just fine), one simulates a triple left click (works but not useful to me) and the three thumb buttons in question.  The buttons are natively mapped to ALT_L, CTRL_L, and SHIFT_L.  When I attempt to assign them to a function inside my game (such as voice team chat) they are not recognized as mouse buttons, they are instead bound to keysyms.  I have messed around a bit with imwheel and easystroke but haven't found a way to have these buttons recognized as mouse buttons and not keysyms.  When I try to see which button is which using xev, I don't get a "button 7" output, it simply says "ALT_L keycode 64 keysym 0xffe9, CTRL_L keycode 37 keysym 0xffe3, SHIFT_L keycode 50 keysym 0xffe1".  I wanted to use imwheel, but running imwheel -c results in, 

INFO: imwheel started (pid=6752)
Configuration terminated by signal 11

and an error report.

 I'd like to have the system recognize my mouse buttons as buttons and not keysyms.    Is there a simple way to accomplish what I'm attempting and where do I start?  The mouse is a[SIZE=2] [Redragon Mammoth M801.]("https://www.amazon.com/Redragon-M801-Programmable-Profiles-Switches/dp/B00GU4F4OM/ref=sr_1_1?ie=UTF8&qid=1488982083&sr=8-1&keywords=redragon+mammoth+m801")[/SIZE]

---

### Post by oldrocker99 on 2017-03-08
*Thread moved to Hardware*

---

### Post by oldrocker99 on 2017-03-08
I did try installing the Windows driver with PlayOnLinux, and it did appear to be frozen. I had to log out to close it.

---

### Post by thomas-rudmin on 2017-03-08
Adding a bit more info, the sensitivity buttons on the mouse are not detected using xev, so likely it's not possible to reassign those in any way (which is fine).  Instead of this being an 11 button mouse, it's really 9.  Left click is assigned button 1, MW click button 2, Right click button 3, MW up button 4, MW down button 5.

Here's the output of cat /proc/bus/input/devices, is it normal to have three separate lines for one mouse?

I: Bus=0003 Vendor=04d9 Product=fa56 Version=0110
N: Name="USB Laser Game Mouse"
P: Phys=usb-0000:00:14.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/0003:04D9:FA56.0004/input/input6
U: Uniq=
H: Handlers=mouse0 event3 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=04d9 Product=fa56 Version=0110
N: Name="USB Laser Game Mouse"
P: Phys=usb-0000:00:14.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/0003:04D9:FA56.0005/input/input7
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=100013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10

I: Bus=0003 Vendor=04d9 Product=fa56 Version=0110
N: Name="USB Laser Game Mouse"
P: Phys=usb-0000:00:14.0-2/input2
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/0003:04D9:FA56.0006/input/input8
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=1f
B: KEY=3f0003007f 0 0 483ffff17aff32d bf54444600000000 1 130f938b17c000 677bfad9415fed 9ed68000004400 10000002
B: REL=40
B: ABS=3fff0100000000
B: MSC=10

---

### Post by thomas-rudmin on 2017-03-08
I found a work around for this.  It involves compiling btnx which I did with this guide:

[http://awesomelinux.blogspot.com/2012/12/btnx-for-ubuntu-1204-and-1210-and-beyond.html](http://awesomelinux.blogspot.com/2012/12/btnx-for-ubuntu-1204-and-1210-and-beyond.html)

btnx is a great tool with a GUI that detects mouse buttons and allows you to assign them to whatever you would like.

I really wasn't able to assign the thumb buttons as extra buttons, but I did map them to unused keyboard entries (Page Up/Page Down) and then assigned those keys in the game for my microphone.  Hopefully someone else with this issue can find this useful.

---

