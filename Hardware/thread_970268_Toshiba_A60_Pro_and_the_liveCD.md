---
title: "Toshiba A60 Pro and the liveCD"
date: 2008-11-04
forum: Hardware
---

### Post by UbuntuKhan on 2008-11-04
I have a Toshiba A60 Pro Laptop with ATI graphics (X7000 I believe) P4 3 Ghz 1,256 GB RAM. I was excited when I heard that 8.10 was out and decided to test the liveCD. At first I had no luck (the liveCD freezing as I saw a weird splash screen). In Qemu I could see the GUI in minimal graphics mode. I thought it was the graphics card but now I am not sure anymore. I succeded booting with "acpi=off nolapic noapic" options or "irqpoll" option. I still get the weird splash screen (one time the moving orange bar was replicated 3 times over the screen, on another time Ubuntu name was divided horizontally in two) but it runs ok. Does anyone knows **why** do I have to use those options? How can I integrate those options in the iso image? Thanks
And I think that someone coming from windows doesn't know about those options.

---

### Post by MeanEYE on 2008-11-04
Hey there...

First the most stupid question, on which medium did you burn your ISO, if you burned it on CD, try burning it on DVD... I had similar problem with booting and was solved solely by writing image on DVD.

You might try starting liveCD in safe graphics mode. If your laptop has nVidia or ATI he'll need restricted drivers to work with its full potential. Also if I recall correctly there should be an option for laptops with buggy display (see HELP from liveCD boot menu). Try experimenting with that too...

No need for adding those command to image. You can (before booting from liveCD) type them on your own or after installig add them to /boot/grub/menu.lst so they are automatically applied.

Hope this helps, if not, please provide some screenshots or more details... :)

GL!

---

### Post by UbuntuKhan on 2008-11-04
I burned the iso image on a CD. My Matshita DVD-Ram is not very reliable with DVD's so I don't think that's an option for me. My graphics card is ATI X7000, but until this version of Ubuntu I had no problems with liveCD's. You told me: "You can (before booting from liveCD) type them on your own..", but that's what I did and already succeded. I was interested in getting them permanently on the liveCD. Maybe it will work on a broader range of sistems. I am also curious about the weird splash. I will post pictures later.

---

### Post by UbuntuKhan on 2008-11-04
I just found out that irqpoll option by itself is not reliable so I booted with acpi=off noapic nolapic irqpoll although I do not know what they are for. Now look at my splash screen:

PS: I found out that my Nikon L16 is not detected by the liveCD

---

