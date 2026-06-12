---
title: "What have I done?"
date: 2009-07-26
forum: Hardware
---

### Post by enragedpirhana on 2009-07-26
I used the standard i386 ubuntu 9.04 cd (downloaded) to install ubuntu onto a flash drive using a laptop.
The disc loaded grub onto the laptop hdd and since then, windows won't boot on that laptop.
The hdd is fine, I've used it through a desktop pc, and everything works.
Ive removed grub using a suber grub boot disc, but windows still won't load.
It loads it's own multiboot interface, then it gets to the logo screen (with the blue bars on xp professional) then it gives me a message saying "windows has been shutdown to protect your hardware. please use chkdsk and remove any new hdds."
 
I'm asking here because ubuntu was the only change I've made to the system.

---

### Post by philcamlin on 2009-07-26
you got a bsod

boot into the xp disk and do chkdsk /r

then reboot 

booot into live cd and reinstall grub

---

### Post by enragedpirhana on 2009-07-26
I don't want to reinstall grub, as it's a borrowed laptop.
I've tried chkdsk /r and it says it fixed 1 or more errors, but it still doesn't work.
It will BSOD on the laptop, but not a desktop.
Even the windows disk BSODs on the laptop.
And yes, it's the same message each time.

---

### Post by lisati on 2009-07-26
Random thought: if the HDD belongs to the laptop and it has a recovery partition, there might be options that will make using the recovery partition work better than a Windows CD/DVD, e.g. non-destructive restore.

---

### Post by enragedpirhana on 2009-07-26
Probably, But like I said, it's a borrowed laptop and I don't have any of the disks.
I broke the terms of use by even putting the linux disc in the machine.
And I'm not allowed to know the admin password.
Bureaucracy.

---

### Post by Yanatsu on 2009-07-26
No, as in, most laptops these days, the companies don't want to pay the 10 cents it costs to have a restore disc. It's normally a hard drive partition, you should be able to access it if you look at the boot options.
But if it's older (+5 years), or made by a company that doesn't suck (Toshiba still gives discs, I think), you're screwed.

---

### Post by enragedpirhana on 2009-07-26
It doesn't seem to be accessible. The only option I see that seems remotely related is enabling/disabling d2d backup.
 
 
It's currently in a 45 second restart cycle
start>Windows started incorrectly screen>start normally after 30 seconds>blue screen>restart.
 
I've gotten rid of the windows multiboot screen, But that wasn't what was bothering me.
I've had it boot in safe mode once, but not in "normal mode".
Now, when i try safe mode it hangs on mup.sys.
Oh, and the windows disk doesn't BSOD anymore, which is nice.

---

### Post by Yanatsu on 2009-08-04
Okay, sorry for the delay, but if it's Windows XP, did you enable SATA on the laptop in the BIOS? That will screw XP up since it doesn't have the proper drivers for it.
If it's enabled, I mean. Try to disable it in the BIOS.

---

