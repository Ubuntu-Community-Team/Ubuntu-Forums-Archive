---
title: "Installed ubuntu on external.... don't want grub....."
date: 2008-08-08
forum: General Help
---

### Post by Tim4rd2000 on 2008-08-08
Ok so I installed ubuntu on an external hard drive and intended to boot from it just by selecting hard drive from the boot menu when I press F8 otherwise I want to go straight into vista... So now I have ubuntu on the external but can't boot into windows because grub isnt there when my external isnt plugged in.

So this is what I would like to do:

Have windows boot without going through grub as default.
Have ubuntu on my external to boot onto when I want 

How can  I do this...

---

### Post by Thyssenkrupp on 2008-08-08
cant you use your bios to select the boot sequence as:

External HDD
HDD
CD/DVD-ROM

?

that should work.

---

### Post by Tim4rd2000 on 2008-08-08
I have it set at that but for some reason the computer has something on it to make it think grub is local when its blatently not.

So my windows hard drive thinks it has grub but of course when the hdd isnt in it doesnt so I have no access to it at all.

Is there a way I can fix mbr from within windows itself. 

I can still boot into both os's

---

### Post by Thyssenkrupp on 2008-08-08
im not exactly great at these things, but somewhere in control panel it says something along the lines of 

'make windows check for other operating systems upon system start'

if you enable that then you would have the option of which OS to boot into,

or would that not solve the problem?

---

### Post by Tim Sharitt on 2008-08-08
If you have your windows cd, you should be able to boot it and run fixmbr from the recovery console.

---

### Post by Sycron on 2008-08-08
If you don't have windows CD, you may use supergrub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Rebelli0us on 2008-08-08
fixboot fixmbr will restore Windows' boot. Then you can boot linux from BIOS exactly as you described.

---

### Post by ZeldaFan on 2008-08-08
But wouldn't the OP still need grub to boot Ubuntu from the external hard drive, even though FIXMBR would let him boot back into windows? What I would do is still fix the MBR using one of the aforementioned methods and if you still can, reinstall ubuntu on your external hard drive, but this time disconnecting your internal hard drive before booting into the LiveCD. This way, grub will automatically install onto the external hard drive and will only show up when you have the external hard drive connected. The reason the you (the OP) have this problem in the first place is because you forgot to disconnect the external hard drive upon installing, which allowed the GRUB configuration to be installed on the internal hard drive instead and subsequently screw things up. That's the way I once set up my laptop and it worked flawlessly.

---

