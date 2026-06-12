---
title: "Trying to clear CMOS made system unusable.  HEEELP!"
date: 2019-02-17
forum: Hardware
---

### Post by x1a4 on 2019-02-17
Hello.

I had the password set to enter BIOS on my desktop.  I forgot what it was and lost the notebook where it was written down.  I tried to clear CMOS and the system became un-bootable.  It's now asking for the password at boot.  I used to be able to boot, now I can't do anything.  

First I put a jumper cap on the CLR_CMOS pins on the motherboard for about 10 minutes and that's when the trouble started.  I did it again for much longer to no avail.  
Then I unplugged the power to the board.  I removed the CMOS battery.  I did it all simultaneously for over 24 hours and keep being asked for a password on boot.  
I, of course, unplugged the system power also.  

The board is a Gigabyte GA-F2A88X-D3HP ATX motherboard with an AMD A8-7600 APU.

Thank you.

---

### Post by Frogs Hair on 2019-02-17
Unfortunately not every bois can be reset by removing the cmos battery. Newer or more secure mother boards will block this action. You may have to contact whoever wrote the bios software. I researched this two days ago while contemplating setting up a bios password.

---

### Post by x1a4 on 2019-02-17
Nevermind.  This was an issue with the fan controller.  I removed it and all is well.

---

