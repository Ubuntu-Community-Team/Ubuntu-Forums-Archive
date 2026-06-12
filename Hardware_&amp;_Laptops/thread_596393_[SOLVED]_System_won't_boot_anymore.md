---
title: "[SOLVED] System won't boot anymore"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by theuninvitedguest on 2007-10-29
First of all, no I didn't break the X-Server for getting some fancy eye-candy running. ;-)
I hope someone can help me identify the root of my problems, since my notebook is the only computer I own.
So let me tell you the story what happened. First I logged of to change user. About the same moment the login-screen became distorted, seconds later the X-Server obviously restarted (had the console output on screen, it was distorted as well btw) and entered the standard (! not the Ubuntu one!) Gnome login-screen. Killed manually the X-Server, everything seemed fine again and logged finally on to one of my accounts. But when I opened the first application, I had a complete rock-solid system freeze! Pushed the power button for 4 seconds the force power-off, and pushed it again. The notebook started... until 2 seconds later when it switched suddenly of... for about 5 seconds more, when it turned on again itself! But it remained undead, with the harddisk spinning but no other reaction, no OEM splash in the beginning, nothing. Ok, I thought, probably just some overheating, give it some minutes to cool down. Same again. Then suddenly, it booted, GRUB loaded, everything seemed fine. Until it froze. Some more attempts till I got it past the splash, when a bios message displayed some memory error (something like 272Megs available, although I've got 512). Reboot. Entered GRUB and selected recovery mode. Got a lot of segmentation faults and the whole process ended with a kernel panic concerning ACPI. Reboot, started Memtest86. After over 1 hour and several passed tests it showed 10240 error (10*2^10 ??). One really noticable thing about the output of the corrupted addresses is that the error are all on the same position (0000ff00).
In between the damn thing still often refuses to start up like described above. And last but not least, WindowsXP won't boot as well (duh!).
To cut a long story short, it smells like broken hardware. Probably it's just the memory, but since this is the only thing I can afford at the moment, it's definitely not the memory but something more critical.

Some more details on the system:
ASUS M6827NEUP (Chipset: Intel i855PM / Mobile Platform)
RAM: 512MB DDR333
OS: Ubuntu Gutsy

To everyone who payed attention up to this point: thanks in advance!
Alex

---

### Post by Wicca on 2007-10-29
> **theuninvitedguest said:**
> Probably it's just the memory, but since this is the only thing I can afford at the moment, it's definitely not the memory but something more critical.


I do not understand what you mean. Just because you can afford it, it cannot be the memory?:confused:

I am almost certain it is the memory, although you will never be 100% sure until you replaced it and the problem stays away. Try changing it (borrow it from a friend, whatever) , or, if you have 2 banks of 256mb, take one out.

You can also try to run the LiveCD too. If the problem is gone, it might be a damaged disk.

Good luck.

---

### Post by theuninvitedguest on 2007-10-29
> **Wicca said:**
> I do not understand what you mean. Just because you can afford it, it cannot be the memory?:confused:

Exactly. Murphys law, you know? ;-)

I'll try changing the memory; it's going to be tough since the one slot is under the keyboard and not directly accessible... :-\

Thanks a lot for your quick reply!

Alex

---

### Post by theuninvitedguest on 2007-10-29
Solved!
Indeed it had something to do with the memory, but it wasn't the RAM itself which was damaged but the slot where it was plugged in. Put the RAM into the other (free) slot and it worked perfectly again!

Thanks for your attention, maybe that helps someone in the future.

Alex

---

