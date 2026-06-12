---
title: "HP Pavilion TX 1000"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by chejose on 2007-05-28
I recently bought a Pavilion TX 1000, with the expectation of installing Ubuntu on it.

I can boot from the Ubuntu 7 CD, but well along in the setup the comuter freezes, and the only way I can get out of it is to disconnect the battery.

The CD works with no problems on my desktop machine.

At this stage I have no idea how to procede, so hope one of you can help.

Thanks

José

---

### Post by necrolin on 2007-06-04
Why don't you run a search for tx1000 on this forum. There are lots of answers out there.:KS

I have this same computer and did this:

To boot: when you're about to boot add: **noapic nolapic** to the boot arguements otherwise it will not boot, later add this to grub so that you can boot the system.

Then install and follow these directions to get sound and networking to work:

[http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000)

---

### Post by farbird on 2007-06-06
some install help here for detecting hardware

[http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000)

---

### Post by creatureofthedark on 2007-07-16
umm sorry to be a noob but how do u do that "noapic nolapic" bit??? im very new to this hole booting problem thing with linux normaly it just works :P

---

### Post by Cuppa-Chino on 2007-07-24
Quick guide (from memory so please excuse any errors)

When Grub (the boot manager) loads up and you have the selection screen select the kernel you want to boot (most likely the one on top)

 -- but maybe a good idea to press the arrow keys to stop the count down and to give yourself more time to read the entire grub menu screen, it has some instruction at the bottom on how to edit things but these are not necessarily self evident-- 

as said select the line you want to boot then press e to edit boot options for the highlighted kernel

then select the line with linux kernel 2.6.etc etc and press e (to edit this line) and scroll to then end, there type in the commands from above and then press enter

Then hit b to boot…

If the parameters work for you you might want to add them to your grub menu automatically, to do that when the system has booted up type
Sudo gedit /boot/grub/menu.lst

You will get a long text file, in this text file towards the bottom you will again find the linux kernel line here add the parameters just as above, save and now they are automatically used.

---

