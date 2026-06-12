---
title: "Grub/Boot Menu"
date: 2008-08-29
forum: General Help
---

### Post by maviso5 on 2008-08-29
Hello

I put ubuntu on my machine yesterday on a seperate 80GB hard drive.

Now when my machine boots up it has the linux boot menu and the default is linux, what i want to know is how to change this setting so that windows xp pro is the default option as i dont want linux to be my main OS.

Thanks

Dan

---

### Post by cariboo on 2008-08-29
For a newbie the best way to change the default boot is to install **startupmanager**. You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it. Once it is installed you will find it under System-->Administration-->StartUp-Manager.

Jim

---

### Post by mcduck on 2008-08-29
Press Alt-F2 and run "gksudo gedit /boot/grub/menu.lst" to open the configuration file for editing.

Then count the boot enttries in the file, starting from 0. Find the line near the begginning of the file with "default=0" and change that into the number of your Windows entry (so if the Windows was 6th entry change the line to "default=5").

After that find the line with "#updatedefaultentry=false" and change that to "#updatedefaultentry=true".

Save the file, you're done.

Alternatively, you can just move the Windows entry to be the first. If you choose to do so make sure you keep it outside of the section marked as "Debian automagick kernels list", otherwise it will be removed when the menu is re-created during kernel updates.

..or install the Startup Manager for a nice GUI to do this  for you.

---

### Post by amedac on 2008-08-29
Another alternative is installing in Synaptic -> QGrubEditor. This is very nice program, you can chance background in grub, change everything easy

---

### Post by Crafty Kisses on 2008-08-29
Both very solid programs, I've used both and they work really good.

---

### Post by maviso5 on 2008-08-29
> **mcduck said:**
> Press Alt-F2 and run "gksudo gedit /boot/grub/menu.lst" to open the configuration file for editing.

Then count the boot enttries in the file, starting from 0. Find the line near the begginning of the file with "default=0" and change that into the number of your Windows entry (so if the Windows was 6th entry change the line to "default=5").

After that find the line with "#updatedefaultentry=false" and change that to "#updatedefaultentry=true".

Save the file, you're done.

Alternatively, you can just move the Windows entry to be the first. If you choose to do so make sure you keep it outside of the section marked as "Debian automagick kernels list", otherwise it will be removed when the menu is re-created during kernel updates.

..or install the Startup Manager for a nice GUI to do this  for you.


Absolute magic, i used ALT F2 method and it worked a treat.

If i ever remove that drive, will the linux boot menu still appear, and if so, how do you get rid of it?

Cheers

Dan

---

### Post by mcduck on 2008-08-30
Great that you got it working the way you like. :)

What happens when you remove the Ubuntu drive depends on where you installed Grub. I think it defaults to the first hard drive. So the original Windows boot loader was overwritten. That meas that if you remove the drive  the computer won't boot into any OS, as the Grub can't find it's configuration (from the Ubuntu drive) and Windows bootloader doesn't work.

But if you ever do that, reinstalling the windows bootloader is easy and takes just a couple of minutes, just start the machine with the windows install disk, boot into recovery console and run "fixmbr".

If you installed Grub into the Ubuntu drive (and your BIOS is set to boot from that drive) you can just remove the disk and set BIOS to boot from the Windows drive again, and everything will work just like before Linux.

---

