---
title: "ubuntu 7.10 killed my laptop"
date: 2008-08-31
forum: Hardware
---

### Post by figg on 2008-08-31
hi,

new poster here. unhappy with vista on my laptop, about a month ago i bought one of those intro to linux ubuntu books with a free boot CD, version 7.04. i installed it and started using it all fine (minus one or two compatibility issues which were on my to-do list like sound & onboard wireless). then recently it advised me to upgrade to 7.10 and i did so, and the installation went okay, but on the final system reboot the loading screen (the one with the horizontal bar filling up with orange) it stopped completely. i had to cut the power, and now my laptop is completely non-responsive. the computer is only a year old, so i was wondering if this is a problem that other people have had, and if so whether there is anything i can do about it.

any comments would be much appreciated

figg

---

### Post by pfdevil on 2008-08-31
Do you mean unresponsive in the way that it won't power up? Load Bios? Try booting from your cd.

---

### Post by figg on 2008-08-31
sorry, should have put more detail. the screen turns on, that is to say that there is definitely power going into it, but it is showing a purely black screen. it doesn't even show me the laptop startup screen (gateway in my case) with the option to push f10 for the menus. this is the same whether or not the boot CD is inserted. i have tried it with another screen and it is the same.

---

### Post by GepettoBR on 2008-08-31
If it is the same with the boot CD, that probably means you aren't even loading into the BIOS. This is serious. Then again, maybe not. Can you make a boot floppy on another computer (assuming your laptop has a floppy drive, which is less and less common nowadays)? If so, Download the Super GRUB Floppy from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and try turning on the computer with the floppy disk inserted. If it doesn't work, then it's a BIOS problem and I don't know how to help you. If it does work, we'll go from there and try to repair your installation.

---

### Post by figg on 2008-08-31
no floppy drive, i'm afraid.

---

### Post by GepettoBR on 2008-08-31
This is hard to diagnose then. Does _nothing_ at all appear on your screen? Not even the GRUB menu or BIOS loading?

---

### Post by figg on 2008-08-31
yeah that's what i'm trying to say, absolutely nothing at all. the last thing it ever showed was the ubuntu loading screen, which froze on me, and since i cut the power it's gone. it's not the end of the world if you tell it's gone forever because it wasn't my primary computer, but i'd just like to know if there's a possibility it could be, y'know, ressurected.

---

### Post by GepettoBR on 2008-08-31
Well, if not even the BIOS screen is loading and you've confirmed that it's not just the monitor then this installation problem has somehow managed to screw up your motherboard. I'm sorry I can't help out more, but the only advice I can give you is to take the computer to a repair shop and see if they can do something.

---

### Post by Daveski on 2008-08-31
Any chance the machine has not powered off properly? Try removing the battery and the mains power for 10 minutes or so. Put them back and try to power it on.

---

### Post by pfdevil on 2008-08-31
Hey well I guess its time for a hardware troubleshoot. 

Lets say it isn't the end of the world and the bios isn't shot.

1. It could be blown RAM, does your laptop beep when you turn it on.
2. Or remove the RAM and turn on your laptop does it beep now?

If not maybe this could be a blown motherboard.

3. Do any fans spin up? (Just to indicate if power is present?)
4. Last but not least, browse the manufacturers website and search for a "hard reset" of the bios. This is typically configuring some sort of jumper.

Also how long did you wait at the load screen. Usually if something goes wrong, meaning ubuntu is struggling with something, it seems that there is a hang. Then Alt+F2 would have helped you to see what's going on there.

I hope you can get things working again.

---

### Post by figg on 2008-08-31
thank you all for your comments and suggestions, i've sorted it now. i removed the battery for 5 minutes and then re-connected, then immediately booted the CD and reinstalled ubuntu, no problems so far!

well done Daveski, you've helped me out a great deal mate

---

### Post by Daveski on 2008-08-31
No problem - glad to help, and even more glad that your machine is OK. Don't forget to mark this thread as solved from the Thread Tools menu.

---

