---
title: "Laptop booting only when battery is removed"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by deepla on 2008-01-16
Hi ,

I  just installed Ubuntu in my acer laptop 1640. I am new to Linux and is presently using dual boot. My laptop is having a problem and i am able to use Windows only if i disable the ACPI from device manager window. If i dont disable it, the Windows XP will not load completely. After showing the desktop, it will hang and mouse and keyboard become very slow or not respond. When i tried to see what process is running, the task manager would show that a process named SYSTEM would be running continuously and using cpu 100%. I used to press the power button and shut down and before it shuts down it would show that a process related to battery power is not responding.(I forgot the name of the process). It would shut down if i give end-task. If i remove the battery from the laptop and and start it on AC power, everything works well. So someone suggested that it could be because of a problem in battery management and suggested that i disable ACPI .I did that and then inserted the battery and rebooted . Everything works. Only problem is that i am not able to see how much battery power is left. I am able to run it in battery alone also. 
This is how i survive with Windows. 
	I installed Ubuntu as dual boot and it was giving the same trouble. I was able to continue the installation and use it only when i remove the battery and run it in AC power. I tried rebooting with the boot options acpi=off , acpi=off apm=on, acpi=oldboot, acpi=ht. None has worked.                                                           
        Can anyone help please. I did not try changing the battery because Acer charges a lot and I was hoping I would be able to manage somehow.

---

### Post by saultpastor on 2008-02-05
If the OP is still around...

I have had the same or similar problem with an Acer laptop.  I tracked it down to some board that regulates power to the battery when it is charging (the chances that a battery change will fix it are slim)

I wish I could give you the solution.  I solved this problem once about 8 months ago.  I now have installed Gutsy (before it was Linux Mint) and I can't remember how I fixed it.

The best I recall I disabled the battery module before it was loaded.  Blacklist doesn't work because that is for hotplugging.  I did blacklist the battery module in Linux Mint, but I'm not sure if that worked or if I tried it and just left it that way and found another way...blacklist doesn't work in Gutsy.

Please, if some Linux Genius could tell me how to disable the module at startup I would be very grateful.  I have rmmod battery in rc.local but it is too late.

---

