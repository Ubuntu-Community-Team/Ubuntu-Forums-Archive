---
title: "install kubuntu and mint single disk"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by stolatos on 2009-05-01
hi!
 
i'm a newbie in linux, but i have use ubuntu awhile, and now i want on a new disk to install kubuntu and mint but i dont know nothing about partition if anyone can point me thru the whole installation of kubuntu or mint (don't know which is better to install first), how should i partition the disk and when, and that grub can see both. in other words the whole process starting from the first distro.
 
and if that procedure can apply when installing 3 or more distros.
 
i would apreciate any help you all could give me.

---

### Post by tommcd on 2009-05-02
So this is a new hard drive with nothing on it? Is that correct?

You will have to use manual partitioning to set this up the way you want. First install Kubuntu (it really doesn't matter which you install first though). When you get to the partitioning part choose manual partitioning and create these partitions:
1 primary for Kubuntu's root (10-15GB if you have a lot of space, can be less if you don't)
1 primary for swap
1 primary for Min't root (10-15GB)
1 logical for a /data partition (the rest of the drive)

The data partition will be for all your data. This will keep Kubuntu's and Mint's home directories separate so all the hidden config files in the home directories don't conflict with each other. Both Kubuntu and Mint can share the /data partition.

Install Kubuntu's grub to the MBR. Install Mint's grub to the Mint root partition. Then add this to Kubuntu's grub to boot Mint:
```

title Mint
configfile (hdX,Y)/boot/grub/menu.lst
savedefault

```
Replace (hdX,Y) with whatever partition Mint is on. It will probably be /dev/sda3 if you partition like I said, which is (hd0,2) in grub.
There are other ways to do what you want to do that might involve different partitioning schemes and grub configurations. This is how I would do it. It is fairly simple. You could use my example to install as many distros as you have room for. You will just need to create more logical partitions for the root partitions of additional distros. They can all share the swap and data partitions. 
See this beginners guide for Ubuntu if you have not already:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
and Herman's guide:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

And welcome to the Ubuntu forums!

---

### Post by stolatos on 2009-05-02
yes is a new hard drive SATA 160GB (i would like to see how the partitioning end up)
 
i still have somethings that i don't get it:
1.- what does it mean by logical partition and why cannot be a primary, and just my document are gona be store in there?
2.-how i install mint grub to the mint root partition?
3.-and just by simply adding the code you gave me exactly as it is (of course just replacing hdX,Y), is enough to boot mint?
4.- and where do i have to add it exactly?
 
thanks for all the help so far

---

### Post by tommcd on 2009-05-03
> **stolatos said:**
> 
1.- what does it mean by logical partition and why cannot be a primary, and just my document are gona be store in there?
You can only have 4 primary partitions. So if you make 4 primary partitions you will not be able to create any new partitions in the future. A logical partition lives inside an extended partition. You can have many logical partitions inside the extended partition. There are many tutorials about partitioning on the net. For example:
[http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)
> **stolatos said:**
> 
2.-how i install mint grub to the mint root partition?

Hopefully Mint's installer will be polite and *ask* you where you want to install grub. Unfortunately, not all distros are polite. There are some installers that just go ahead and take over your MBR without asking you where you want grub installed. I always install Ubuntu with the alternate install CD because it gives you this option. I don't know if Mint gives you the option where you want grub installed or not. If Mint is impolite enough to take over your MBR it will likely pick up your Ubuntu install. So you would end up booting Ubuntu from Mint's grub instead of the other way around. This is not a problem. I just like to have control over which distro controls my MBR.
> **stolatos said:**
> 
3.-and just by simply adding the code you gave me exactly as it is (of course just replacing hdX,Y), is enough to boot mint?
Yes. The configfile grub entry will boot Mint as long as Mint's grub is installed to Mint's root partition and (hdX,Y)/boot/grub/menu.lst is the path to Mint's menu.lst, which it likely is since it is based on Ubuntu. This will chainload Ubuntu's grub right into Mint's grub, so that each distros grub will be automagically updated with kernel updates. I have booted Debian, Mandriva, and Arch this way and it works well. 
> **stolatos said:**
> 
4.- and where do i have to add it exactly?

Just leave a space at the very end of the file and add it at the very end of the file. For reference, here is the entry for booting Arch from Ubuntu's grub in my menu.lst:
```

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Arch Linux 2009.02 (on /dev/sda6)
configfile      (hd0,5)/boot/grub/menu.lst 
savedefault

```
Just out of curiosity....
Why do you want K/Ubuntu *and* Mint? They are pretty much the same thing. If you want to try something different, and learn more about linux, then perhaps consider a different distro. 
I would recommend Debian because:
Ubuntu is based on Debian, so much of the configuration files are similar.
Debian does not hold your hand with GUI configuration tools like Ubuntu. You will have to learn the "Debian way" and be competent with apt-get, aptitude, apt-cache, as well as generic linux commands.

---

### Post by stolatos on 2009-05-03
Well i don't have a very powerfull connection and i think downloading the distros would take a long time. My PC only have a CD reader so all i can choose from was k/ubuntu and mint 'cause they are LiveCD's.
And i first thought installing ubuntu, fedora, opensuse and mandriva (the last three where all LiveDVD's).
I wish to use debian, but i've heard it's kind of difficult for someone in the transition of migrating from windows to linux. but i'll try it someday

---

### Post by tommcd on 2009-05-03
Well, good luck with whatever distro (or distros) you use. I was thinking you could use K/Ubuntu as your "working" distro and perhaps Debian as your "learning" distro. Debian was the first distro I tried after Ubuntu and I learned a lot from it. 

BTW, Fedora, Suse, and Mandriva are all available as live CDs. You only need to download 1 CD to install them. You don't have to have the DVD. Debian only requires the first CD to do a complete install. You don't need all 20 Debian CDs. You can apt-get whatever you want after you install.
This article comparing Xubuntu and Debian Lenny may interest you:
[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

Write back if you need more help.

---

### Post by stolatos on 2009-05-06
thank you very much, all this will help. and i'll write back for any question it appears to me. and i wanna kow if there's a link where i can fully learn the basic of linux.

one's again thankyou very much

---

### Post by tommcd on 2009-05-07
> **stolatos said:**
> ... and i wanna kow if there's a link where i can fully learn the basic of linux.

There are many great sites with linux tutorials. The Linux Documentation Project has tons of stuff:
[http://tldp.org/](http://tldp.org/)
I learned a lot from reading through the tutorials at [http://www.yolinux.com/](http://www.yolinux.com/). 

This site really helped me to learn basic linux terminal commands:
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

