---
title: "I'm in some really deep kaka after upgrading to a sata hard drive, please help"
date: 2008-10-12
forum: General Help
---

### Post by gully on 2008-10-12
Alright, here it goes.

Recently I upgraded from an IDE HDD to a SATA HDD.

I had a dualboot system with windows xp (ntfs) and hardy herron (reiserfs) on different partitions.
I was also upgrading my motherboard at the same time so I knew windows would be screwed anyway, but I used a gparted live cd to copy my ubuntu partition to the new HDD.
My ubuntu installation did survive a previous motherboard upgrade so that's not the problem.

After I installed my HDD I booted and the boot menu I used to have didn't show up.
I went ahead an installed windows xp on another partition anyway, but now I want ubuntu back so I booted off the ubuntu live cd and I could see the partition where hardy should be, much to my relief all the files were still there.

That's as far as the good news goes: I've reinstalled windows before on my dualboot so I know how to get the boot menu back (boot from live cd, edit grub etc...), but this time it wasn't working and grub/stage1 couldn't be found on any of my partitions, when I explored my hardy partition I couldn't find menu.lst either.

I decided I'd have to create a menu.lst file myself and copy it to the hardy partition but that didn't work because I couldn't copy paste between different partitions, not even with ntfs config (which I used to use all the time to move files between my partitions), so copying my important files from the hardy partition to the windows partition and then reinstalling hardy wouldn't be an option either.)

Does anyone know of a way for me to get my boot menu back (or any other way to get hardy back), or a way for me to copy files from my hardy partition to my windows partition from a live cd environment?

---

### Post by gully on 2008-10-12
I've got an idea: install hardy on a small partition, then create a dualboot again and then transfer the entire /boot folder to the old hardy partition and of course changing the values (hd0,x) in menu.lst.

Would that work?

---

### Post by gully on 2008-10-12
I've installed and upgraded ubuntu on a small partition and I can now copy files between partitions, so in theory I could copy all my files to the new ubuntu installation, but I'd only do that as a last resort because I don't want to loose all my settings.

I tried adding a new entry (I called it "Ubuntu old") to menu.lst for hardy that referenced to my old partition, that is I set "root" to that specific partition, I didn't know if I should change the "kernel UUID" and to what value.
I then copied the entire boot folder to the partition of my old install, so there wouldn't be any conflicts there.

When I try to boot into "Ubuntu old" I just end up on the desktop of the new install.

So my guess is I should edit the "kernel UUID" value in menu.lst, but it's just some big random number, so does anyone know how to find the UUID of another partition? Or if that even works at all?

---

### Post by gully on 2008-10-12
Consider this one closed.

I got my old hardy install back when I changed the UUID value in menu.lst, I found the value in /etc/fstab in the new install (just to be sure I copied fstab to the old install partition.)

I can now boot into my old install, I could play movies and browse firefox in it and unlike the new install it even recognizes my numpad (yes, that's right!) The only problems I encountered so far are that my new soundcard doesn't seem to be working (luckily onboard sound does work) and the ntfs config tool doesn't work anymore, but those are minor glitches.



Off-topic: why do I sometimes have to log in 5 times before I can post and why do have to fill out something resembling an IRS form (plus weird random questions that will sometimes give me an error even when I give the correct answer) when all I want to do is do a search on ubuntuforums?
I mean seriously, security is nice and all, but it can be overdone...

---

