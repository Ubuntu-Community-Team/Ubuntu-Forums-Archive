---
title: "Need help fixing hardy"
date: 2008-08-25
forum: General Help
---

### Post by animalsx on 2008-08-25
Hey guys, I've finally run into a snag with ubuntu. Somehow my /boot directory was deleted. I copied the /boot directory off the livecd onto the old root dir and rerun the grub setup, but no dice. startup snags at "waiting for root filesystem" The old kernels are still in the modules directory, but I don't know how to direct grub to use that. I've tried to boot from the livecd and chroot over to my old one and rebuild the kernel, but I get errors when installing. I also can't use apt-get update (after chroot) because it is unable to resolve any of the repositories even though I am on the internet. I've also tried redownloading the files needed to rebuild the kernel; but the installation fails.

I'm somewhat new to this area of linux so I'm sure there is an easier way to do things. Any help would be appreciated..Thanks

I'm on hardy, I was previously running the intrepid kernel (2.6.26-2)

---

### Post by carolinason on 2008-08-25
I've never put the entire /boot directory back and am sure it can be done, but it sounds like a lot of work and depends on the size of the data you have that needs to be backed up. 

If you have data to needs be archived, I would use something like systemrescuecd to backup files.

If you don't have any data that needs to be backed up then I would just reinstall Ubuntu.

but this is just how i would do it.

---

### Post by wannadumpwindows on 2008-08-25
Because you just copied it over from the LiveCD, it's probably trying to find your kernel on a CD. You need to edit your kernel lines to point to your hard disk.

That'd be my first guess as to what's going on.

---

### Post by animalsx on 2008-08-25
That's what I was thinking, but I don't know how to edit the kernel since it's not loaded (chroot is fubar'd)

Can I use a boot directory from someone else using 2.6.26-2 with a mount @ /? Or is that too simple..?

I can access all the data off the partition (from windows) and back it up, so I'm not worried about that.  I would like to avoid the hassle of reinstalling, though.

---

### Post by wannadumpwindows on 2008-08-25
> **animalsx said:**
> That's what I was thinking, but I don't know how to edit the kernel since it's not loaded (chroot is fubar'd)

Can I use a boot directory from someone else using 2.6.26-2 with a mount @ /? Or is that too simple..?

I don't know what you did with chroot, but I'd think it'd be as easy as editing your menu.lst file to point to the right place.

Open up a terminal, and in it enter:
```
sudo gedit /boot/grub/menu.lst
```

Then edit your kernels lines to point to the right locations on your hard drive. You should be able to look at what you already have there to get an idea of what they need to look like. Sorry I can't offer more specific help, but I've never had to do this. And you might still have some kind of problem stemming from your chroot-ing.

---

### Post by animalsx on 2008-08-25
I don't know why chroot is weird, perhaps because I am runnning it off the liveCD.  It does work, but I can't do anything worthwhile (like apt-update) without changing it back to /

And the vmlinuz and initrd file were both deleted and I can't find (or download) them so I can't point menu.lst to anything.  The kernel still has a folder in /lib/modules, I'm guessing there is a way to rebuild from that..?

edit: when I use the vmlinuz file from the livecd (no initrd is on there) it boots and hangs at "waiting for root filesystem"

Thanks for the help so far

---

### Post by wannadumpwindows on 2008-08-25
Starting to sound like you might be better off backing up and re-installing. Even if you do manage to get things fixed, it sounds like you might still have a bunch of other issues after you get it all sorted out.

I don't wanna be the bad guy, but it sounds to me like it's your easiest route at this point. Unless someone else has something better.

---

### Post by DemonBob on 2008-08-25
Copy your /etc/resolv.conf /etc/hosts /etc/hostname over to the chroot, then chroot to the enviroment. 

apt-get install linux-image

---

### Post by animalsx on 2008-08-25
> **DemonBob said:**
> Copy your /etc/resolv.conf /etc/hosts /etc/hostname over to the chroot, then chroot to the enviroment. 

apt-get install linux-image

That got apt-get working! apt-get install linux-image didn't fix my problem though.  I am running apt-get -f upgrade now so hopefully that will fix it.

---

### Post by carolinason on 2008-08-25
I used to think a reinstall was bad. Why miss the fun of putting it back together. 

I did make a few assumptions on this. Post count, even though this doesn't reflect anything other than the number of posts. Ubuntu ease of use. Based on the complexity of the issue and post count, I figured functionality outweighed academics.

I just checked my /boot directory and there is nothing in it.

Am I here?

***EDIT*** Rebooted /boot has returned. best i coan figure it became unmounted.

---

