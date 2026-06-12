---
title: "problems installing 8180L Drivers for wireless pcmcia card"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by kjoyce on 2005-07-21
I am new to linux and am trying to get a Netgear MA521 wireless PCMCIA card to run under Hoary 5.04 Ubuntu.  My kernel version 2.6.10-5-386

I got the drivers from here : [RTL8180L drivers](http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8180').  They compiled the fine by changing the Makefile to have the Kernel version point to '2.6.10-5-386' and the kernel source to /usr/source/linux-headers-2.6.10-5-386/'.  However when i try to add the module by runnin 'devmod' then 'modprobe open8180' i get the error: 'FATAL: Error inserting open 8180(/lib/modules/2.6.10-5-386/kernel/drivers/net/open8180.ko): invalid module format'.  I googled this error and found that it usually results from compiling from incorrect libraries.  Should I have the kernel source be the linux headers? Or can this error mean something different? Are there alternative drivers?

---

### Post by Milambar on 2005-07-21
My laptop is using the windowXP RTL8081 drivers via ndiswrapper. Perhaps you can do similar?

---

### Post by kjoyce on 2005-07-21
Milabar, do you know of a good tutorial on nddiswrapper? I've heard a few horror stories.

---

### Post by Milambar on 2005-07-21
I find the installation instructions on the ndiswrapper website to be quite easy to follow. I've installed ndiswrapper on 8 machines so far, and everyone has been a smooth install, and flawless working.

That said, I too have heard horror stories, but, when I grill the people telling them, it usually comes down to them "knowing" how to install it without following the instructions properly.

First, I used apt-get install ndiswrapper-tools

Then I extracted the windowsXP drivers to a directory, I chose to mkdir /var/drivers and then extract the windowsXP drivers to that directory. Its irrelevant as long as you know where they are. :)

Then I did ndiswrapper -i NET.INF

Then I checked in dmesg to see if it had installed properly, then did modprobe ndiswrapper.

At that point, the LED on my PCMCIA card started flashing slowly, indicating it was communicating to the laptop, but not to the WIFI.

I then did ndiswrapper -m to generate the appropriate modules.
Finally, I added the line "ndiswrapper" to /etc/modules so that it loads up at reboot.

Then I went to system->administration->networking

It now showed my PCMCIA network card, and I used that tool to finish configuring it.

Job done.

---

### Post by kjoyce on 2005-07-21
Wow, Milambar, I followed your instructions almost verbatim and Voila!  Thank you so much.  That was was almost too easy to be linux ;) Thanks again 
Kevin Joyce

---

