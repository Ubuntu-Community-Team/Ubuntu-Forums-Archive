---
title: "USB Problems while and after installation"
date: 2012-03-03
forum: Hardware
---

### Post by kleebuntu on 2012-03-03
Helly,

I've got a problem with my Ubuntu 11.10 x64 installation and beyond. I made a bootable flash stick with yumi and got the installation to boot. the issue was, that I was not able to use my keyboard and mouse. After replugging them they worked.

After the installation the first boot was ok and I installed the updates through the update-manager. After a restart my usb devices (1 keyboard with background lightning, two mice) were not working. the background lightning of the keyboard began to flicker. both mice were not recognized at all.

I started to replug them again to get them recognized but then my usb headset began to crinkle. I stopped it after a reboot.

after all I Thought: "OK, kernel 3.2 will fix it" and updated to the 12.04 beta (64bit). But the problem remains.

Thats my hardware setup:
Motherboard: ASUS P8Z68-V Pro/GEN3
CPU: Intel i7-2600k
RAM: 16GB 1600MHz Corsair C8
SSD: 120GB OCZ Vertex2
Graphics: Gigabyte GTX460OC 1024MB VRAM

Does anybody know how to fix it? 

Thanks in advance.

klee

---

### Post by Bucky Ball on 2012-03-03
Welcome.

Um, 12.04 LTS is not released for another couple of months so wouldn't go looking there for a fix. Latest is not always the greatest. 

Are you getting these issues with a rock solid, stable kernel/release? e.g. 10.04 LTS ...

Obviously it was the update that killed you and I'm guessing you have updated the kernel. Try dropping back to the previous kernel (select it from the list at boot, should be third down under the new kernel's recovery kernel) and try that.

---

### Post by kleebuntu on 2012-03-03
Thanks for the welcome :D

I had the issues before the 12.04 update. they came up at the 11.10 installation and while booting into the installed system (11.10). then I made the normal updates (no update to 12.04).

the update to 12.04 was my last try to fix it.

Are there any known issues with the usb support for Sandy-Bridge mainboards or can I check the usb drivers, reinstall them, fix them?

---

### Post by kleebuntu on 2012-03-04
Today I installed 11.10 x64 from a CD and have the same problem -.-"

---

### Post by Bucky Ball on 2012-03-04
Tried 10.04 LTS? It is the current long term support release (supported until April 2013). Boot from the CD, 'Try Ubuntu' and see if your USB and everything else works. If so, maybe install that. 

It is a one click upgrade to 12.04 LTS from there, if you want to go there, and that is supported for five years (until April 2017). I would wait a couple of months after release if you go that way, check the forums and see how stable it is. You could even wait until 10.04 LTS end of life by which time 12.04 LTS should be as rock solid as 10.04 LTS is now.

---

### Post by kleebuntu on 2012-03-04
I tried the 10.04.4 x64 LTS an got the same problem. I started the "try ubuntu" and there were some error messages in the console: 

usb-hid can't restart

or something like that. mouse and keyboard did not work either...

---

### Post by Bucky Ball on 2012-03-04
Okay, well that narrows it down a bit anyhow. Seems to be something about your hardware configuration and the way Ubuntu handles USB. It doesn't help, but does this sound like you?

[http://askubuntu.com/questions/104378/boot-stuck-after-discovering-usb-devices](http://askubuntu.com/questions/104378/boot-stuck-after-discovering-usb-devices)

When you boot from the LiveCD how far do you get and take note of exactly what happens, including exact error message, and post back here.

If you can get to the screen with the option 'Try Ubuntu', hit F6 and try the option 'acpi=off', then 'Try Ubuntu'.

---

### Post by kleebuntu on 2012-03-04
Hm not really. But he has the same motherboard series... Maybe there is a problem with the usb chipset in asus motherboards - my windows 7 is working fine.

Edit: the usb 2.0 is integrated in the intel z68 chipset. my mouse and keyboard are plugged at usb2.0.

this isn't a known problem? :D asus is a well known company and usb2.0 is used often :D

When I boot from the LiveCD I can get into the ubuntu gnome desktop. but I can't do any inputs with my mouse and keyboard.

I try that acpi=off thing. brb.

---

### Post by Bucky Ball on 2012-03-04
> **Bucky Ball said:**
> 
When you boot from the LiveCD how far do you get and take note of exactly what happens, including exact error message, and post back here.

If you can get to the screen with the option 'Try Ubuntu', hit F6 and try the option 'acpi=off', then 'Try Ubuntu'.

Try this. If it doesn't work try with the option 'nomodset'. If one of these works then we can tweak once you're in the desktop.

---

### Post by kleebuntu on 2012-03-04
Tried acpi=off and acpi=off nomodset.

both did not solve the problem.

---

