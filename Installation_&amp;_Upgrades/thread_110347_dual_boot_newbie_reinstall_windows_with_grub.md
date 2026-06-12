---
title: "dual boot newbie/ reinstall windows with grub"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by PDXlewis on 2005-12-30
hey there.
  New to Linux; new to dual booting. I have ubuntu 5.10 on my primary drive (80gb) and xp pro on my secondary drive (20gb). I was wondering how you reload the windows in this dual boot environment? Is it a question of physically detaching it  and reloading it on it's own? If not, how would I get the boot from cd on the secondary drive with grub. Don't get me wrong. I am loving the linux thing and would love to drop windows someday. until then, as reloads are a common need for windows, I'd like to be able to refresh the os. 

:confused: It is ok, you can tell me I need to start over. My thought is that I should take off the ubuntu drive, reload my windows drive to something "cleaner" and then reattach the ubuntu drive. I am a little nervous as I think I will have a dual boot issue then and my only recourse for that is to reload ubuntu to get the sweet load with grub.

Any words of wisdom or otherwise is greatly appreciated.

---

### Post by ShirishAg75 on 2005-12-30
what should be happening is when u're installing Linux the windows hard disk should be there, as most probably it would get probed & known as a Win95 FAT32 or NTFS partition. I haven't tried this with a second hard disk but have done this umpteen times with a Windows partition & in the end GRUB will write the entries for Windows XP. If this is not happening then u'll have to dig a little bit deeper & look for the grub manual as well as tools like fdisk, parted which would tell u how & where the partitions are so they can be pointed. I haven't done this in a long time hence don't remember much. But its good as a starting point I guess.

---

### Post by PDXlewis on 2005-12-31
Thanks for the info. So, have you had to reinstall your windows os in your partitioned  dual booted setup with ubutnu? My booting is great now and I can get to both. I am having probs with windows seeing my cd drives but that may have something to do with the fact that I have windows as the secondary and it gets confused.  I am fixing that this weekend by starting over and reloading both once I swap the drives. I'd like to be able to "refresh" windows without bothering the ubuntu load (and grub). I think I am just not thinking about it right yet. Something will click here. I will look at the grub manual though, thanks, I think that will clear some of mhy fogginess.

-Tim

---

### Post by paddyg on 2005-12-31
Just in case you're still interested...
1. install windows first, linux next
2. install Grub to the MBR
3. Grub doesn't boot windows directly, it just chainloads, and what you'll see in /boot/grub/menu.lst is something like
```

title		WINDOWS XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by PDXlewis on 2005-12-31
I am cooking with gas now...  swaped the discs and reloaded and it is working like a charm. Love this stuff.  thanks for all the help. 
although,  where do I go in linux to see the other drives? I even left a fat partition on the disc with windows... I will look around and see what I am missing. 

Thanks
Tim

---

### Post by Leigh on 2006-01-01
Following on from this, I have a Windows drive as the primary drive and Ubuntu as the secondary. I will be replacing the Windows drive as it is faulty (hardware problem). When I install the new drive and reinstall Windows, how do I rebuild the GRUB menu and put it back in the MBR, I don't really want to re-install Ubuntu, but if I have to then that's OK too.

---

