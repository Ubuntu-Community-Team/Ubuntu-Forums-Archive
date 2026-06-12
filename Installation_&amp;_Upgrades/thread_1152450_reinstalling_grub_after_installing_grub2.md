---
title: "reinstalling grub after installing grub2"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by csc2ya on 2009-05-07
Firstly, I apologise for the length of this post, but I wanted to get all the details in in case they're important.

I'm running ubuntu 8.04 (I know it's old, but it's a custom version from another site that I like, and I don't have the bandwidth to download a newer version of theirs)

The way I was booting previously, was that I had a triple boot configuration set up, with Vista and XP on the internal drive of my laptop, and ubuntu on the external.

I then used the vista bootloader which had entries for vista, xp, and ubuntu. The ubuntu option would then start grub, which in turn, booted into ubuntu.

I saw mentions of grub2 on here earlier, and (stupidly...hindsight is a wonderful thing) thought i'd give it a try. I downloaded and installed it through synaptic, and when installing, selected to chainload it off of the original grub menu, as suggested by the installer.

I then rebooted after installing it, and got an error. Unfortunately, I can't remember the exact error now.

I thought, fair enough, booted off of my vista dvd, and selected to do a startup repair. However, it appears that it completely wiped out my original MBR. After doing startup repair, and rebooting, I got the same error again. Next, I tried using super grub disk on the ultimate boot cd to boot into either windows or ubuntu, but this did not work.

I then booted off of an ubuntu livecd, and looked up how to restore grub.

I ran find /etc/boot/grub/stage1 to find the partition number, then ran grub followed by root (hd whatever partition number was returned by the find command), then install (hd0). I got no errors from this, and so rebooted and prayed.

And got exactly the same error as before.

I then decided to cut my losses and reformat the internal drive. I disconnected the external drive, put my recovery dvd in and rebooted, removed all the partitions, then told it to apply the factory image.

I'm now at the point where i've got Vista working again, but i've got no idea how to change grub2 back to the original grub on the ubuntu drive to get that to boot again, as I assume it would have changed the boot menu file.

I'm reluctant to try the method I mentioned above, in case it just restores grub2 to the mbr again, as I would have to reformat again if that happened. All I want is the original grub back on that drive and working, preferably without reinstalling ubuntu, as I have no backups of any of the data on there (It would also take a while for me to get everything reinstalled even if I could back up all my data).

Is there any way to get the original grub installed and working again using the livecd, preferably without risking the same thing happening that happened when I originally installed grub2.

I appreciate any help that can be provided.

---

### Post by pdxmuse on 2009-05-11
Had the same problem - grass is always greener on the other lawn cuz that's where the bulls...

OK, anyway, now I can only reboot into Wubi 8.04 and stoopidgrub2 gets an Error 11: Unrecognized device string.  i'm not a wild and wooly geek, just a recovering windowsfreak and trying blindly to find my way around.

Suggestions?????

---

### Post by mk.persia on 2009-05-11
If you can boot in one of your windows, your solution is a free app called EasyBCD, by using it you can reset MBR, or reinstalling grub, ( a nice grub have a menu for each of your OS)

---

### Post by Nightjock on 2009-05-11
I have the same problem cannot boot into xp or vista just ubuntu is there anyway I  can restore grub to see and boot into xp vista or ubuntu

---

