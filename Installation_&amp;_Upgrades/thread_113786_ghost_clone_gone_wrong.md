---
title: "ghost clone gone wrong"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by andrew_y on 2006-01-07
I recently did a Norton Ghost 2003 clone of my dual boot system to a new hdd, and when I tried to boot it, all that showed up for GRUB loader was the word GRUB across my screen, with the bottom 5th or so of my screen blinking it. When cloning, Ghost said there was an error and to do a fsck to find the error, but I went along with the clone. 

When I boot to a live CD, it cannot mount it and says that the fs is corrupt or something when i do dmesg | tail, as it said in the error during the mount. 

I was suggested to reinstall, but I wish to not have to do it. Though, I was looking at the TARing the entire root, and was wondering if I did a complete root tar, and copied it over to the new installation, would it be possible to do so? Any help would be appreciated, thanks.

---

### Post by encompass on 2006-01-11
First off... do you need the root?  Second... you could copy all your home partition to a new one... and reinstall linux and leave the Home directory untouched.  That is what I do.. You could even do a netowrk transfer of all the data, even with file permissions intact with rsync.  That is the options that come to my mind.  Hope that helps.

---

