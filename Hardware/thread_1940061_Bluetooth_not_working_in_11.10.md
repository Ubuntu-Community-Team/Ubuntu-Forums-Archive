---
title: "Bluetooth not working in 11.10?"
date: 2012-03-12
forum: Hardware
---

### Post by bohemian9485 on 2012-03-12
Greetings forum.

I installed Ubuntu 11.10 Oneiric on my Lenovo S10-3 Ideapad netbook (replacing the original Windows 7 Starter OS), and things did look great. It is only the other day when I tried to transfer some pictures from my cellular phone to my netbook using bluetooth did I realize that the built-in bluetooth was not working. I can see the bluetooth applet icon enabled on my panel, it says the bluetooth is on. But in system settings it says my bluetooth is disabled. As a Linux noob, I'm pretty much stumped here. Google search only show up how to connect bluetooth devices, but nothing useful to resolve my problem. The information I got from Lenove website did not state the bluetooth device maker either. All I want to know is, how can I enable my onboard bluetooth device?

Help is greatly appreciated and more powers!

---

### Post by Vitnim on 2012-03-18
Same issue with Gnome 3.4 on an Acer 3820T.  

After booting cold into Ubuntu, the applet shows bluetooth on, but options show it off and un-toggle-able.  Using FN+F3 will toggle bluetooth (and WiFi) on and off in the applet properly, but no love in options or usability.

If I start the computer cold into Windows, bluetooth is off.  Using FN+F3 brings up the toggle and I can then switch it on and use it no problem.  
If I then restart (not shutdown) from Windows and then boot into Ubuntu, bluetooth is on in both the applet and options, and works fine with no problems. Everything worked on 11.04.

Unfortunately, I also suffer from not knowing enough to be able to do anything about it.

---

### Post by bohemian9485 on 2012-05-20
Now I have upgraded my system to 12.04 Precise, but the problem still persists. From [here]("http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4313") I got the specification for my Broadcom BCM4313 chip, but no solution. Googling the net got nowhere either.

Just I thought that I was at my wit's end, I found the solution on how to activate the built-in bluetooth adapter: Knoppix LiveCD. While reading my reference book Linux Bible 2008 Edition by Christopher Negus, I learned that Knoppix has a great hardware detection capability and I thought, why not use Knoppix to detect my blueetooth adapter? Sure enough, after booting into my netbook using Knoppix 6.4 Live USB, I saw that the bluetooth was disabled, and there is a button with the caption Enable (the most beautiful caption at that moment :lolflag:). After clicking the button and re-start my netbook normally to boot into Precise, the built-in bluetooth adapter is functioning again. Now I have no problem connecting my cellular phones and other bluetooth devices. So I consider it solved.

---

