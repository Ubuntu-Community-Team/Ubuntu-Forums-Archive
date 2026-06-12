---
title: "Hard Drives problem"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by sinbad2699 on 2007-12-03
Hi, this problem is more my own fault, but i have no idea how to fix it as I'm new to Linux/Ubuntu.

I recently got a new computer [custom build], but the motherboard was faulty. Out of frustration, I reassembled my old Dell 8400 [dont worry its out of warranty!] I went to reinstall Windows on it but, it half-booted [got to the Windows XP boot screen], when I forced the computer off [because the Hard Drive had an old install with Gigabyte Drivers installed and not Dell]. Now I went to install Windows, but when it came to accessing the Hard Drives, the Dreaded Blue Screen Of Death reared its ugly face.
So anyways, I tried my Ubuntu 7.10 LiveCD, only to find I dont have a clue about the Nitty Gritty, stuff like surface scanning and such.

So anyways, I went to install Ubuntu on my offending Windows Hard Drive [it wasn't mounting properly], and that all went well, but the same problem occurred on another Hard Drive. So I tried re-installing Windows on my OS Drive, but same BSoD came up yet again.

***Basically here's what Ubuntu is reporting:***
```
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sda5':Operation
not supported Mount is Denied because NTFS is marked to be in use. Choose one action:
Choice 1: If you have Windows then disconnect the external devices by clicking 'Safely
Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.
Choice 2: If you don't have Windows then you can use the 'force' option for your own
responsibility. For example type on the command line: mount -t
ntfs-3g/devsda5/media/TV Series 2 -o force Or add the option to the relevant row in the
etc/fstab file: /dev/sda5/media/TV Series 2 ntfs-3g defaults,force 0 0
```

When I was using the LiveCD [before I installed Ubuntu] the same message came up for my Windows drive [replacing the sda5 with sda1, and TV Series 2 with Windows]. Now obviously I cant try the first choice, because I can't install Windows, and I don't want to try second because I want whats on the Hard Drive in-tact as much as possible [there is more than TV Series on it, quite valuable information to me is on it too]

I was, thinking, when I similar problem cropped up in Windows, I would just run a full surface scan and chkdsk to try and recover the File Table.

Is there any way I can do this on Ubuntu, because, while Ubuntu has its good points, it also has its bad points, like it cant run games that I want to play [this might a graphic compatibility problem, but I dont want to mess with it in case it destroys what I already have].

If you think that all I want Ubuntu for is just to fall back on when Windows fails, you're mistaken, I plan on using it a a Media Centre when I get my gaming PC going [becuase of its low resource hit, and so far I havent found a movie/sound file i cant play]

Any help would be appreciated thanks.

---

