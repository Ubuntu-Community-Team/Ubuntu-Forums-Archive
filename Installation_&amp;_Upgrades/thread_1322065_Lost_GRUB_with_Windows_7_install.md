---
title: "Lost GRUB with Windows 7 install"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2009-11-10
My brother has Ubuntu 9.10 installed across 3 partitions for /, /home and SWAP and everything was working fine. He also had a spare NTFS partition sitting there and finally got around to installing Windows 7 onto it. Now when he reboots his machine Windows 7 boots without showing GRUB so he can't boot into Ubuntu at all.

I searched the forums and most people seem to be having the opposite issue, I couldn't find anything similar to this. Is there a way he can repair the MBR to get GRUB to load again and dual boot? Is there any reason he should install GRUB 2 instead? Does it matter?

---

### Post by darkod on 2009-11-10
This is quite normal if you install windows after linux. Windows just writes his own bootloader in the MBR and it can't even see linux partitions even if it wanted.

It is quite easy to restore grub from the ubuntu cd but I am new to ubuntu and wouldn't like to misinform you about the steps.

Google reinstalling grub and you'll find loads of posts and tutorials. Cheers.

---

### Post by oldfred on 2009-11-10
The way to reinstall grub2 is different than that for legacy grub. 

I  have save these links:
reinstall grub2
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Maheriano on 2009-11-10
> **oldfred said:**
> The way to reinstall grub2 is different than that for legacy grub. 

I  have save these links:
reinstall grub2
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Awesome, thanks. Will this work for installing GRUB2 if he only had GRUB before? It says reinstall so I'm wondering if he'll have to install GRUB now since that's what was on there previously.

---

### Post by ratcheer on 2009-11-10
Here is the current documentation on grub2. Should have everything on installing, reinstalling, and using it. Even covers errors and troubleshooting.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Tim

---

### Post by Irony on 2009-11-10
Just boot up with your ubuntu live CD then issue the following commands in terminal;

```
sudo grub
```

This opens up the grub program, with a prompt of grub>, now type;

```
find /boot/grub/stage1
root (hd0,X)
setup (hd0)
quit
```

If your ubuntu install is on say hda3 or sda3 then (hd0,X) is (hd0,2) which is what the find command is doing. setup (hd0) means install to the MBR which is the place to do it.

---

### Post by caue.rego on 2009-11-18
> **Irony said:**
> Just boot up with your ubuntu live CD then issue the following commands in terminal;

```
sudo grub
```

This opens up the grub program, with a prompt of grub>, now type;

```
find /boot/grub/stage1
root (hd0,X)
setup (hd0)
quit
```

If your ubuntu install is on say hda3 or sda3 then (hd0,X) is (hd0,2) which is what the find command is doing. setup (hd0) means install to the MBR which is the place to do it.

This doesn't work with Karmic Koala any more. As others already mentioned, it comes with **grub2**, which works differently. The links provided are already helpful enough, but I'll add a direct official one (which I find not to be as simple as the wiki or the updated topic already mentioned):
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

From my experience, basically the "new steps" are quite easy:
0. Boot to the LiveCD Desktop (Ubuntu 9.10 or later)
1. From the Places menu, select and mount (double-click) the partition with your Ubuntu installation
2. sudo grub-setup -d /media/XXXX/boot/grub /dev/sda
3. if 2 fails: sudo grub-install --root-directory /media/XXXXX /dev/sda

Just keep in mind you better read more and **understand what you're doing _before_ frenzing on those steps**.

---

### Post by Maheriano on 2009-11-18
> **Irony said:**
> Just boot up with your ubuntu live CD then issue the following commands in terminal;

```
sudo grub
```

This opens up the grub program, with a prompt of grub>, now type;

```
find /boot/grub/stage1
root (hd0,X)
setup (hd0)
quit
```

If your ubuntu install is on say hda3 or sda3 then (hd0,X) is (hd0,2) which is what the find command is doing. setup (hd0) means install to the MBR which is the place to do it.

This worked perfect for his 9.1 install, thanks.

---

