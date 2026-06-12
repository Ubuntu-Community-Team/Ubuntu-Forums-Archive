---
title: "Upgrade to UNE Lucid gone bad on eee pc 1005PE"
date: 2010-05-02
forum: Hardware
---

### Post by lbravo on 2010-05-02
I upgraded (or attempted to) my 9.10 perfectly stable install on my eee pc 1005PE to 10.04 and all has gone awry. It seems to boot into 10.04, but now get a blinking screen (every four seconds, the screen blinks - unusual). I can't seem to boot from a USB to start all over again... in fact, I can't get the my little notebook to start with the standard start up screen -- it goes straight to grub, and only gives me options to boot into the broken 10.04. I don't know why this is... I've removed direct power and battery, and tried to reboot, but it won't reboot starting with the bios - it just goes straight to grub. I'm feelin' really stupid right now... missing something.

Also, if I try to create a new startup USB, on a different system running desktop 9.10, the "Make Startup Disk" utility tells me I need to format the USB -- fine (I've tried two different manufacturers) -- and it does nothing. I'm totally stymied and I want my eee pc back... dang it!

If anyone has clues on what I should do, PLEASE respond, I'll consider you a rock star!

Huge Advance THANK YOU's for any clues you can provide.

Lori

---

### Post by FishFoot on 2010-05-03
Hey Lori,

I can tell you that if you tap on "f2" as the machine is starting it should get you into the BIOS.  I had some problems with this recently on a Windows 7 eee PC that I was trying to install Lucid on.

Just keep hitting F2 and you'll get the BIOS.

As for making the USB disk, make sure that you have root permissions when you launch the disk maker utility.

If you're in Ubuntu you can run it by pressing "Alt F2" then entering 

 gksudo usb-creator-gtk

or from a command line

 sudo usb-creator

I banged my head against that one for a bit as well.

Good luck
FishFoot

---

