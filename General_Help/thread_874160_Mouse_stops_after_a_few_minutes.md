---
title: "Mouse stops after a few minutes"
date: 2008-07-29
forum: General Help
---

### Post by Düal on 2008-07-29
The installation with wubi went fine, but I'll log on to ubuntu and shortly after I do this my mouse stops. I checked the USB and there is nothing wrong with it. My keyboard works because I used it to shut down ubuntu.

How can I fix this?

---

### Post by minhmeoke on 2008-07-30
I am assuming that you have a usb wired mouse, could you tell us the manufacturer and model? If you have a bluetooth/wireless mouse, then your mileage may vary, since some are incompatible with ubuntu.

Open a terminal, and after the mouse stops working, type in the "lsusb" command. This should show you all connected usb devices, for example

Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse

If there is nothing there, then there is probably a hardware conflict, you may have to edit boot parameters, search for "noapic". If the mouse is still detected by lsusb, then you can try reconfiguring Xorg, which handles display and input devices, use the "sudo dpkg-reconfigure xserver-xorg" command.

Also, try typing in "dmesg" to show the message log, and look for errors near the end.

---

### Post by Düal on 2008-07-31
Yes I am using a wired mouse.

This is the mouse that stopped after a few minutes,

[http://www.xsreviews.co.uk/reviews/peripherals/razer-death-adder/3/](http://www.xsreviews.co.uk/reviews/peripherals/razer-death-adder/3/)


I also tried using an older mouse which I had which was a Microsoft intellipoint 4.1 mouse, it worked longer then my first but it eventually stopped working as well.

After it stopped I opened the terminal and used the "lsusb" command and showed intellipoint 4.1 along with my other USB ports.

I also used the "noapic" but it only showed about reconfiguring my keyboard.

---

### Post by Düal on 2008-08-01
Sorry to bump and double post in this topic, but no one has replied in an entire day.

---

### Post by minhmeoke on 2008-08-02
It seems that there is a bug in your mouse's firmware (see: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/74069](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/74069) ), so you might want to try updating the firmware first.

If the mouse still does not work, try adding "acpi=force irqpoll" or "noapic" to your boot options in /boot/grub/menu.lst
See this thread for instructions: 
[http://ubuntuforums.org/showthread.php?p=2595386#post2595386](http://ubuntuforums.org/showthread.php?p=2595386#post2595386)

This might also be useful for enabling more buttons: [http://ubuntuforums.org/showthread.php?p=2398239](http://ubuntuforums.org/showthread.php?p=2398239)

You can search ubuntuforums for more solutions if the ones listed above do not work.

---

### Post by sanga_sanga on 2008-08-06
Both Ps2 and usb mice stop on a computer im using after a few minutes. I tried the "acpi=force irqpoll" line, but it made the cursor disappear :mad:. The version is Hardy. 

what exactly does "acpi=force irqpoll" mean and do? has anyone else faced this problem too, and how did it get solved? any help would be much appreciated..

---

