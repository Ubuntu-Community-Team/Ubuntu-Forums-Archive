---
title: "Dual Booting Suse, and Ubuntu"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Zom-b on 2009-03-15
yeah, so I *was* going to dual boot, ubuntu and suse, to see what some of the differences where, and when I did it somehow I did it wrong and now my ubuntu boot doesn't work, says something about the root folder being unable to be found, is there anyway I can fix this or should I just start from scratch, and is there any way I can recover files I had on the ubuntu possibly?

---

### Post by Zom-b on 2009-03-15
actually, after a bit of searching I found the files from my other boot, so I have been backing up my stuff in case I can't restore my ubuntu

---

### Post by avtolle on 2009-03-15
I'm no expert, but think that you would need to edit Grub (likely under openSUSE) so your Ubuntu install is correctly recognized. 

Was openSUSE installed after you installed Ubuntu? I didn't have any problems with this on one computer where I was trying openSUSE out, but definitely had an issue with it on another one, which was resolved for me by doing a reinstall of Ubuntu, after which Grub picked up the openSUSE install correctly. The reason I did it this way is that in my situation, both were newly installed, and I didn't have anything to save from the Ubuntu install. Good luck.

---

### Post by Zom-b on 2009-03-15
> **avtolle said:**
> I'm no expert, but think that you would need to edit Grub (likely under openSUSE) so your Ubuntu install is correctly recognized. 

Was openSUSE installed after you installed Ubuntu? I didn't have any problems with this on one computer where I was trying openSUSE out, but definitely had an issue with it on another one, which was resolved for me by doing a reinstall of Ubuntu, after which Grub picked up the openSUSE install correctly. The reason I did it this way is that in my situation, both were newly installed, and I didn't have anything to save from the Ubuntu install. Good luck.

I installed SUSE second, just today actually, so how wuld I got about editing grub? right now I'm in the SUSE live cd so I don't have to worry about not being able to do anything because of my hdd being mounted.

---

### Post by Zom-b on 2009-03-15
when I first start it and grub loads up, if I try to load ubuntu or the failsafe it gives me this message

---

### Post by Zom-b on 2009-03-15
well I am transfering all the things off of this hdd onto my gf's computer, and by the time that is done I am just going to start fresh and reload both lol, with the rate it's going that should take long enough for me to either get the fix or not.

---

### Post by avtolle on 2009-03-15
Sorry, had to leave for a while. 

It does definitely appear that Grub under Suse cannot find either Ubuntu or the failsafe. Looking around a bit, it appears that Suse uses a config file, rather than /boot/grub/menu.lst as Ubuntu uses. As I said earlier, I'm no expert, so where you go from here is beyond my knowledge. Good luck with what you're attempting; sorry I couldn't be of better assistance.

---

### Post by avtolle on 2009-03-15
If you're going to reinstall, I'd suggest Suse first, then Ubuntu; Grub on Ubuntu seems to do a very good job detecting exisiting o/s.

---

### Post by Simian Man on 2009-03-15
If you just want to try distros out, use Virtualbox.  Install the one you like best on your machine then try the others out as vms.

---

### Post by Zom-b on 2009-03-15
> **avtolle said:**
> If you're going to reinstall, I'd suggest Suse first, then Ubuntu; Grub on Ubuntu seems to do a very good job detecting exisiting o/s.

hehe thanks


@simian man
it's not so much trying them out or I'd just stick to the live cd's but I remember really enjoying the amount I could mess around in suse, and I like the support features of ubuntu, looking at them now it's almost like looking at the same then after a fresh install but i'd like to have both, yanno?


in the future I doubt this will be a problem because i'm looking at making a home server, so I can have all of my computers backed up lol

---

