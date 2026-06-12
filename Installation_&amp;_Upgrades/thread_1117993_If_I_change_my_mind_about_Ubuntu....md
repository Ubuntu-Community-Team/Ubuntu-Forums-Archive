---
title: "If I change my mind about Ubuntu..."
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by bryceowen on 2009-04-06
I've been playing with the various incarnations of ubuntu (I setup a LAMP on one box to play with and another box is using kubuntu exclusively) and think I'm finally at the point where I want to install it on my primary box. Now, I plan to set this up as a dual-boot system with my existing XP installation. My question is about partitioning. I currently have a 160gb drive and I planned on a 100gb NTFS partition for XP and the rest to ubuntu and its swap. In the even I decide ubuntu won't do for my primary box, is there a process that restores the partition to 160gb NTFS or would I have to find another utility to fix it?

Also, though I doubt it matters, I'm running XP 32-bit and plan on installing ubuntu 64-bit. There won't be any clash, will there?

---

### Post by Kalma on 2009-04-06
I don't know if there is any other way, but Norton Partition Magic can do what you are asking for. Anyway, I don't think you will want to go back to Wintho$e as your only OS any more  ;-)

---

### Post by 0cton on 2009-04-06
There are both commercial tools and open source software that do that:
see [http://partedmagic.com/](http://partedmagic.com/)
or for a proprietary one: [http://www.partition-manager.com/](http://www.partition-manager.com/) (There are many more,this is justs one I've used)
But a word of caution: Partitioning always involes a risk of losing/corrupting data have a backup :)
You should know that partitioning is a logical(logical disk) thing (you can repartition it (how you want) as long as the hdd is alive)
Hope it Helped

---

### Post by bryceowen on 2009-04-06
So I would have to fix it myself... Maybe I should just use a different HD...

---

### Post by davec64 on 2009-04-06
If you boot a live CD you can use Gparted to configure your partitions.

So if you  want to go back to XP:

Run a Live CD and Gparted to delete the Linux partitions, then extend the NTFS partition back up to 160GB.
You will then need to boot your XP disc and run fixmbr from the recovery console to remove Grub.
Once done you're back to XP.

As always just remember to back up important data just in case!!!

---

