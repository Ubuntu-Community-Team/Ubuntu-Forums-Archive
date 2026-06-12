---
title: "[SOLVED] Dissappearing splash screen after resizing partitions"
date: 2008-07-20
forum: General Help
---

### Post by palomar on 2008-07-20
Hi,
Recently I expanded my /swap partition using a gparted live cd and shrunk the root-partition. After that, when booting Ubuntu, the splash screen disappears after a few seconds and I see console text, starting with 'reading files to boot' and so on (goes to quick to read completely).
After that, Ubuntu is running fine and there seems to be no problem at all.

But: I want to know WHY the splash screen suddenly disapear? I think it's undesired behaviour and there must be something that triggers it. It all started after resizing my swap partition from 1.8GB to 4.5GB (and shrinking my / partition with that same proportional amount).

Are there log files I can check?

Kind regards.

---

### Post by coffeecat on 2008-07-20
> **palomar said:**
> But: I want to know WHY the splash screen suddenly disapear? I think it's undesired behaviour and there must be something that triggers it. It all started after resizing my swap partition from 1.8GB to 4.5GB (and shrinking my / partition with that same proportional amount).

Yup. This sounds depressingly familiar. :(

Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=857565"). In my first post in that thread, I give the fix and three links which may help to explain the background.

One question:

> **palomar said:**
> It all started after resizing my swap partition from 1.8GB to 4.5GB

Why such an enormous swap partition? :shock: 1.8 Gb was probably more than you'll ever need.

**Edit**: Read right through that thread. I forgot about checking /etc/fstab in my first post and mentioned that later. If you don't get the swap UUID in fstab right, Ubuntu will probably boot up OK but not mount the swap partition. Which would mean 4.5GB going to waste. :wink:

---

### Post by dcstar on 2008-07-20
> **coffeecat said:**
> 
......
Why such an enormous swap partition? :shock: 1.8 Gb was probably more than you'll ever need.

Swap must be as least as big as real memory to allow hibernation to disk, so perhaps someone did a RAM upgrade?

---

### Post by coffeecat on 2008-07-20
> **dcstar said:**
> Swap must be as least as big as real memory to allow hibernation to disk, so perhaps someone did a RAM upgrade?

Good point. I forgot that. :)

---

### Post by dcstar on 2008-07-20
> **palomar said:**
> Hi,
Recently I** expanded my /swap partition** using a gparted live cd and **shrunk the root-partition**.
.......

You have changed the UUID of both those partitions, so your /etc/fstab file is probably no longer correct.

You need to manually edit /etc/fstab to reflect the new UUIDs, or just change it to use normal /dev/ designations.

Plenty of posts in the forum with details on doing this.

---

### Post by palomar on 2008-07-20
Thanks Coffeecat. Followed your tip as mentioned in the other topic:
> 1 - Run 'sudo blkid -c /dev/null' (no quotes) from a terminal. Include the -c /dev/null bit. If you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.

2 - Check that the UUID for the swap partition in /etc/initramfs-tools/conf.d/resume is the same as the UUID you got from blkid. Edit the file if necessary.

3 - Run 'sudo update-initramfs -u' from a terminal (again, no quotes).

4 - Reboot.

5 - Enjoy usplash.
And splash screen is working fine now :)

And about the' huge' swap partition. When installing Ubuntu I just took the same amount as my RAM (2GB in fancy GUI installer became 1.8GB). But hibernation did not work, so I tried increasing it to something big enough like 4.5GB. But it seems like hibernation is still not working...

update.
I had to edit /etc/fsab as well, since gnome system monitor still reported 0 bytes of swap. Now it reports the right amount. Hibernate still doesn't work well (screen stays blank), but that's another problem.

---

