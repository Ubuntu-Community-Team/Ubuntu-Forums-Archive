---
title: "Cant install feisty on aspire 5003wlmi"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by ram100987 on 2007-08-14
I've been using feisty on my desktop for several months and played with one of the older version for a short time a while back.
I've been trying to put feisty on my fiance's laptop(acer aspire 5003wlmi) for the past couple weeks to let her get the hang of this much better OS. But i've had no luck getting it running.

I've read many people successfully installing feisty on 5003wlmi minus some resolution and wireless card issues. but I can't even get it to install.  I've tried both 32bit and 64bit and both act the same.  If I use the normal livecd, it will load the kernel very slow(for some strange reason shaking the laptop helps) and then it either freezes at 100% or it will go to the boot screen and freeze before it finished booting, or just plain never boots, just keeps loading............ I then tried the text version and I would choose text installation and I could only see a vertical strip on the left quarter of the screen and the rest would be black.  I was thinking I had bad disks or the reader sucked, but I tried the no-CD net installation last night where I install an app in windows that changes the boot file and allow me to boot into the text installation and have it download the distro and install it, eliminating the disk all together but I still ended up with only the left quarter of the screen visible.

Could someone give me some pointers on how I could troubleshoot this issue please?

P.S. everything is factory, not even any added RAM and the bios are default besides making the cdrom boot first.

---

### Post by ram100987 on 2007-08-14
well I solved one problem.  I found somewhere several boot options to try, so I added "vga=791" to the boot option and it worked! I was able to boot into the text installation and got most of the way through but now it stalls at 6% during the software installation.  It keeps trying to read the disk for 10 min then gives up and says that it has failed.  I really hope this is just due to a bad disk this time. I am going to burn a fresh disk and hope it works

....I welcome to any other suggestions that might help out....

---

### Post by operator207 on 2007-08-15
The fact you state you can shake it to make it continue, leads me to believe you have either bad connectors to your optical device, or a bad optical device (worn out, so its not tracking exactly where it should be) I doubt its a bad CD, though it would be the cheapest thing to replace at this point.

---

### Post by ram100987 on 2007-08-17
whats strange is I've burned many movies on it that play just fine on my 360...  But anyway, i finally got ubuntu working by using wubi, then using lvm to make it a true installation.  Literally just got it working and it booted up just fine, but im back in windows for a moment to read how to get the wireless working, but after thats going, ill be using ubuntu for good :)

---

