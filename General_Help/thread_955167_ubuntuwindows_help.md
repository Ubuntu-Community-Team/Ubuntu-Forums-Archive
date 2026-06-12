---
title: "ubuntu/windows help"
date: 2008-10-21
forum: General Help
---

### Post by deviator on 2008-10-21
hi, i recently installed ubuntu on my compaq presario SR5490AN. 
it had vista running.
 i now have a working ubuntu box but every time i try to stick a windows xp/vista/98 cd in i keep getting a blue screen and white writing. 
the cd simply doesn't boot up. any ideas? 

i want to get dual boot but cant seem to wipe my HDD clean of ubuntu, and it seems ubuntu is stopping me from installing windows.
:(:confused::guitar:

---

### Post by estyles on 2008-10-21
You said it already had Vista running...  Did you uninstall Vista for some reason?  The best way of making a dual-boot system is to install Windows first (or have it already installed), and then install Ubuntu.

When you say "blue screen with white writing", what kind of white writing?  Is it a "blue screen of death" that you often get in Windows?  Because you ONLY get those in Windows.  Neither Ubuntu nor any sort of pre-OS startup will give you the same blue screen that you get in Windows.  If it's some other "blue screen with white writing", then you have to tell us what the writing says.

When you say you put the Vista CD in, when are you putting it in?  Describe the process.  To boot from the CD, you would put the CD in, then restart the computer - at some point, it should say "Booting from CD", unless your BIOS is not set to boot from CD, and then it should start installing Windows.  If you reinstall Windows after you already have Ubuntu installed, and you actually want a dual-boot system, you'll have to reinstall Grub, because Windows overwrites the master boot record when it installs.

---

### Post by deviator on 2008-10-22
the windows cd finished copying the files.
it attempts to boot into the installation menu and crashes with a blue screen reading:"the program has enoucntered problems and has shut down"

blah blah blah

technical information: stop x80000000 blah blah blah.

:lolflag:

p.s i uninstalled vista because i wasnt happy with it.

i have two hard drives.

---

### Post by deviator on 2008-10-22
Halp???

---

### Post by /////// on 2008-10-22
Try unplugging both your hdds and boot the windows cd then after it passes the point (if it passes) which you were stuck on before, immediately plug the sata/ide plug back into the hard drives

---

### Post by deviator on 2008-10-22
are you sure? while the computer is running?

doesn't sound very safe for the HDD's.

:confused:

---

### Post by /////// on 2008-10-22
Uhh yea just be careful not to touch anything else if you don't know what you're doing

---

### Post by estyles on 2008-10-22
Ugh... I know SATA is hot swappable, but that doesn't sound advisable nor helpful.  I would not follow that advice.

What I would do is boot up a LiveCD and open GParted.  Make sure there is an empty Primary Partition available to install Vista onto.  See if that helps.  Search on GParted for more info.

---

### Post by /////// on 2008-10-22
Well I assume its something in one of your HDDs preventing Vista from loading so to check this theory just do what I said then when your actually in the setup, if it cannot read any of the disks then theres a problem with it. This would see if it was a problem from your hdds or your other hardware. There was a time when the XP cd just would'nt even boot up for me and I used this method to boot into the setup and was actually able to install XP like this

---

### Post by deviator on 2008-10-24
disconnected both hard drives...did exactly the same thing.

HALP!


it just doesnt wanna load windows :(

---

### Post by deviator on 2008-10-24
bump

anybody have any ideas?

i have tried everything except taking out the motherboard battery :mad:

---

### Post by estyles on 2008-10-24
> **deviator said:**
> bump

anybody have any ideas?

i have tried everything except taking out the motherboard battery :mad:

Are you trying to install onto a primary or logical partition, is it the same drive as Ubuntu or a different one?

The only things I can think of that would be causing your problem are: 1) installing onto a logical partition (I don't even know if it's possible to try it or not, nor whether it would cause this problem or not - just a thought), 2) bad hard drive, 3) bad installation CD.

Can't think of any other reason to die on installation like that.

---

### Post by deviator on 2008-10-25
everything is new so im not sure about the hardware. it could possibly be the cd but then again i tried various version and copies of windows.

when i get to the bottom of it i will let you know.


then again if anybody knows....:lolflag:

---

