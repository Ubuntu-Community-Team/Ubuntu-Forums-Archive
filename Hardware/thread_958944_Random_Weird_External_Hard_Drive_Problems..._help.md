---
title: "Random Weird External Hard Drive Problems... help?"
date: 2008-10-25
forum: Hardware
---

### Post by komarue on 2008-10-25
To all,

First, this is my first post, mainly because I usually find the answers to my problems in this forum before I have to actually ask, so thanks to everyone who posts helpful responses. 

The problem: External Hard drive will not mount in linux / windows

Systems: 
1 Compaq v2309US Laptop - Xubuntu 8.04 w/ Gnome desktop installed
1 Dell Optiplex Mid-Tower GX270 Windows XP prof. Service pack 3

External Western Digital 500GB (don't know specifics, bought it pre-built in a fantom external case)


More detailed explanation of the problem.

I use my Old dell as a media center out in my main room, and the 500 external houses most of my media. Last night the computer started beeping approximately every 30 seconds (the whole, device plugged in, sound, 30 seconds, device unplugged sound) I hadn't done anything to it at all. I shut the machine down and left it to the morning. This morning I discover (via kismet) someone is trying to deauth-hack my network. Spent the morning securing my network. Turned my attention to this external hard drive issue. Plugged it into my linux laptop and about every 30 seconds my laptop would try to mount it as well, and fail. The error it displayed was something along the lines of Unclean mount $Load has erros in it, run chkdsk or force mount.. 

I plugged the device back into the windows machine, however now the drive wouldn't show up (even for the few seconds between "plugged in" and "unplugged" sounds) so I couldn't have chkdsk try to fix it. Ran the whole gamut of Admin tools, no way to get chkdsk to run on it. I tried to convince chkdsk to run on all my drives when I booted next, this worked, it checked Drive C only... 

Switched back to linux and felt my last resort was to just force mount it so I could run fsck or ntfsresize (only not actually resize it, just have it check/repair any errors). This didn't go so well. Now I am getting the following error
--------------------------------------
ntfs_attr_pread: ntfs_pread failed: Input/output error Failed to read first NTFS_BLOCK_SIZE bytes of potential restart page. Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2:If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/disk-3 -o force or add the option to the relevant row in the /etc/fstab file: /dev/sdb1/media/disk-3 ntfs-3g force 0 0
---------------------------------------

Unfortunately it won't even mount to /dev/ anymore so trying to force it again gives me a 'directory not found' issue.

The operating systems don't have a problem, its got to be with the Hard drive itself, if I could somehow get it to mount I could try to fix it using fsck etc.. however still no dice. I really don't want to lose a 500gb hard drive over this. Even Gparted doesn't see anything (which is to be expected of course)

I really don't know what to do at this point. Hence the post and my desperate plea to have some direction on what I might be able to do to get my data back / restore my hd. 

Thanks in advance. I am pretty new to linux, only a year or so but have 2 years professional java programming experience etc so the super detailed doesn't scare me too much, maybe a little.

Komarue

---

### Post by Lord Xeb on 2008-10-26
Just plug it into a Windows machine and then safely remove it by unmounting it from within windows.

---

### Post by cariboo on 2008-10-26
It looks like the only option you have is to in a Applications-->Accessories-->Termianl type:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/disk-3 -o force
```

Then install ntfsprogs and run ntfsfix if there are any errors. 

After you've got your external drive back on line, it's time to check you other computers for root kits, just in case.

The tool to use is rkhunter for linux, and I'm sure you can find an appropriate tool for Windows.

Jim

---

### Post by komarue on 2008-10-27
cariboo907 - root kits / linux ntfs apps
Lord Xeb - windows

Thanks for the speedy replies!

Lord Xeb, I would, but it doesn't show up on any of the windows machines, that's the problem. Thanks though!

cariboo907, Thanks for the root kit / ntfs app pointers.

I let the drive sit for a day and now it won't even register in Linux anymore, I'll rip it out of the external case and see what happens when I hard wire it into my main rig. I'll post just in case people searching in the future come across the same problem. 

First time in 10 years had a hard drive fail on me. Guess I'll have to buy a new 1TB. 

Thanks again all.

Komarue

---

### Post by komarue on 2008-11-08
Well 

I managed to figure out the source of the problem, or at least narrow it down to the external cases circuitry. Apparently the power supply on the external hard drive went bad, overloaded the USB/Sata board in the case and fried it. The board flaking out like that caused the errors with the actual hard drive. I was able to remove the hard drive and put it inside my main machine. Simple forced chkdsk and its working beautifully. Very happy it was the case with the issue, and not the HD. Thanks for everyone's help.

Kom

---

