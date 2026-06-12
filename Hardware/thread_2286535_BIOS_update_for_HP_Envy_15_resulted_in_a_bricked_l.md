---
title: "BIOS update for HP Envy 15 resulted in a bricked laptop"
date: 2015-07-13
forum: Hardware
---

### Post by alikazmi-2040 on 2015-07-13
Hi

With my HP Envy 15 laptop, resume from hibernate resulted in a kerneloops 8 times out of 10 and after trying almost all other options (swsusp, uswsusp, tuxonice, setting kernel boot parameters through grub, changing settings in config files, adding various quirks etc), I decided to flash the latest BIOS update available for my laptop model from the HP support site (which was obviously a windows exe, thanks a lot HP). The exe created a USB drive with the bios update and some other tools (mem check etc in uefi mode). The installation of the BIOS update completed and i was told that upon reboot, it might take a couple minutes with some blinking leds before the display became active but after waiting around half an hour, since nothing was happening (except for the fan spinning), i restarted the laptop manually.

Since then, i haven't been able to get to BIOS post. The laptop just sits there with the fan spinning, the WiFi led in the off state and the display completely off, the caps lock led cycles once (which is normal behaviour as far as i remember) and the hdd led blinks a couple times and then turns off. The original BIOS was Insyde F.1C and the update version was F.65. The laptop is out of warranty as far as HP is concerned although i have an extended warranty (of sorts) from the local store i bought the laptop from but i only want to use that potion as an absolute last resort.

- I have tried connecting an external monitor which didn't do anything.
- I have tried taking the battery out, holding down the power key for 15 to 60 seconds with the power adaptor disconnected and rebooting.
- I have powered the laptop on while pressing Win+B with the HP_TOOLS USB in various ports.

I would greatly appreciate any help in trying to resolve this problem, thanks in advance.

---

### Post by Bucky Ball on 2015-07-13
Have you tried creating another BIOS flash USB on another laptop, and flashing it again? 

This doesn't have anything to do with Ubuntu, so wondering if you may have better luck posting on the [HP Forums]("http://h30434.www3.hp.com/") as well. Good luck.

(PS: [Here's]("http://h30434.www3.hp.com/t5/forums/searchpage/tab/message?allow_punctuation=true&filter=labels&q=flash+bios") a start. Maybe something was amiss with the USB you created. Maybe even [this]("http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/HP-DV4-1225DX-bios-flashing-without-an-operating-system/m-p/292089/highlight/true#M11802") might help.)

---

### Post by alikazmi-2040 on 2015-07-13
I know it's not Ubuntu related but i am slightly desperate &#128534; and since most people here know their way around computers, i thought someone might've had solved a similar issue at some point &#128517;.

With HP support forums, I've already spent a couple hours reading various posts and all of them are filled with the above mentioned suggestions with the end result (in case of the issue not being resolved) being someone suggesting sending the laptop off to HP. Personally, i almost never get a response at all so wasn't sure if there was any point in even posting there and since i don't have a HP warranty anyway, I don't think i can send the laptop off to HP &#128553;.

Thanks anyway, I'm going to try using a secondary laptop to put the bios bin files in the root of a USB drive and see if that does anything because i can't really use HP bios recovery tools without the display.

---

