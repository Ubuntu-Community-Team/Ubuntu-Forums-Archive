---
title: "Help me fix my roomates laptop before he kills me!!!"
date: 2009-04-30
forum: Hardware
---

### Post by Crypty on 2009-04-30
So what happened is one night a few days ago I spun around in my desk chair which bumped into his desk,a flimsy plastic TV dinner tray thing. It was supporting his mammoth 17 inch HP laptop, which he keeps only about 1/2 on the desk to give the fan more ventilation. 
So the whole thing toppled over, and there was a USB mouse plugged in. Well the USB plug hit the ground which in turn jammed in the USB port.

Just the other day I helped him upgrade to 9.04 and everything was working fine, until today, he starts his laptop and gets "operating system not found"
I didn't think this was related to me knocking it over b/c it had been working for a few days since then, but I opened up the HD compartment and it appears that when the USB port got pushed in, it hit the SATA connector on the mobo and completely messed it up separating the connector from the contacts.
There's no way I can fix this 100%, but I think I might be able to find a workaround. 
This laptop has 2 sata drives in it and he only uses one. I'm guessing the one with the messed up connector contains the OS, which is why it wont boot. I need a way to tell the machine to boot from the other sata drive so I can swap the 2 drives positions and have it working again.
Does anyone know how to do this? I already tried swapping them but I get the same message as if it's trying to boot from the drive in the position with the broken connector regardless of which HDD is in there.


Thanks a lot. Any help is appreciated.

---

### Post by Tweak42 on 2009-04-30
You can try going into the bios (usually one of the F1 - F12 keys at boot), and locate the boot drive settings.  It may or may not allow you to change to the 2nd drive.  I haven't worked with a 2 drive laptop before, but desktop boards usually have bios setting to set the physical boot drive.

---

### Post by lindsay7 on 2009-04-30
Yes. you need to change the boot priority in bios. You should have a setting in bios to start on you devices like,

1.  Cd or dvd
2. Hard drive x
3. hard drive y
4. other

sometimes the bios will look like this

1.  cd or dvd
2.  hdd
3.  other

when you choose hdd, it will give you the choice of hddx, hddy, usb drive... you set the order in which the computer will look for the os.

---

