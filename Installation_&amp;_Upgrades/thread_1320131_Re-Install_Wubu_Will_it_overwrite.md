---
title: "Re-Install Wubu Will it overwrite"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2009-11-08
I am to the point where I want try and re-install since Ubuntu wont load and I  have tried everything I know to do.

Will it overwrite everything, see that I have an install and offer to fix or what?

---

### Post by AnarchyLinux on 2009-11-08
[B]Ubuntu wont load?


What hapends?


Can you be more specific?[/B]

---

### Post by ronaldbrijo on 2009-11-08
A clean install will overwrite everything on your hard disk.

---

### Post by dontgetshocked on 2009-11-10
Well, I wish I could but unfortunately I finally gave up and re-installed.Even though I only told it to partition 30gigs, the old 80 gig partition showed up in the un-install process.Even after I re-installed using Wubu again, I still could not get rid of the multi-boot menu with Ubuntu listed as second choice.It says something about system32 Hal.dll and since I am no fool I know not to mess with it.Been there done that.Anyway the message was a weird one, something that didnt make any sense.I am now not a fan of Wubi.Since I didnt have a cdrom with my netbook it was my only choice since it came with xp.Thank goodness I have my desktop with Ubuntu.Thanks one and all.

---

### Post by wilee-nilee on 2009-11-10
You can load the ISO onto a bootable thumb drive and install in the netbook after you get this worked out, a dual boot. To get rid of the Ubuntu in windows boot after it has been removed you look for all extra files named wubi ans ubuntu delete them then run msconfig in run on windows and edit or remove the ubuntu from the windows bootloader. Hopefully somebody will give a better explanation then mine. 

You just have top find the correct ISO to thumb program, or if you know anybody with a linux setup use the program in the stock system.

---

### Post by garvinrick4 on 2009-11-10
In wubi on C: in Windows there is an uninstall option use it and the boot selection in windows dos4grub will be gone also. When you
reinstall wubi it will put itself back into the windows dos4grub that wubi attaches itself to. 
 Wubi does not use the GRUB2 or GRUB legacy. It uses the DOS grub.

---

### Post by dontgetshocked on 2009-11-11
One more question.I still have Ubuntu show up upon boot,but with this Eee PC it wont let me edit thee boot.ini file.Anyway around this? I tried logging in as admin and also booting to the command prompt with no success.

---

### Post by garvinrick4 on 2009-11-12
That old 80 Gig partition thing worry's me. Wubi only go's up to
30 Gig I believe why is there an old 80  gig partition. 
 If you have a XP and an Ubuntu boot that is a good thing.
Did you have an old 80 Gig partition with a Grub legacy hanging
around in there somewhere?

When you uninstall Wubi the Ubuntu boot in the Dos4grub will be gone. And in the install it would be added back in. That is what
WUBI does.

Something sounds a little odd with this 80 gig Ubuntu partition of yore.

---

### Post by dontgetshocked on 2009-11-12
Well it didnt quite work out that way.I cant get rid of the old Ubuntu menu showing up on boot since my Asus Eee 900HD has come with some restrictions on it.I dont have a cd/dvd drive right now so I am encumbered.I will correct this soon.The Wubi un-install did not go as it should have.Anyways it is a mute point now because I have deleted the partition and all is well except that dual boot screen.MsConfig will not let me edit the file even as admin.When I get my drive I will fix this hopefully by booting to the cd and then the command prompt. Thanks for your help.

---

