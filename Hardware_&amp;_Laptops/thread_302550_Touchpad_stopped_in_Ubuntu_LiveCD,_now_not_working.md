---
title: "Touchpad stopped in Ubuntu LiveCD, now not working in Windows"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by kaajd on 2006-11-18
The Problem: When I tested out the Ubuntu-6.06.1-desktop-i386 LiveCD (iso download) on my ACER Aspire 5102WLMi AMD Turion64 x2 Laptop with a Acer Navarro ATI Radeon RS482 mainboard, the 'Synaptics TouchPad V6.2 on PS/2 Port' gave me some unusual behavior and then stopped responding completely. I had to shutdown using the keyboard. Booting into native Windows XP MCE 2005 showed the extent of the problem. The mouse cursor does not respond to the TouchPad here either, except, just as the desktop loads, before the startup programs finish loading, the mouse responds correctly to the touchpad and buttons for a few seconds, then stops completely and does not move again. Also when Windows is shutting down, the mouse responds for a second before the laptop turns off.

Additional Info: I had D/Led and tested both Ubuntu-6.06.1-desktop-i386 and -amd64 and both Kubuntu-6.06.1-desktop-i386 and -amd64. In Kubuntu-amd64 the mouse started out okay but soon started to behave improperly. When I stroked the touchpad to move the mouse, the cursor responded as if (on a normal external mouse) I clicked-and-dragged. I do not think that Kubuntu-i386 did the same thing, though I can't quite remember, so I don't think so. Ubuntu-i386 did this just before the mouse froze on me. Ubuntu-amd64? I don't remember. In the Knoppix 4.0.2 LiveCD the mouse also locked up at one point but there were no lasting effects on reboot. Now it no longer responds to the touchpad either.
In Windows, after the fact, I tried doing a restore, unistalling and automatically reinstalling the Synaptics drivers, and manually reinstalling the drivers. Nothing worked. The Device Manager always said that the 'Synaptics TouchPad' device was working correctly.

Conclusion: I think this is a hardware problem because the LiveCD is not supposed to touch my HDD and therefore my Windows drivers should still have worked. The touchpad is still functional because the cursor responds at certain times. My guess is a hardware/motherboard/BIOS error. But what exactly?

Question: Is this a known problem with Linux? Is there a known solution? Do I have to wait before I can use Linux on my Laptop?  Can I ever again use my touchpad, at least in windows? I'm going to check for newer Synaptics Windows drivers and try those but I doubt that'll fix it. Could this have something to do with the tapping func of the touchpad? It worked sorta in Ubuntu. I can survive with an external USB mouse, but I would really like my touchpad back (as a 'built-in, no wires' option) and my brand new laptop perfectly functional again. Please. I'm a linux newbie.

---

### Post by TrD on 2006-11-19
I have the exact same problem. My touchpad only works for a few seconds when I activate it in windows control panel. In ubuntu it only worked once back when I first installed edgy and has stopped working ever since.

My laptop is an acer aspire 5100

---

### Post by dansnik on 2007-01-15
Hi,

Regarding the touchpad not working on an Acer 5100, please try the following:

Press 'Fn' and 'F7' keys together and this should alternate between turning the touchpad on and off. 

Cheers,


Dan

---

### Post by TrD on 2007-01-21
Hi Dan.

I've already tried Fn+F7, but thats not the problem either. It also doesnt work in Windows.

---

### Post by kaajd on 2007-02-06
The 'Fn'+'F7' key combo was the answer (I came across this by accident).  Touchpad now behaves.  I think this all came from incompatibility issues between Linux and the ACPI (I think) aspect of my hardware.  Just looking around the forums and I can see there are significant problems with touchpad drivers in linux.  I think my laptop hardware thought linux sent it the command to disable the touchpad which is why it also failed to work in Windows.  I'm running Ubuntu now in virtualization mode (VMWare Player) just to be safe.  Thanks.

---

### Post by FrooziE on 2007-12-14
Yea, I'm an idiot. FN+F7 was all that was needed. Thanks for that. I spent about 2 days poking around the web for the answer. At least it'll never happen to me again :)

---

### Post by rockinlinux on 2007-12-14
have you guys looked in you bios and made sure everything is on? im sure you have but im just making sure ;)

---

### Post by kringle on 2007-12-16
Thank You!!  I feel like an idiot, too.  It stopped working in Vista and I figured it, Vista, hosed the drivers again like it kept doing with the ATI drivers.  The restore disc errored and wiped out Vista, so now my daughter will be running Gutsy only...probably for the best anyway...

---

