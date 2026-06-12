---
title: "Feisty Install"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by cowboy.bebop on 2008-12-08
So it seems the newest Ubuntu isn't my most favorite rev, released, so I decided to move back to the Feisty Fawn edition. Why, do you ask, because of the crappy nvidia feature they got on there, even after uninstalling it I still could not manage to manipulate my X.org config. So I figure hey why not install what worked back then. This is my setup here:

[IMG]http://img177.imageshack.us/img177/6104/screenshotsl5.png[/IMG]

So as you can see I have multiple partitions set up, yes I know, don't ask me why, until I can figure out what it is that I am going to actually do with them. So, I have made the decision of saying "Screw windows" I don't game anymore and or do graphic design, so my best bet is to use something that is quick and clean.

So after wiping my SATA clean I have added the following:

    / = Pretty much the left over free space
/boot = 80MB
 SWAP = 2048

Okay so now that it is clean and clear, And installing I get an error on the screen: "Error loading Operating System" *bites lip*

Okay so lets try to restore GRUB:

Applications > Utilities > Terminal

% sudo grub
% grub: find /boot/grub/stage1
   (hda0,0)
% grub: root (hda0,0)
   root (hda0, 0)
% setup (hda0)

and of course setup was successful... lets reboot

% grub: quit
% sudo reboot

[Computer Restarts]
waiting patiently...

Black screen! Oh Noeeee's!

"Error Loading Operating system"

*Bites into lip, watching as I hemorrhage*

Such a dramatical sequence forgive me, just venting.
Could someone please tell me where I went wrong?

---

### Post by lovelyvik293 on 2008-12-08
As in the pic there is not any '/'(root) mount point. 
You have to have a '/'.

---

### Post by cowboy.bebop on 2008-12-08
Well I made a 

/ = All disk space
/home = 20GB
/boot = 50MB
SWAP 2048

I am about to see what the results are now, rebooting brb.

---

