---
title: "Comprehensive list of Boot Options as HTML"
date: 2005-11-27
forum: General Help
---

### Post by os2mac on 2005-11-27
Does anyone know where I can get a copy of a list of the boot options available at start up for the live CD?

---

### Post by aysiu on 2005-11-27
[QUOTE=os2mac]Does anyone know where I can get a copy of a list of the boot options available at start up for the live CD?[/QUOTE] I don't know about HTML, but here are some screenshots...

---

### Post by os2mac on 2005-11-28
Thanks I am thinking about writing a wiki about this.... it seems awful tedious to me to have to boot to the live disk to find the boot options... there should be a file somewhere that we can d/l that has all the options to allow us to formulate the boot command BEFORE we actually boot the machine.

---

### Post by aysiu on 2005-11-28
[QUOTE=os2mac]Thanks I am thinking about writing a wiki about this.... it seems awful tedious to me to have to boot to the live disk to find the boot options... there should be a file somewhere that we can d/l that has all the options to allow us to formulate the boot command BEFORE we actually boot the machine.[/QUOTE] Can you explain why this is necessary? The only time you'd need the boot options would be when you're actually using the CD. And when you're using the CD, you can just press the F-keys to see what the boot options are.

In any case, if you want to translate those screenshots into a little Wiki entry, go for it!

By the way, to get those, I didn't reboot. I just ran the live CD off of Qemu: ```
qemu -cdrom /dev/cdrom
``` Didn't take long at all.

---

### Post by os2mac on 2005-11-28
yes I will be happy to.... and I will give you a real life reason why I need them... I am helping a friend to try and run the liveCD on a Dell Inspiron 8000 laptop. When we boot using the default settings it goes through configuration then hangs on a black screen. I looked @ [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28laptop%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28laptop%29)

and it lists several things to try... but not the syntax of the command. It would be very handy to have a easily understandable list of all the options to try (with syntax)  on boot up rather than trying one at a time until you get it correct (having to reboot after every unsuccessful boot) make sense?

---

### Post by aysiu on 2005-11-28
Makes sense.
Go for it!

---

### Post by cannuck on 2005-11-28
I have tried running the PPC Live CD mailed from Ubuntu on a Mac G4/500 and absolutely nothing happens. Why? Put question up on forum and zip.

Also tried 86 Live CD mailed from Ubuntu on my IBM laptop. Took about three attempts to get it too install - with lot of trying something and maybe something will happen - like as lot of "enter" clicking. Now that it is installed - I get the opening window and then nothing. I previously installed Linux before on the same laptop (full install - not Live CD) - I think it was Debian. Anyway it worked fine - installed easily.

I am kind of superprised that the Ubuntu "team" would not want to make the Ubuntu OS - "Usable" - by having a Quicktime movie to explain the install on the different Os's. Or a least a "simple language" (understandable by anyone) - easy - step by step text tutorial with pictures. I can only imagine the thousands of wasted hours by various potential Users trying to install Ubuntu. The notion of relying on the forums to solve specific issues might make sense - but using forums to help on the basic install doesn't make sense to me - because the frustration of the install will force a lot of people to abandon Ubuntu. As I mentioned above - I got no feedback for the Mac Live CD install.

---

### Post by aysiu on 2005-11-28
[QUOTE=cannuck]
I am kind of superprised that the Ubuntu "team" would not want to make the Ubuntu OS - "Usable" - by having a Quicktime movie to explain the install on the different Os's. Or a least a "simple language" (understandable by anyone) - easy - step by step text tutorial with pictures. I can only imagine the thousands of wasted hours by various potential Users trying to install Ubuntu. The notion of relying on the forums to solve specific issues might make sense - but using forums to help on the basic install doesn't make sense to me - because the frustration of the install will force a lot of people to abandon Ubuntu. As I mentioned above - I got no feedback for the Mac Live CD install.[/QUOTE] I, too, am shocked by this--as Mandriva, Debian, and even Mepis have a PDF you can easily print out and reference during installation. I'm working on something like that--[this is the prototype](http://box.net/public/benplaut/dfiles/ubuntu_user_guide_05.11.pdf). It's in its very early stages, and I hope to revise it every month.

Unfortunately, documentation for the Mac (PowerPC) version of Ubuntu in general is very skimpy.

---

