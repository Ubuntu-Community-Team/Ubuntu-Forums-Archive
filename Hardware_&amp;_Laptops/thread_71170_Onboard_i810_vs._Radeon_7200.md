---
title: "Onboard i810 vs. Radeon 7200"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by DonPachi on 2005-10-02
Hi All,
My pc has an onboard Intel i810 video chipset that works just fine with Ubuntu.
I would like however to get my ATI Radeon 7200 PCI card working.
My BIOS has no option to disable the i810, only to select betwee PCI and AGP video but there is no AGP port on the board! (thanks emachines.) 
Currently ,with the Radeon card plugged in to a PCI slot and my monitor plugged into the Radeon, my pc will post and begin booting linux until it starts X at which point the screen goes blank and remains that way.
...so my question is:  What steps should I take to get the Radeon card working?
Attached are my xorg.conf and the output from lspci.

---

### Post by Hamman on 2005-10-03
[QUOTE=DonPachi]Hi All,
My pc has an onboard Intel i810 video chipset that works just fine with Ubuntu.
I would like however to get my ATI Radeon 7200 PCI card working.
My BIOS has no option to disable the i810, only to select betwee PCI and AGP video but there is no AGP port on the board! (thanks emachines.) 
Currently ,with the Radeon card plugged in to a PCI slot and my monitor plugged into the Radeon, my pc will post and begin booting linux until it starts X at which point the screen goes blank and remains that way.
...so my question is:  What steps should I take to get the Radeon card working?
Attached are my xorg.conf and the output from lspci.[/QUOTE]

I might have missed something, but you should replace "Driver    'i810'" with "Driver 'radeon'". X tries to run your Radeon with the Intel driver.

---

### Post by yrjo on 2005-10-03
[QUOTE=DonPachi]Hi All,
My pc has an onboard Intel i810 video chipset that works just fine with Ubuntu.
I would like however to get my ATI Radeon 7200 PCI card working.
My BIOS has no option to disable the i810, only to select betwee PCI and AGP video but there is no AGP port on the board! (thanks emachines.) 
Currently ,with the Radeon card plugged in to a PCI slot and my monitor plugged into the Radeon, my pc will post and begin booting linux until it starts X at which point the screen goes blank and remains that way.
...so my question is:  What steps should I take to get the Radeon card working?
Attached are my xorg.conf and the output from lspci.[/QUOTE]
Look first what pci slot your Aticard uses in var/log/Xorg.0.log,for example:PCI:1:10:0.  Restart pc. Press ESC in the begging when pc automatically picks up kernel. Choose recovery mode. You will be root in the terminal. Write: dpkg-reconfigure xserver-xorg.Choose radeon module when you can choose module. If you cant get to x, edit manually with gedit  /etc/X11/xorg.conf to get right pci slot numbers. That's how I did it.

---

### Post by DonPachi on 2005-10-03
[QUOTE=Hamman]I might have missed something, but you should replace "Driver    'i810'" with "Driver 'radeon'". X tries to run your Radeon with the Intel driver.[/QUOTE]

Please forgive my lack of understanding, but I've been using linux for about a month now. 
When editing xorg.conf do I need to replace the entire "Device" section of xorg.conf? Or do i need to add another "Device" section for the Radeon?

---

### Post by Hamman on 2005-10-03
[QUOTE=DonPachi]Please forgive my lack of understanding, but I've been using linux for about a month now. 
When editing xorg.conf do I need to replace the entire "Device" section of xorg.conf? Or do i need to add another "Device" section for the Radeon?[/QUOTE]

First, you don't have to appologize for not knowing this. In fact, I wish more people were as descriptive when asking for help with their problems. 
Secondly, I don't think you need to replace the hole section, just change 
Driver		"i810" to
Driver		"radeon"
You might wanna rename 
Identifier	"Intel Corporation 82810 CGC [Chipset Graphics Controller]" to something like
Identifier	"ATi Corporation Radeon 7200 PCI" 
but then you would also need to change to the exact same value in 
Section "Screen"
The difference is purely cosmetical though. 
Try that and see if it works.

---

### Post by DonPachi on 2005-10-03
I'd like to thank both of you for your help.  

I edited xorg.conf manually, changing the driver to "radeon" and changing my identifier to  "ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
Also I changed the BusID section to match the output from lspci -X that described my radeon card.  

And it worked superbly. Thank you!

---

### Post by Hamman on 2005-10-04
[QUOTE=DonPachi]I'd like to thank both of you for your help.  
I edited xorg.conf manually, changing the driver to "radeon" and changing my identifier to  "ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
Also I changed the BusID section to match the output from lspci -X that described my radeon card.  
And it worked superbly. Thank you![/QUOTE]

I'm glad to hear it worked!

---

