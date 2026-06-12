---
title: "[SOLVED] Slash Screen Problems"
date: 2008-08-02
forum: General Help
---

### Post by thegodfaza on 2008-08-02
Well I made a new partition with gparted and now when I boot I don't get the load bar splash screen. I get the first one that goes side to side but then it drops down to text only. I get the load bar on shutdown though.

Edit: The title should be "Splash Screen Problems"

---

### Post by weweboom on 2008-08-03
that could mean you messed up you xorg.conf
to fix enter into the text only screen 
```
sudo apt-get --reinstall install xserver-xorg
```
then reboot, did that fix it?

---

### Post by thegodfaza on 2008-08-03
Nope. Didn't work.

Edit: I should probably also mention that when I repartitioned I removed my SWAP partition and deleted the entry from fstab. Don't really need one with 2 gigs of ram.

---

### Post by cariboo on 2008-08-03
I belive you will eventually run into problems running without a swap partiton. I have 2Gb ram and entering  free in a treminal this is the result:

```
free
             total       used       free     shared    buffers     cached
Mem:       2025152    1925972      99180          0      45184    1099976
-/+ buffers/cache:     780812    1244340
Swap:      5662872        660    5662212
```

As you can see swap is being used. I currently have running, Firefox, 2 terminals, 2 instances of Acrobat, and 2 instances of nautilus. It's not a lot, usually I have a lot more running. I'm running Intrepid alpha3 and I'm limited to only 2 workspaces because compiz only works occasionally. :(

Jim

---

### Post by weweboom on 2008-08-03
not having the swap partition is most likely the problem you should back up your files if you can access them somehow and reinstsall ubuntu

---

### Post by thegodfaza on 2008-08-03
Not seeing the little load bar isn't big enough to make me reinstall the whole OS. I just like seeing it instead of text. And I haven't had any problems running without a swap partition. I usually disable it while installing on my machines since they are all +2 Gigs of ram. I have just never removed a swap after having it on the OS so I think I may have missed something to modify.

> **weweboom said:**
> not having the swap partition is most likely the problem you should back up your files if you can access them somehow and reinstsall ubuntu

I could also use gparted to make a new swap partition then write an entry into fstab for it.

---

### Post by coffeecat on 2008-08-03
> **thegodfaza said:**
> I could also use gparted to make a new swap partition then write an entry into fstab for it.

And if you want your usplash back, you have to do a little more. Most people lose the usplash when they resize their swap partition and the UUID changes. I should imagine you did because you got rid of your swap partition.

Anyway, have a look in my first post in [this thread](http://ubuntuforums.org/showthread.php?t=857565) for the fix. If you want the full story, and why this is happening, follow the links (especially the launchpad one) that I provide there.

---

### Post by thegodfaza on 2008-08-04
That works great. Thx.

---

