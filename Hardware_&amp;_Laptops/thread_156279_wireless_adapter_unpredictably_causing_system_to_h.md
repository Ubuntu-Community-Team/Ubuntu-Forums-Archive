---
title: "wireless adapter unpredictably causing system to hang"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by symphony on 2006-04-06
I recently aquired a wireless router and for my computer a DWL-G132 USB wireless adapter. After much struggling I managed to get the newest version of ndiswrapper installed along with the drivers for the adapter. The adaptor works sometimes, but not other times. When I insert a line saying simply "ndiswrapper" in my /etc/modules file, the computer will start fine and the wireless adapter will work. However, the next time it is shut down, or possibly the time after that(it's not constant), the boot process will hang at "starting hotplug subsystem". When I attempt to load the ndiswrapper module while the computer is running it doesn't work and seems to mess up something with my computer's USB, because the command "lsusb" will hang, not even responding to ctrl-C. In addition to this, when I plug in my iPod(after running "sudo modprobe ndiswrapper") it won't charge or be recognized by the computer. When it hangs at startup I have to boot up with a livecd comment out ndiswrapper in the etc/modules file. Then I reboot and it works fine. Then I change it again, reset, it works. Then the next time I start it up, it hangs at "starting hotplug subsystem". Any ideas?

---

