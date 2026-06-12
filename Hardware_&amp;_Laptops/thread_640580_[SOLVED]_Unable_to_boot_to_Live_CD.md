---
title: "[SOLVED] Unable to boot to Live CD"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by dbraniff on 2007-12-14
Just started using Ubuntu the other day, went to install it in my home computer which I have hooked up to my TV through DVI and I wasnt able to get anything on the screen. My Graphics card is just a Asus Geforce 5600FX. Is it possiblbe that the resolution is causing this problem. The TV is a 32" Acer that supports up to 1080i if that helps.

Thanks

---

### Post by jbulcher on 2007-12-15
> **dbraniff said:**
> I wasnt able to get anything on the screen.

Did the computer display the BIOS boot sequence and then go blank? Is that what you mean?

---

### Post by dbraniff on 2007-12-15
It always posted (beeped) and eevrntually displayed the Windows Logon screen because of the resolution but i never did see the Bios screen or the windows Loading screen. That is why i think it has to do with resolution when I first throw in the live disc.

---

### Post by jbulcher on 2007-12-15
I missed the part where you said you were trying to display to a TV - it makes sense why you might not see anything pre-boot. Do you have a monitor handy? that might help to get Ubuntu set up initially, and then you could see if it will display to the TV.

Also, even if you don't have a regular monitor handy, you should check for computer activity to check that the computer can boot off the CD. First you have to be sure that the computer is set up to boot from CD. Then, let the computer boot with the disk in it. Give it... say...2-5 minutes, and then hit enter. If your computer is capable of running the live CD you should see disk activity at this point - the drive should spin up &/or the light will start blinking. Maybe Ubuntu will even be able to detect the display upon boot and you'll boot straight into Ubuntu!

I have had trouble with the latest version of Ubuntu booting to the live CD. Aparently there is an issue with one of the models of Dell's Optiplex where booting to the live CD will lock up the computer instead of booting - but the issue didin't affect any of the other live CD versions, so you could try a different version of Ubuntu if the disk you have doesn't work..

Good luck!

---

### Post by jbulcher on 2007-12-16
dbraniff, did you get it working? If you did, let us know what you did to get it working so others with the same problems can find the solution! (You can mark the thread solved by clicking on "Thread Tools" too!

---

### Post by dbraniff on 2007-12-16
OK so yeah I solved that problem by hooking up an actual monitor had to go out and get one. I also ran into a bunch of other problems but that was just with the bootloader for some reason grub doesnt like my system. However I am sure if I were to configure the installer to change its resolution to something the TV would enjoy it would be all well.

---

