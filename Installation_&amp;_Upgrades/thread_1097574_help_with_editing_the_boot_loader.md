---
title: "help with editing the boot loader"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by 37fleetwood on 2009-03-16
I have hopefully a simple and quick question or two.
first a little explanation, when I decided to move away from Windows, I decided to keep a safety net and start with a clean windows install and dual boot with Kubuntu. well I hated Kubuntu and had to fall back on Ubuntu which has turned out pretty well.
now for the question or maybe questions.
can I simply delete the partition with Kubuntu on it and then edit the boot loader from the menu when the computer starts?
and next question which is related is every time I do updates I get more stuff in my boot list, do I need the old entries for older Kernels? can they go when I deal with Kubuntu, or is there a valid reason to keep them around?
finally, when I installed Ubuntu, it made a separate swap partition, so now I have two. can I safely delete one and does it matter which one?

if anyone cares the main reason I am unhappy with Kubuntu is that it is a fight every time I try to mount my NTFS storage drive, Ubuntu and Xubuntu do this with ease and give no hassles. Open GEU also refuses to play nice with my NTFS drive, or I might have used it instead of Ubuntu.:D
thanks,
Scott;)

---

### Post by bendib on 2009-03-16
If you have one installed, yes you can edit it easy, but if /booot is in the kubuntu partition, DON'T TOUCH IT! This will ruin grub. I would just go in there and delete everything that wasn't /boot, and then resize it smaller. Don't move it, just make it smaller on the right side. If you move where the beginning of the drive is, it'll have a cow.

---

### Post by 73ckn797 on 2009-03-16
> **37fleetwood said:**
> can I simply delete the partition with Kubuntu on it and then edit the boot loader from the menu when the computer starts?

You could have booted from the LiveCD, which I am sure you did when installing Ubuntu, and chosen to completely over write Kubuntu. The installation would have taken care of everything.

For the grub menu, open a terminal and enter:
```
gksudo gedit /boot/grub/menu.lst
```

At the bottom where the menu selections are listed you can insert "#" at the beginning of each line of the kernel entry you do not want. That will make it not appear when booting. It would be a good idea to not delete an earlier kernel just in case an update messes something up. If, after several days or so, you are not having any problems you can comment out the entry or read below.

If you want to completely remove an earlier kernel installation you can do that through Synaptic Package Manager. That will safely remove everything related to that kernel. You will find the entries for whatever is installed in the list.

Hope this helps.

---

### Post by 37fleetwood on 2009-03-16
just checked in /boot/grub/menu.lst on both partitions and it is using the one in my newer Ubuntu partition. the Kubunti menu.lst file only has Windows and Kubuntu listed.
I don't remember Ubuntu asking about overwriting Kubuntu, I think it gave me the option of overwriting the entire drive but that would have ditched Windows too and I didn't want to do that.
now if I'm not mistaken I need to be careful when resizing since the Kubuntu partition is first I can't just resize the Ubuntu partition over the top of it as it will move the starting point of that partition correct?
also what about the 2 swap partitions, is there a way to tell which one I'm using?

how hard would it be to put another linux install in there? I have a certain Puppy Linux that I wouldn't mind being there. I think I'll look into that.
thanks guys!

---

### Post by 73ckn797 on 2009-03-16
It would probably be just a matter of making certain that you do not wipe the entire drive. This might mess up grub, however, since Windows is (or has been?) the first partition. Creating a new partition might change the numbering. I am not absolutely certain about that, though.

A good tool to use for fixing the grub menu is "Super Grub Disk" available at [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) .

There is also a way to fix grub using the live CD. See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) .

---

### Post by 37fleetwood on 2009-03-16
I was thinking along the lines of emptying the partition and plopping Puppy linux into it and just adding it to the existing grub list where Kubuntu is listed now.puppy will let me do an install without setting up grub at all, so all I would have to do is add it in the list and point to it. the new Puppy Puplet with e-17 is really nice and might be usefull as it is super speedy and compact.
thanks
Scott;)

---

