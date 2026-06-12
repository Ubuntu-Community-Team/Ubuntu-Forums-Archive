---
title: "Wireless Card disabled after installation"
date: 2010-06-15
forum: Hardware
---

### Post by tdubbs584 on 2010-06-15
I am new to Linux, but not to computers. I installed the new version of **Ubuntu** on my **HP Pavillion dv4 Notebook PC** using **Wubi**. Windows Vista was the factory installed OS and is still operational. When I boot Ubuntu, my wireless card **(Broadcom 802.11 b/g WLAN)** stays **disabled**. I have a button on my notebook but the button remains "orange" (disabled) instead of "blue" (enabled). I restarted back into Windows Vista and the wireless works fine. I followed the troubleshooting in Ubuntu utilizing the terminal command. The output said the card was disabled. 

I found this excerpt from the Pocketguide, but since I am new to Linux, I don't know where to find this...[INDENT][LEFT]'If you’re faced with non&#8208;working wireless, you might try
installing the linux&#8208;backports&#8208;modules&#8208;intrepid package, if
using Ubuntu 8.10, or linux&#8208;backports&#8208;modules&#8208;hardy, if using
Ubuntu 8.04 (reboot after installing). If that doesn’t fix it, you
might consider using Ndiswrapper. This is a hardware driver that
lets you use Windows wireless drivers under Linux."

[/LEFT]
[/INDENT]Please help.
[LEFT]
[/LEFT]

---

### Post by spotted zebra on 2010-06-15
system>admin>hardware drivers

you must be connected via LAN. the program will load available drivers. i am not sure but assuming you are running 10.04 Lucid Lynx you will want the B43 driver if it is offered. if there is more than 1 option and you don't know which to chose just ask and we will help you out.

hope this helps and if it doesn't let us know.

---

### Post by Rhodriguez on 2010-06-19
Hi there, I too am new to Ubuntu and I think I have a very similar problem. I have installed ubuntu 10.04 desktop i386 today on to my compaq presario AMD. The wireless network is on and enabled when I run XP, when I switch to ubuntu, it's disabled. 
As suggested in the previous post, I trid to install the B43 wireless driver from the System->Administration->Hardware Drivers menu but midway through the installation i got the message 'Sorry installation of this driver failed, see var/log/jockey.log for details'.  There didn't seem to be anything wrong in this file, all I could see was:
unbind/rebind on driver sys/module/b43/drivers/ssb:b43:device ss60:0
 
any suggestions you have would be great thanks

---

