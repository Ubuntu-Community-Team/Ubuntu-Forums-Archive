---
title: "Can't mount my HDD??? HELP!"
date: 2008-10-17
forum: Hardware
---

### Post by StaticSpaz on 2008-10-17
Ok.. so after trying to partition my vista section with vista itself.. it crapped out and gave me an error and wanted to restart the computer. So i let it and now i'm stuck in a loop.. When it restarts vista screams at me that there is a problem and it wants to repair, so once again i let it do it's thnig, but then once it thinks it can log on, it says i can't find the problem on why it can't load vista, and wants to restart... you can see my loop here..
So now i've loaded Ubuntu with my LiveCD and when i go to double click on my HDD to look at my files, it says something like "can't mount volume on HDD"...
How do i fix this? 
Ask any questions if i need to provide more information!
Here's a picture to help out too!

---

### Post by jerome1232 on 2008-10-17
If the Windows chkdsk utility couldn't repair the file system...

You made backups right?

Can you mount it read-only?

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda3 /media/windows -o ro
```

Do Not try to force any mounts, it can only worsen the problem I believe.

Do you have an external drive?

srry But i'm going to be out for a bit I will try and help more when I get back unless some1else takes it up.

edit: run chkdsk a few more times I've seen multiple runs help before.

---

### Post by inxygnuu on 2008-10-17
heres what you want to do:
1)open your computer
2)harshly rip out the hard-drive
3)get very angy and throw your computer, then nuke it, or strap it to dynamite.
4)buy a new computer
problem solved:)

no, want you really want to do is download a program that reads your nfts, Ubuntu can't read nfts partitions.
try add/remove programs.

I went through the same problem, and good luck.

---

### Post by jerome1232 on 2008-10-17
Ubuntu can read/write to ntfs just fine, it just doesn't have utilities as good at repairing ntfs as Windows does.

---

### Post by inxygnuu on 2008-10-17
> **jerome1232 said:**
> Ubuntu can read/write to ntfs just fine, it just doesn't have utilities as good at repairing ntfs as Windows does.
or that, I just knew that it was not that good with nfts. the throwing the computer away and buying a new one would would work fine...:-P

---

