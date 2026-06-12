---
title: "Is WUBI More Strenuous On the Hard Drive Than a Native Installation?"
date: 2013-12-14
forum: Hardware
---

### Post by LillyDragon on 2013-12-14
I'm asking this here because I really have no idea what else to look for, so I'm going to ask some of you guys on the Ubuntu forums about it. Sorry it's a wall of text, but it had to be said.

I have been using WUBI for over a year and a half, because I didn't want to mess with the partition table on my laptop. (Silly recovery partitions, just give me the disks!) I noticed the hard drive would be a little warmer while booted into Linux, but didn't really think anything of it, until I recently got more noise coming from the hard drive itself.

This made me panic so quickly, I thought there was something caught in the fans. After disassembling my laptop for the entire night and putting it back together after cleaning out the fan, that wasn't the source of the noise. It was actually coming from the hard drive, and if some of the guys on Sonic Retro are right, the bearings are likely the issue.

Again, I thought maybe the motor was just getting a little aged, so I let it go too, until the noise got worse. I've been booted into Windows since then, where the hard drive isn't as stressed, apparently. I still get some noise, but it's not as dangerous now. To be on the safe side, I still ordered a new hard drive replacement, (Exactly the same model and specs as my old one, just a smaller capacity; desktops are better for archiving anyway.) and will install Ubuntu on it, while keeping the original hard drive encase I ever need Windows for some reason.

[CENTER]***[/CENTER]

However, I am concerned the next hard drive will get warm too, and I don't like the idea of replacing my hard drive every two years, when they usually last so much longer. I understand WUBI doesn't quite get native speeds since it's all happening inside a virtual loop disk partition inside a real partition, which is slower; I'm beginning to think this also means more stress on the hard drive, and the tiny amount of fake swap space probably caused a lot of unnecessary access as well.

So long story short, will a real, bare-metal installation of Ubuntu be much easier on my hard drive, or is there a common power management issue I'm overlooking? It's a recent HP laptop without the weird Intel/ATI hybrid graphics setup, and the only workaround I needed was a GRUB boot parameter for allowing the OS to adjust screen brightness.

---

### Post by oldfred on 2013-12-15
I do not know but wubi is just a file inside the Windows NTFS partition. NTFS does tend to fragment files where Linux formats write entire file every time but then they may be scattered all over drive. The fragmenting may be an issue and that is why with Windows defrag is often suggested. But it then moves all files to beginning of drive, both data & system. 

If a new partitioned install I might suggest a smaller / (root) partition of 10 to 25GB so all system files are closer together and the rest of the drive as /home (and some swap). 

I would backup /home and make a list of installed applications with dpkg so you can easily reinstall all apps.

---

### Post by LillyDragon on 2013-12-15
If that is the case, then that would explain the extra stress on the hard drive. A Linux OS trying to write files as it does normally while sitting inside a fragmenting NTFS partition, and I have never defragmented this hard drive once in the past two years that I have owned this laptop. On Windows it boots and runs at optimal speeds thanks to CCleaner, so I didn't see the need; that may have been a fatal mistake.

It won't do this on a fresh hard drive dedicated only to ext4 partitions, however, so I hope it stays relatively cool. That arrangement sounds like a great suggestion, and would still allow room for one more partition if I wanted a Windows dual-boot. I may give /root 20GB for native programs, 80Gb to /home, and 6GB to swap. (Since I have 3GBs of RAM.)

And it's a good idea to backup Home too, but booting back into WUBI would mean lots of scary noises from the HDD again. However, I do have packages of all my favorite programs, printer/scanner drivers, and games backed up to an ext4-formatted 16GB USB flash drive, so besides hunting down a handful of dependencies and PPA's again, reinstalling programs shouldn't be as overwhelming. :)

---

### Post by LillyDragon on 2013-12-21
I have talked to more people on other web forums about this, and there is honestly no way WUBI is at fault here. So I may label this as solved unless others have thoughts to chip in.

The hard drive gets no more warmer on Windows than it was on Linux, now that I'm staying booted into the former, and I have learned HDD's will not push themselves harder to reach data more quickly. So even if my partition is heavily fragmented, it only affects performance and not the longevity of the drive itself.

Someone even suggested wiping a hard drive over defragmenting it, which is much faster if you have everything backed up. Although on Linux partitions (Or at least their drivers, as someone said. Fragmenting on Windows partition formats is actually a legacy feature to maximize storage rather than a bug.) fragmentation doesn't happen, so that's one thing I won't have to worry about. And if I got an SSD in the future, fragmentation on either OS is completely irrelevant since there are no physical moving parts to reach any sector.

On the topic of the HDD itself, the bearings are most likely the source of the noise, so it is dieing and needs a replacement. The payment for a new one cleared a couple of days ago, so it may arrive in a few days.

---

### Post by LillyDragon on 2013-12-26
So, in an unusual turn of events, it turns out the noises were actually coming from the [caddie being a flimsy piece of plastic](http://www.overclock.net/t/1194055/dampening-hard-drive-noise-annoying-hum-hum-hum#post_16093382); it must be flapping like a playing card in tire spokes, which obviously resonates through the whole laptop case. Both HDDs are most likely still fine, so I'm marking this as solved while I try to figure out how to fix the caddie.

I can't believe I over-thought this issue so dramatically, because the noise does not match any scary sounds I found online of failing Hitachi hard drives at all.

---

