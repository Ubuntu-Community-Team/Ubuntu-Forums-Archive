---
title: "Remove XP boot option at start up"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by leolion on 2009-10-27
Hello, I have XP SP3 installed and Ubuntu. The PC is otherwise completely blank and the space XP is taking up isn't really an issue at all.

What I would like to do is remove the option to boot up to XP or Ubuntu at startup so it goes straight into Ubuntu. Could someone tell me the easiest way to do that please? I would leave it as it is but it defaults to XP so I can't just switch it on and walk off.

---

### Post by Mark Phelps on 2009-10-27
Depends on your installation...

If you have XP and Ubuntu installed to different partitions, such that you're seeing a GRUB menu, if you just want to remove the selection option for XP, use the terminal to edit the menu.lst file to remove the XP stanza from the boot/grub/menu.lst file.

If you have Ubuntu installed inside XP (using Wubi) and are using an MS Windows boot loader menu to select your OS, you have a much more difficult problem.

---

### Post by JugglinPhil on 2009-10-27
I think it would be easiest to install Start-up Manager from the repositories. Running it (System => Administration => Start-up Manager) just unselect the option 'Show bootloader menu'.

---

### Post by leolion on 2009-10-27
I'm sorry I'm not sure what Wubi is but I had XP on there and installed Ubuntu from inside XP. The screen comes up black with two options and a countdown if that helps.

I think what I would like to do is wipe the computer clean and get it set up right as it's currently not got anything else on it.

I have a CD called ultimate boot cd with lots of useful programs on it. One will wipe the hard drive, there's also one that will set up a linux boot disk. Would I be going in the right direction to think I need to wipe it, set up that boot disk and then boot up from the Ubuntu disk that I made from the iso and that will install Ubuntu?

I was hoping there might be something simple I could set that would just remove the option.

---

### Post by Earl_Maroon on 2009-10-27
You can edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

Delete the entry for Windows XP and the next time you boot it shouldn't show. You could also cut and paste the section to the end of the file if you would just like to have XP appear as the last option instead

Back up menu.lst first in case you mess up though!


(If you want rid of your XP partition completely you can then use gparted (in the repos) to delete and reformat the disk space used by XP.)

---

### Post by Mark Phelps on 2009-10-29
> **leolion said:**
> I'm sorry I'm not sure what Wubi is but I had XP on there and installed Ubuntu from inside XP. The screen comes up black with two options and a countdown if that helps.
That is what is known as a Wubi install.  It installs Ubuntu INSIDE MS Windows in a special file that Ubuntu treats as a partition.  This means that removing XP wipes out Ubuntu as well.

> I think what I would like to do is wipe the computer clean and get it set up right as it's currently not got anything else on it.
That's certainly the cleanest approach -- but it does mean you have to start over from scratch.

> I have a CD called ultimate boot cd with lots of useful programs on it. One will wipe the hard drive, there's also one that will set up a linux boot disk. Would I be going in the right direction to think I need to wipe it, set up that boot disk and then boot up from the Ubuntu disk that I made from the iso and that will install Ubuntu?
Have seen those. They're a collection of utilities, sometimes quite old, that are designed for MS Windows machines.

My own preference is to use Linux utilities for Linux installs, and MS Windows utilities for MS Windows installs.  So, if your goal is to wipe XP and go entirely Ubuntu, you don't need that disk.  Simply boot from an Ubuntu LiveCD and select the "Use entire disk" to erase all the existing partitions and install Ubuntu.

> I was hoping there might be something simple I could set that would just remove the option.
No -- not something simple.  If you want to "move" your Ubuntu install to its own partition, you can then remove XP -- but that's a lot more complicated than a fresh install.

However, if that's what you want to do, look over the info at the following link: [http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

