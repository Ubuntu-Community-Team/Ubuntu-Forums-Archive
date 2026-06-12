---
title: "Error: No Such Disk"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by hotwax on 2009-11-07
I just installed Ubuntu 9.10 on an empty hard drive and I have another hard drive with Vista on it. When I boot up, I get the following message in boot screen

Error: No such Disk
grub rescue>

How do I solve this?

---

### Post by SuperSonic4 on 2009-11-07
Are you sure you didn't overwrite vista? If not it could be an fstab/boot order thing.

Can you boot into either OS by changing the boot order from the BIOS?

---

### Post by drs305 on 2009-11-07
Normally the user gets a "grub-rescue" prompt because grub 2 is installed but it can't find a usable grub.cfg file. This would make sense since it can't even locate the drive.

Take a look at this section on booting from the grub-rescue prompt and see if it helps:
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

---

### Post by hotwax on 2009-11-07
I'm certain I didn't overwrite vista and I haven't tried the boot order... ill try that now

---

### Post by hotwax on 2009-11-07
The boot order thing didn't work and i copied down those commands from the link, but im uncertain on how to use them. I tried locating a directory but i couldnt figure out how to open it. Any help on starting to learn how to change directory is much apperciated.

I type ls and i assume the text that showed up were my partitions, I just couldnt figure out how to change roots

---

### Post by Wuubu on 2009-11-08
Hi,

I dual boot with win XP, and get the same error, but in a different way.
After installing Ubuntu 9.10 i can use it and restart the system as many times as i want, and all will work fine with Ubuntu.
BUT, if i boot into Win XP and then restart the comp i'll get that message: 

Error: No such Disk
grub rescue>

Maybe windows is changing smth when quitting?
Now i just boot into Ubuntu and dont use XP cause it will brake the Grub every time.
To fix i reinstalled Ubuntu, but dont want to do that every time i go into xp :P
Please help us...

---

### Post by drs305 on 2009-11-08
What's obviously needed is for someone to post a nice howto on using GRUB 2 with Windows XP, Vista and Win 7. I am learning a lot about Grub 2 but don't deal with Windows. 

If someone has already posted a comprehensive guide to doing this then providing the link will help everyone out.

---

### Post by paul kinell on 2009-11-08
Found on Launchpad, similar?
If grub2 fails with a file not found error.
Try  - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) - worked for me.
or
At the grub rescue prompt try this:

set - # this shows where grub's trying to boot from, is it right?
ls  - # this lists all disks & partitions.

Now if you know the partition grubs "supposed" to be booting from, do this:

At the rescue prompt type:

set prefix=(hd0,1)/boot/grub
# the (hd0,1) being your hard disk, and partition.

then
insmod normal

then
normal

You should then get your grub2 menu as usual.
This fix (if it did indeed fix it) is not however permenant.
So after boot up, reinstall grub-pc & grub-common - # the fix proper.
Done.
Also worked for me, good luck.

---

### Post by darco on 2009-11-08
> **drs305 said:**
> Normally the user gets a "grub-rescue" prompt because grub 2 is installed but it can't find a usable grub.cfg file. This would make sense since it can't even locate the drive.

Take a look at this section on booting from the grub-rescue prompt and see if it helps:
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

Similar issue here but both drives have grub2....
SDA has Mint/Win running Grub2, SDB has Karmic running Grub2. When I installed Karmic, I disconnected SDA and everything is fine. On boot up I would hit f10 and choose SDB to log in to Karmic. Now for some reason, the SDB Grub2 has taken over meaning I no longer need to hit f10 as the Grub menu shows Karmic/Mint/Win....
How would I make SDA the primary Grub2 menu? I get this error the OP reports only when I disconnect SDB. I see your Grub rescue commands (set root=/dev/sdXY), would that work in this situation?
thxs

darco

---

