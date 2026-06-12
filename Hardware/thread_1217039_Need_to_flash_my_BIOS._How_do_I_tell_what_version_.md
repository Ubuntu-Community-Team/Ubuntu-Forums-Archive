---
title: "Need to flash my BIOS. How do I tell what version to use?"
date: 2009-07-19
forum: Hardware
---

### Post by anthony62490 on 2009-07-19
I really need to learn when to leave well enough alone. I think I got myself into a mess of troubles. 

My current CPU is OLD and does not support SSE (for OpenGL gaming, I believe), so I tried to swap it with a newer CPU. It was at this point that I discovered that AMD and Intel are NOT interchangeable. 
So I put the old CPU back in and flipped it on. GRUB loaded up and I tried to boot under Ubuntu. All I can remember seeing is the phrases "**cannot load kernel**" and "**oops**". I flipped it off and back on. 
This time, GRUB did not load. I received "**GRUB error 15.**" This tells me that I need to reinstall GRUB. Only now my live CD won't boot. I get the message, "**Cannot boot from this disk. Try a BIOS update.**" Joy. 

My motherboard is a "Gigabyte GA-7VKML - Rev1.1". I checked Gigabyte's website for a BIOS image and I came up with this page:
[http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1306]("http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1306")
The thing is, I'm not sure which version to download. Flashing the BIOS is supposed to be a touchy process, so I'd rather not screw this up. The BIOS chip itself isn't too wordy, but it does say this:
> 686
AMIBIOS
(c) 1999
GG44
2547 (this was stamped on the bottom, not printed)
Any help here would be GREATLY appreciated.

---

### Post by Malta paul on 2009-07-19
Yes you have to be very careful flashing your BIOS you must also get the correct Bios for your motherboard.(I've done it about four times)
If I were you though, I would _first_ just try to set up your existing Bios settings. To excess the Bios, bootup and press Delete or F1 (depending on your Bios make) If you are not sure what to do, use the the default setting. Then set the boot order to CD (first) your HD second. F10 to save the settings. Put in you live Ubuntu CD and reboot.

Hope this is of help :)

---

### Post by oxf on 2009-07-19
> **anthony62490 said:**
> I really need to learn when to leave well enough alone. I think I got myself into a mess of troubles. 

My current CPU is OLD and does not support SSE (for OpenGL gaming, I believe), so I tried to swap it with a newer CPU. It was at this point that I discovered that AMD and Intel are NOT interchangeable. 
So I put the old CPU back in and flipped it on. GRUB loaded up and I tried to boot under Ubuntu. All I can remember seeing is the phrases "**cannot load kernel**" and "**oops**". I flipped it off and back on. 
This time, GRUB did not load. I received "**GRUB error 15.**" This tells me that I need to reinstall GRUB. Only now my live CD won't boot. I get the message, "**Cannot boot from this disk. Try a BIOS update.**" Joy. 

My motherboard is a "Gigabyte GA-7VKML - Rev1.1". I checked Gigabyte's website for a BIOS image and I came up with this page:
[http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1306](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1306)
The thing is, I'm not sure which version to download. Flashing the BIOS is supposed to be a touchy process, so I'd rather not screw this up. The BIOS chip itself isn't too wordy, but it does say this:

Any help here would be GREATLY appreciated.

I would say at this point you dont need to flash your bios if you've not upgraded anything else. 

As Malta Paul says first try and re set your existing ones. Beside F1/Del it could also be ESC like on my system or one of the other F keys, F10/F12 are common.. Then live cD ir a clean install. Let us know what happens.

On the wider subject of Bios flashing that info should be displayed in the the BIOS setup. Not what you need to do now but an update is fairly safe if you are carefull get the correct one. My PC manufacturer had it for download on the website

---

### Post by anthony62490 on 2009-07-19
Maybe you're right. I may not need to touch my BIOS. It has stopped telling me to flash my BIOS and has started behaving very strangely. I don't like using the word "erratic," but I have to. It starts up with a wide variety of effects and flavors, none of them pleasing. 

> When the Live CD is in, it:
-Loads up the boot menu and shows me my choices. (none of them ever work)
-Loads up the boot menu and immediately freezes
-Loads the logo of the boot menu and nothing else
-Tries to load the boot menu, but ends up hard resetting the machine.
> 
When the Live CD is NOT in:
-GRUB loads up and when I select my kernel, it sends me a kernel panic.
-GRUB loads up and I proceed to log in normally. Halfway through the startup sound effect, the machine freezes/resets.
-GRUB sends me "Error 15"
-occasionally, GRUB doesn't load at all. Instead, it skips GRUB entirely and shows me a screen with a circular blue gradient.

On one of the occasions where I could log in, I tried to start a failsafe GNOME session. It proceeded to load my desktop picture and immediately freeze. Not sure if it's worth mentioning, but at this point, my CAPS and SCROLL lock lights were flashing.

I'm not so sure that my BIOS really needs to be flashed anymore. Anyone know how I can change the thread title?

---

### Post by anthony62490 on 2009-07-23
bump

---

