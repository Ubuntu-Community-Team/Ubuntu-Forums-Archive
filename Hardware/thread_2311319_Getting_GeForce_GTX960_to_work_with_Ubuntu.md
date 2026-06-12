---
title: "Getting GeForce GTX960 to work with Ubuntu"
date: 2016-01-26
forum: Hardware
---

### Post by rexen on 2016-01-26
[COLOR=#111111][FONT=Ubuntu]After more than five years of setting up Ubuntu on various computers, for the first time I am at the verge of giving up on a case.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The issue is setting up proper graphics drivers for the NVIDIA GeForce GTX 960. The default Nouveau driver does not seem to recognize resulutions above 1024, I don't think it will support multi-monitor, and overall I think I will get suboptimal performance. That leaves the official drivers from NVIDIA. I tried installing them from the "Additional drivers" utility in Ubuntu. Installation seems to finish without errors. I then reboot, get a quick Ubuntu splash screen (little progress bar of dots on a purple background), and then it drops to a completely black screen with a little blinking prompt line in the upper left. It never seems to move on from that, so the only option is to reboot. This will then lead to the same place, unless I go to recovery mode and purge everything NVIDIA.[/FONT][/COLOR]

[LIST]
[*]This was all done on a clean install of 14.04 and 15.10 (I tried both).
[*]Monitor is connected with DisplayPort.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]So I am out of ideas, and am hoping that someone here might help. If someone knows a way of setting up multi-monitor with Nouveau, that could also be an alternative.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Things I have tried:[/FONT][/COLOR]

[LIST]
[*]Boot flag "nomodeset" (in fact seens to be necessary to boot at all with 15.10)
[*]Boot flag "acpi=off" (This leads to a stop at the purple screen, instead of the black screen)
[*][http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316)
[/LIST]
[COLOR=#111111][FONT=Ubuntu]List of relevant hardware:[/FONT][/COLOR]

[LIST]
[*]CPU: Intel i7 5820K (Haswell)
[*]Motherboard: ASUS X99-A
[*]RAM: DDR4 2133MHz
[*]GPU: MSI GeForce GTX960 2GB
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Errors I have seen here and there at boot/install. Not sure about relevance:[/FONT][/COLOR]

[LIST]
[*]"acpi pcc probe failed"
[/LIST]

---

### Post by rexen on 2016-01-26
So I finally got it working, in one more iteration of trying different things. (Yes there were many...)


This is what I did:


* Connect a monitor to the DVI-port.
* Fresh install of Ubuntu 15.10
* Set boot option "nomodeset" using the program boot-repair.
* Set blacklist.conf according to here: [http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316) This included fixing the typo "nouveua".

    blacklist vga16fb
    blacklist nouveau
    blacklist rivafb
    blacklist nvidiafb
    blacklist rivatv
    blacklist lbm-nouveau
    options nouveau modeset=0
    alias nouveau off
    alias lbm-nouveau off 

* Switch to non-graphical terminal: ctrl+alt+F1
* Kill GUI: sudo service lightdm stop
* sudo apt-get install nvidia-352
* nvidia-xconfig
* Start GUI again: sudo service lightdm start

And then it worked! 

I think having the monitor connected to the DVI-port while installing the driver is important. My previous attempts used the DP-port while installing the driver. Switching to DVI after driver install did not help.
I connected two additional monitors to DP-ports, and my desktop was extended flawlessly. So it's not that DP doesn't work, but it may be a requirement of at least one DVI monitor to get it set up correctly.

Note that I myself do not have a full understanding of what I did with blacklist.conf and the boot option "nomodeset". Neither do I know if it was crucial to do the install in a ctrl+alt+F1 with a killed GUI. One or many of these things may have been unnecessary. Perhaps others will enlighten us.

---

