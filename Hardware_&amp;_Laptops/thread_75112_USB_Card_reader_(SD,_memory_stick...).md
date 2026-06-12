---
title: "USB Card reader (SD, memory stick...)"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by bdash on 2005-10-13
Hello. I have a card reader in my machine. It is internal, but USB (I plugged it myself). There are basically 2 ports, one for CF/Microdrive and one for SD/Memorystick/MMS.

It used to work with Gentoo as a mass storage device: I plug and thanks to HAL it is automounted and I can see it in Nautilus "computer".

On Breezy, it doesn't work. It seems like nothing happen. No automount, no devices created in /dev... My audio player (mass storage) as well as usb keys work fine.

Where can I investigate to see the problem?

---

### Post by bdash on 2005-10-14
Sorry to bump the topic.

Is there any command I can try to check the status of HAL devices?

---

### Post by aran384 on 2005-10-14
ive got a 13 in 1 card reader that i would like to know if its supported on breezy cause atm its just sat on my desk doing nothing... 

only cost my a £5 but i would like to be using ... i didnt on my other comp because it take up the 2 front usbs .... where there plug in the motherboard that is....

---

### Post by endangst on 2006-01-09
> Hello. I have a card reader in my machine. It is internal, but USB (I plugged it myself). There are basically 2 ports, one for CF/Microdrive and one for SD/Memorystick/MMS.

It used to work with Gentoo as a mass storage device: I plug and thanks to HAL it is automounted and I can see it in Nautilus "computer".

On Breezy, it doesn't work. It seems like nothing happen. No automount, no devices created in /dev... My audio player (mass storage) as well as usb keys work fine.

Where can I investigate to see the problem?

I have the same exact problem with my Win-Star USB card reader (external using USB for power).  It once showed up in Device Manager as a card reader (C-media), but now it doesn't.

Even when it was recognised, it is not mounted, because no icon for it shows up in "Computer".

Furthermore, when I put my xD picture card into my card reader, nothing happens.

Works just fine in Windows.  If M$ can make it work, why shouldn't it work in Linux?  

I did hear this is a bug (USB devices not being automounted) and it won't be fixed until Dapper is released because if they fix it now it could break other things.

I connect to the internet by cell phone and that is connected to my computer by USB cable.  No problems there.  I'm quite confused and this is the only reason that I keep my system dual-booting (so I can transfer my photos from my Fuji digital camera to the computer via my card reader and then burn it to CD).

If this is fixed, then goodbye Windows.

Here is the hal output... I was told to report that, but have no idea what it is.
Also, nothing shows up in /etc/sda*... that's where the card reader should be but that's empty.

endangst@ubuntu:~$ groups hal
hal : hal cdrom floppy plugdev

---

### Post by cweekly on 2006-02-19
hey endangst
same issue, have internal "mtg cr-in212xu-1" 12in1 card reader (which internally is usb) and can't get it to be recognized. not even 100% sure it's getting power (dmesg and tail -f /var/log/messages don't seem to notice when I stick a cf card in it). up to date breezy and other packages (amd64)....
good luck. (shrug)

---

### Post by Mr Fat Bat on 2006-05-10
Same here, I have an internal reader and my /var/log/messages doesn't show anything when I stick in an xD card!

It's just that to go and my Dell 6400 is all set up and I can get on with breaking it =)

---

