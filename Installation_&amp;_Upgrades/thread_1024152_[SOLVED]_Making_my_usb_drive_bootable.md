---
title: "[SOLVED] Making my usb drive bootable?"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by zahrtman2006 on 2008-12-28
Hello, i have recently installed Ubuntu 8.10 onto a usb flashdrive, however when i went to change bios settings the flash dirve could not be booted. Is there a way i can make my computer be able to boot from a flash drive. But not screwing my computer up? IN other words can i make it to where it is possible to boot from the flash drive but also still be able to boot into windows when the flash is not plugged in?

Thanks for anything.

Update: For clarification, booting from a usb drive is not an option in the bios.

---

### Post by utnubuuser on 2008-12-28
Hi -- suppose you tried F12 at start-up?  This, (sometimes it's another Fxx key), should bring up a boot device list.
Mostly only the newer computers will boot from USB-flash.
I came across a how-to some time ago, showing how to boot from flash regardless of BIOS.  Couldn't tell ya where though,  it was just some posting somewhere that I arrived at by googling "boot from usb".

---

### Post by zahrtman2006 on 2008-12-28
Ok, i am running a newer computer i will try f12. It wont mess up the computer will it?

(the reason i am so careful is becuase it is not the first time i have crashed a computer lol, and i dont wanna lose data!)

---

### Post by zahrtman2006 on 2008-12-29
Ok i did some "exploring" and i found that my usb drive is in the Hard drive submenu of the boot priority menu. Would it be safe to set my USB for first boot over my hard drive?

---

### Post by Lightstar on 2008-12-29
Yeah one of my drives has the same problem, it's detected as a hard drive instead of removable media..   I haven't really bothered testing it... if we make it the first HDD to boot.. then what happens when it's not plugged in?  no boot?  I don't want to have to edit the bios everytime.

I'll try it later, you can too, the worst that could happen is having to re-order the boot in the bios a second time.  Just write down the current order.

---

### Post by zahrtman2006 on 2008-12-29
I have played with it a little. And yes it will just revert to your original hard drive much like the priginal boot priority works. However when i tried it the it said no operating system found (ubuntu wasnt installed correctly i guess, although i installed it by the "make usb startup disk" option). So i booted into windows and formatted the drive, and re made the startup disk using ubuntu again. This time instead of getting an error message saying no operating system the computer just by passes to the original HDD.

Any suggestions?

---

### Post by logos34 on 2008-12-29
you could always try making the bootable live usb with [Unetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by zahrtman2006 on 2008-12-29
That looks like it does the same thing as Ubuntu does in the adminstrator menu of the OS.

And do you have to have the usb in a certain drive for it to be made bottable and firther more for your computer to boot or can it be in any usb drive?

---

### Post by zahrtman2006 on 2008-12-29
OK i am on my usb linux OS so it worked thanks everyone that had a say!

---

