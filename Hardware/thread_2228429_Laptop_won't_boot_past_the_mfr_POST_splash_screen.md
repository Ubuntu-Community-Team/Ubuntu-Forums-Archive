---
title: "Laptop won't boot past the mfr POST splash screen"
date: 2014-06-07
forum: Hardware
---

### Post by Dragonbite on 2014-06-07
I recently received a Compaq Presario CQ56 laptop with an Intel dual core T4400 motherboard which has Windows 7 installed in a primary partition and most of the disk partitioned in an extended partition. I tried a couple Live USBs (openSUSE (Gnome), Fedora (KDE) and Ubuntu) which worked fine.

Last night I installed Linux with 4 separate partitions in the extended drive; <swap>,/boot, / & /home. I installed it from a LiveUSB session and did not see any errors. I set up the /boot partition and in the last screen I enabled booting from /boot instead of the MBR.

When I rebooted, the system comes up to the Compaq splash screen, where it tells you to hit ESC for the options.

And that's it. It doesn't do anything whether I hit ESC or leave it to finish; doesn't boot, doesn't go into options, nothing.

After removing the battery and reinserting it and striking F8 quickly when the screen comes up (F8 is the option for choosing boot-up location, which you see after you hit the ESC key) the text message changes to the Select boot device message (or something similar) but nothing happens.

I haven't tried opening it up and either removing & replacing the CMOS battery, check the hard drive seating or seeing if there is a jumper switch yet.

In the past when the boot or hard drive is in a state that it won't boot, I can at least be able to boot from a Live session USB or CD/DVD but in this case I am not getting that far.

Other than the already mentioned actions I plan to take (when I get a block to do it, so I am not rushed), do you have any suggestions on what could be the cause or how to fix it?

---

### Post by Dragonbite on 2014-06-07
Ok, I found out it was the hard drive had died. Once I unplugged it and booted up the BIOS was responsive again.

---

