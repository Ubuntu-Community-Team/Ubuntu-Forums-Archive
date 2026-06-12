---
title: "Keyboard not loading in time"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by cbeckwith on 2007-05-21
When the GNU GRUB menu comes up to select OS to load the keyboard does not work and time runs out and so ubuntu linux loads everytime.  I was wondering if anyone else has had the same time of problem or has any suggestions.  Thank you.

---

### Post by Ubimad on 2007-05-21
the keyboard must be not recognized, ubuntu is free, investing 20$ in a new keybord makes nobody pennyless.
try if keybord works in the BIOS
what notebook you are runing ?

---

### Post by cbeckwith on 2007-05-23
i got a usb keyboard and it still does not work.  I have a vaio labtop.  The keyboard does not work during bios I cant use the keyboard until the time runs out and Ubuntu gets chosen and Essential Drivers get loaded.

---

### Post by swudee on 2007-05-23
Hi

Make sure you have enabled USB legacy or dos support option in your bios, whatever your motherboard calls it. I had similar problems installing OS's with a USB keyboard until I realized;) The keyboard should work to get into Bios with the del or F2 key or whatever your motherboard uses to get into the bios, but wont work in the boot loader!

---

### Post by cbeckwith on 2007-05-23
Hey so this time it did work... I had my usb keyboard plugged in and it worked, I dont know why.

Although after reading your post swudee I was pressing delete a lot before hand that time maybe that was it.  But thanks Ill try that for sure if i have any problems next time.

Thx

---

### Post by cbeckwith on 2007-05-24
So that didnt work cause today when i booted up i could not get into windows and pressing delete did nothing. :(

---

### Post by cbeckwith on 2007-05-25
Is there a way to stop Ubuntu from unloading drivers for the keyboard because after I get pasted GNU GRUB screen and ubuntu starts loading as soon as it says Loading essential drivers my keyboard works.?

---

### Post by swudee on 2007-05-25
Hi 

Just pressing the Delete key during boot isn't what I meant. That is only to get you into the computer Bios screen before it goes to the boot loader. When you get into to the bios, where you can make changes to the boot order of the drives, eg boot from floppy first CD rom second and Hard Drive 3rd, set system clock etc. You should find somewhere to enable legacy/dos support for USB devices. Some mother board Bios use other keys to enter the bios, Del is probably the most common, but F2 is used quite a bit as well. If you have the manual for your machine it should be in there, otherwise try to download it from the manufacturer, try Google or some manuals are available from [http://www.motherboards.org](http://www.motherboards.org) the link is right at the bottom of the page. If you can't find a manual post the details of your machine and I will try to locate a manual for you.

---

