---
title: "Grub Trouble/ Not booting into Win XP Home"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Terrizzle on 2009-03-19
Hey all,

So I'm fairly new to ubuntu but from what I can tell, I love it so far. BUT, im having trouble which is making me a lil frustrated.

Story:

I have a computer that was really going down the toilet because of a virus. There was no way around it...trust me. So, I installed ubuntu as a second OS and saved my files to a partition created in ubuntu. Then, I re-installed win xp home edition. 

Problem:

After reinstalling win xp, I no longer seen grub! It just boot right into XP. I checked disk management in win xp and there are two logical drives that are still assigned to ubuntu. So my files are still there. I just can't get to them!
So what I did now was follow some instructions to get Grub back. It worked...but now when i try to boot into windows. it flashes  and goes right back to the OS selection screen. thats it.

how do i fix this????

*by the way, I can boot into Ubuntu No problem*

---

### Post by tommcd on 2009-03-20
> **Terrizzle said:**
> 
So what I did now was follow some instructions to get Grub back. It worked...but now when i try to boot into windows. it flashes  and goes right back to the OS selection screen. thats 
I can boot into Ubuntu 
What *exactly* did you do to "get grub back"? Did you reinstall grub from the live CD? In any case, you could try to reinstall grub:
First, backup your grub menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
Then try reinstalling grub from the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
If that does not work, then post the output of:
```

sudo fdisk -l

```
and post everything after the **### END DEBIAN AUTOMAGIC KERNELS LIST** in your /boot/grub/menu.lst file.
If Windows is installed to the first primary partition of your hard drive, which it likely is, then you could try adding this to the end of /boot/grub/menu.lst:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by guywithcable on 2009-03-20
It's probably that your menu.lst refers to Windows being on the wrong partition (since I'm assuming you recreated the Windows partition), so it is still referring to the old partition. I think Ubuntu 8.10 now uses UUIDs in menu.lst, so you can use
```
ls -l /dev/disk/by-uuid
```to find the new partition's UUID. NTFS UUID are about half the size as Linux ones, and don't contain dashes, so that's the one your looking for.

ps: use
```
sudo gedit /boot/grub/menu.lst
```to edit menu.lst.

---

### Post by Terrizzle on 2009-03-20
thanks folks :)

well, I actually just removed grub completely that way I was able to boot back into windows. Once I done that, i used a handy little tool that can be found on this site:

[HTML]http://www.fs-driver.org/[/HTML]

i was able to see my logical drives in Windows and get my files without trying to boot into ubuntu and transfer files that way.

after that, I deleted my logical partitions involved with linux and used partition magic to join the free space leftover to my current partition on windows.

all is well :)

but i'll definitely print out those steps you both have mentioned..that could of helped A LOT before i did my actions lol

thanks again!

---

