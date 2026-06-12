---
title: "keyboard stops working on choose language screen"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by miasmak on 2005-08-13
Hello all, 

My question, I am doing an Ubuntu 5.04 default install with a vanillaI(cheap) ps2 keyboard and ps2 mouse.

I can get into the bios. I can press enter to start the installation after I have booted from disk but when I get to the Choose language screen it no longer responds to any key presses.

Must be because I was waxing lyrical about how easy the previous install had been, One should only make claims like that out of aura earshot of any hardware.

Any clues will be hugely appreciated.

---

### Post by andlinux21 on 2005-08-13
any chance you can borrow or try another keyboard to see if you can get through the install :neutral:

---

### Post by miasmak on 2005-08-13
I'm on the second keyboard already, no luck, I am suspecting hardware at the moment. It's really weird that it works fine in the bios and then won't carry on. Just about to boot back into the Suse install on the other partition to see if it still works.

---

### Post by miasmak on 2005-08-13
some more info perhaps

When you get to the point where you type enter or server for the install the keyboard works fine. You can go into the help with F1 and read through all the help sections. The minute you type server enter or just enter the Choose language screen comes up and the keyboard doesn't work anymore.

The same with the Suse install that is on the other partition. When the Grub offers a choice of failsafe or normal, you can go in the help but once Suse is loaded, no keyboard or mouse.

I have tried different keyboards, serial mouse instead of ps2 mouse in case the mouse was confusing things, no luck. 

Next step would be to try with windows, oh the horror, I hope I find a solution before resorting to such desperate steps.

---

### Post by miasmak on 2005-08-15
Sorry for the thread bump again, but I am a bit despondant about the state of afairs.

Now I used a completely different ps2  mouse and keyboard which I am sure works fine because I tried the live ubuntu cd on them on my other tower and it works. So I know it isn't the mouse/keyboard.

I fiddled with all the bios settings I could think of but no luck. Enabling/Disabling USB Enabling Legacy USB. I did this on the odd chance that the USB ports on my motherboard was confusing things. Then reverted to default bios settings again.

I also tried calling the install with linux pci=noacpi

I have no USB devices connected.

[SIZE=1]*mumbeling under my breath about planetary allignments, Mercury should be out of retrograde soon*[/SIZE]

---

### Post by miasmak on 2005-09-05
It works again at last.

Here's what I did;

I set the **BIOS to setting for legacy USB to be keyboard/FDD**

I discovered this because I decided to try with a USB keyboard and had to change the BIOS for that. 

The USB keyboard worked and I happened to have the PS2 keyboard in aswell. Both worked.

Now it also works without the USB keyboard.

Frankly I can't quite remember if I ever tried that BIOS setting, but for my own sanity's sake i am assuming I didn't.
Hope this helps someone else in a similar predicament.

---

### Post by foxxx on 2006-10-08
correcting the BIOS setting worked for me, too.
thx for the hint, gj!

---

