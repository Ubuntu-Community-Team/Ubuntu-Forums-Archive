---
title: "Can't select OS in Grub"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by Ashrin on 2009-09-01
Please excuse me if this is a simple question. I'm new to Ubuntu (and linux in general) and recently installed it onto my Win XP machine as a dual boot.

However, when grub boots on my computer, I cannot select the OS. More specifically, I see the text based grub screen and cannot arrow down to select any OS. In fact the entire keyboard seems to be unresponsive, I can't press enter to speed though the screen, I can't enter into the grub settings.

I've tried reinstalling Grub from the live CD. While the install and reset seem to have taken place without a problem, they did not resolve the issue.

Although I believe it to be a separate issue: I did (since the ubuntu instal) have to reset the motherboards settings due to a power problem. Problem was present before and persistent after the reset.

While I've been liking Ubuntu, I need XP for a few programs. Thanks in advance for any help you can provide.

---

### Post by mrgnash on 2009-09-01
What type of keyboard are you using? If it is a USB keyboard, there are a couple of things you could try:

Try powering down the computer and disconnecting the power cable for awhile.

Check your BIOS settings as to whether the OS or the BIOS should "control" the keyboard. Whatever it's set to, change it to the alternative ;)

---

### Post by Ashrin on 2009-09-01
mrgnash,

Thanks so much, worked like a charm!


For anyone else that has this problem and has found this thread:

Boot to the Bios 
Change the peripheral integration for usb keyboard to be controlled by Bios
Reboot

---

