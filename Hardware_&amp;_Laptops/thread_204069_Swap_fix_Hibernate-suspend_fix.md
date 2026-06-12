---
title: "Swap fix/ Hibernate-suspend fix"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by PENGUIN-PC on 2006-06-26
Hi there,
I had a problem with my hibernate-suspend features on my laptop too, and I also went looking through my partitions for an unrelated reason. I wanted to see what was going on with my swap space because my laptop (Sony Vaio pcg-grz630) was running really slow compared to my girlfriends winblows system running the same apps. What I found was that my linux-swap didn't even exsist technically. Space was allocated for it (twice actually), but it wasn't even being used (or it was inactive). When I fixed my swap space, my hibernate-suspend worked, and they didn't before. So here is what I did I hope it helps.:KS I'm sure a lot of you guys have different ways to fix this, and if any of them are better let me know, I'm learning like everybody else here.

1. Use Gnome Partition Editor to delete screwed up partitions, and recreate on     hda(insert whatever number you prefer here) linux-swap space.

2.  Use teminal for the rest of the following steps
[COLOR="Red"]sudo parted /dev/hda print[/COLOR]
This should show that you now have linux-swap there under the file system category.

3.[COLOR="Red"]sudo gedit /etc/fstab[/COLOR]
This will allow you to make sure, and/or edit the hda# so it is the same # as what you wanted to be used for your linux-swap space and save the changes.

4. [COLOR="Red"]sudo swapon -a[/COLOR]
This should activate your linux-swap space, and allow it to be used.

5. [COLOR="Red"]sudo update-grub[/COLOR]
This will update your grub so it loads with all the changes you have just made, and allows your computer to reboot correctly.

6. restart your computer (because you changed mounting points on the harddrive. Not sure if this is necessary, but I did it.)

[COLOR="Orange"]Enjoy!! and check out [www.Penguin-PC.com](www.Penguin-PC.com) Where I will be selling top of the line custom built and configured laptops, and desktops with Ubuntu Linux. [/COLOR]

---

### Post by Hellkeepa on 2006-06-26
HELLo!

Regarding your last step. It's not neccesary at all, as mount-points are made to be edited while the system is running. All you need to do to mount them after adding/chaning them us to mount them. This can either be done via referencing to the dev-item, "mount /dev/hda2" for instance; Or referencing it via the mount-point, "mount /home". This example assumes "/dev/hda2" should be mounted to "/home", and both are equal of the fstab is set up correctly.
As far as the swap goes, it should be enough to just use the "swapon" command after adding the swap-partition to the fstab.

Happy codin'!

---

### Post by PENGUIN-PC on 2006-06-27
Cool Thanks for the info. I am trying to learn as much as possible, and every little detail helps.

---

### Post by PENGUIN-PC on 2006-06-28
I'm still having trouble. Everytime I reboot all the changes I make are not staying. The linux-swap gets turned back into unknow file type, and becomes inactive. Anybody have any ideas why this change is not sticking?

---

