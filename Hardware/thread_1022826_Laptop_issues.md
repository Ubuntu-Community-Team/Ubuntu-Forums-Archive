---
title: "Laptop issues"
date: 2008-12-27
forum: Hardware
---

### Post by jorl17 on 2008-12-27
Hi. Recently I bought a new Asus X50GL laptop.

Everything seemed fine but it isn't as well as I thought.

I have various issues and I think you might be able to help me.

First, the battery isn't detected properly. It always thinks it's running on battery power and doesn't report its status

Second issue is the brightness. I really think that since the last kernel update, the screen is dark, and I don't mean the in-brightness, I mean the LCD brightness. (EDIT: I think the fn keys did something but only after rebooting. I youched the brightness fn keys again and now I have it back, so this appears solved)

Also, fn keys aren't mapped as they should (they don't do what they should do with brightness, etc...) and I have some problems which QT that I will report later.

---

### Post by teaker1s on 2008-12-27
sounds like an acpi issue, firstly check on manufacturers support page for bios updates-just in case it's a known bios issue.

---

### Post by hotweiss on 2008-12-28
The only thing I can help you with is the brightness:

The ambient light sensor is the cause of the dim screen, we’ll have to turn it off. To fix this we will have to create a shell script that will be run on boot up that will turn of the ambient light sensor.

A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

---

### Post by jorl17 on 2008-12-28
Thanks for your answers.
(I'll post other problems I've been having in another thread, because they're mostly software-related and not hardware nor laptop-specific)
The brightness issue was a one timer (the lcd light didn't turn on, that's all).

My biggest problems are the fact that Ubuntu (only ubuntu, since Windows does) doesn't shut down.

First, the progress bar from the splash screen (but only the shutdown bar) is fine, but only in the upper-half of the screen. the lower-half seems to corrupt graphics. ACtually, it seems to be pointing to a specific video-memory location that is always the same, since the same sequence of colours passing through this half happens.  After the progress bar  stops, the PC hands there, as if shutdown, but it isn't shutdown.

Ubuntu however can restart (but the progress bar shows the same)

More info on the battery problem: If i boot it with battery, it says it is running on battery power, always. However, if i boot it with the AC cable plugged in (with or without the battery), it says there is no battery.

It does seem an ACPI issue, but nothing of this happens in Windows (which I only kept here for other people, i personally would have simply denied the EULA and erased it...but that doesn't matter). 

Maybe I can show you dmesg, or something else, please do say.

Thanks,

Jorl17

---

### Post by jorl17 on 2009-01-02
bump...

---

