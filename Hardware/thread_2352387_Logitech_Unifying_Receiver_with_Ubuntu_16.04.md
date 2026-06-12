---
title: "Logitech Unifying Receiver with Ubuntu 16.04"
date: 2017-02-12
forum: Hardware
---

### Post by aquib on 2017-02-12
I am having problems using my Logitech Wireless Keyboard & Mouse, which are connected using the Logitech Unifying Receiver. The problem is that keyboard or the mouse will stop working intermittently and will either require powering off and on the keyboard/mouse. At times this does not work and I will have to pull the receiver from the usb port and reconnect it. At times I just have to reboot the computer. 

I have dual OS on my computer (Windows 10 and Ubuntu 16.04). I dont have any problems with the keyboard and mouse on Windows and I expect the same from Ubuntu.

Hope someone can give me a concrete and permanent solution.

PS: I have installed Solaar as well.

---

### Post by QIII on 2017-02-12
Hello!

Can you provide more information on your hardware -- including the motherboard.

---

### Post by aquib on 2017-02-12
Hi QIII
Thanks for replying. The information you asked for is as below. Let me know if more information is needed. 

Cheers
Aquib

Motherboard : Gigabyte P55A-UD3
Processor : Intel(R) Core(TM) i5 CPU  760  @ 2.80GHz
RAM: 12006 MBytes
OS: Ubuntu 16.04 xenial
Kernel : Linux 4.4.0-31-generic

---

### Post by aquib on 2017-02-13
No one interested in helping me solve a fundamental problem.

---

### Post by efflandt on 2017-02-16
I use a Logitech mouse all the time with a Unifying receiver and have never had any problem, except when I had a graphic card that began failing shortly after its one year warranty expired. I am not even sure if I was using a wireless mouse at that time, but symptoms were that mouse buttons and keyboard would stop responding, although, mouse cursor would still usually move.

I currently use MX Master mouse, and previously used Anywhere MX mouse until its M1 button failed due to gaming (fixed using contact cleaner, but relegated to less frequent laptop use). I have not used a Logitech K400 wireless keyboard much other than trying it out on my desktop. I usually use that keyboard and Anywhere MX mouse on a laptop for viewing WebEx sessions in Win10 off on the side where inconvenient to type (chat) on the laptop itself.

There is an Ubuntu package called "solaar" which can associate Logitech devices with a Unifying receiver and in some cases tell battery level.

---

### Post by QIII on 2017-02-16
Does this work if you have the receiver in a USB2 port on startup?

---

### Post by kurt18947 on 2017-02-17
My thought is similar to QIII. If the device is plugged into a USB 3 port and you have a USB 2 port available, try that. Or just try a different USB x port.

---

### Post by Rinre on 2017-02-19
I think the last two posts might contain the solution:
 I also have the Unifying receiver (with M805 mouse and K270 keyboard). If I remember correctly I used to have some problems with reception in the beginning (while still on (L)ubuntu 12.04) . I read somewhere that usb3 inputs can "disturb" the infrared signals or something, so I tried putting the unifying receiver in the USB 2.0 port on the back of the computer which is farthest from the usb 3.0 ones. Also, I put an extension usb-cord between the computer and the receiver, keeping the receiver itself below my screen, "in sight" of the mouse and keybord (don't remember if this also improved the reliability). Now, on Ubuntu (Studio) 16.04.1, I didn't have to do anything (didn't even install solaar), it just worked.

---

