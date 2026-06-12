---
title: "IBM Thinkpad 600/Xircon Ethernet Card (Newbie)"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by redheaddiesel on 2006-01-26
Hello, I'm a total Newbie that just installed 5.10 on an older IBM thinkpad 600. I can't yet connect to the internet because it doesn't recognize my Xircom Cardbus Ethernet 10/100+Modem 56 card (rbem56G-100). 

This is a totally new harddrive (to the computer, at least), and I have no other OS on it. I downloaded the drivers for the card on a jumpdrive, and stuck them on the desktop, but when I click to open it "can't display" the file. I"ve looked at other posts, and even tried to use some suggested code in the terminal, but it says that many of the commands aren't understood or that the program it presupposes doesn't work. 

Is there a way to install thiese windows drivers on my computer? Am I going about this all wrong? 

Thanks in advance! 

Matt. 

I'm also going to post about trying to fix the poor screen resolution (same probelms with entering code above) and later a wireless card.

---

### Post by mips on 2006-01-26
Please forget about windows and windows drivers, ever see someone trying to use linux drivers/software in windows... (The only time you might use windows drivers is when you try and get wireless cards to work with ndiswrapper).

What model 600 do you have 600e, 600x etc. Whats the model on the xircom card ?

Try booting with this parameter: **acpi=off**
See if your card is detected and working. You can later add this permanently by editing the /boot/grub/menu.lst file as explained in one of the threads below.

Can you see the card with this command [B]lspci -v
[/B]
Look at this guide for troubleshoting: [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

[http://www.ubuntuforums.org/showthread.php?t=96240](http://www.ubuntuforums.org/showthread.php?t=96240)
[http://www.ubuntuforums.org/showthread.php?t=106275](http://www.ubuntuforums.org/showthread.php?t=106275)

Your next problem will most likely be the sound. Try searching here for "Thinkpad 600" and you will find lots of info.

---

### Post by redheaddiesel on 2006-01-26
Its just a regular 600 laptop. The model card is Xircom Cardbus Ethernet 10/100+Modem 56 card (rbem56G-100). 

When I do the lspci -v it does see a Dell 1300 wireless network card (which also doesn't work) when it is in, but not the network card. I already went in the terminal and added the acpi=off, and also added apm=on. (I don't have much of an idea of what I'm doing, just blindly following instructions). This info I got from the following forum: 

[http://www.ubuntuforums.org/showthread.php?t=96240&highlight=IBM+Thinkpad+600+resolution](http://www.ubuntuforums.org/showthread.php?t=96240&highlight=IBM+Thinkpad+600+resolution)

I'll check out the other forums you mentioned, but any other comments on problems you see with what I'm doing wouldbe greatly appreciated! 

Thanks! 

Matt.

---

