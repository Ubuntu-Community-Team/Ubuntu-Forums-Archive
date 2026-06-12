---
title: "[SOLVED] DVD does not recognize in Windows after Ubuntu install"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by scruffybeard on 2007-11-10
Hiya everybody!

After enjoying a certain amount of success with Ubuntu on my laptop, I decided to slap another HDD in my desktop and do a dual boot there as well.

The problem is this. After installing Ubuntu to the new HDD, Windows does not recognize my DVD drive, at all.

Here's my basic hardware setup.
Primary IDE Master - Maxtor 80 GB - Windows System Drive - NTFS
Primary IDE Slave - Western Digital 80 GB - Windows Storage - NTFS
Secondary IDE Master - Sony DVD-RW
Secondary IDE Slave - Western Digital 40 GB - Ubuntu - ext and swap

The DVD drive works perfectly in Ubuntu, just not in bloody Windows.

The only thing I can speculate is that Windows completely ignores the secondary IDE channel since there is an unsupported file system. Am I correct in this assumption, or is there more to the story?

Also, mmc still shows the Ubuntu HDD, as well as the DVD, so I know Windows is at least aware of their existance.

---

### Post by Linicks on 2007-11-10
Do you use 80-wire IDE cables?

Are the jumpers hard coded (master/slave) or cable select?

Oh, forgot.  What happens if you disconnect IDE2 hard drive and just leave the DVD there as master - does MS find it then?

Nick

---

### Post by JBAlaska on 2007-11-10
If it's seen in hardware manager,it's probably what you think (unsupported FS),there are a couple of drivers that will allow windoze to"see" the ext3 partition.

explore2fs and Ext2 IFS For Windows are 2 that I know of.

For the DVD problem:
Check your jumper settings,then check your pre assigned drive letters in windoze for a conflict.

If that's all good,it may be that winblows does not like the mix, you might have to swap secondary drives on the IDE bus.

**Edit: Linicks, your a faster typist than I am lol**

---

### Post by scruffybeard on 2007-11-10
> **Linicks said:**
> Do you use 80-wire IDE cables?

Are the jumpers hard coded (master/slave) or cable select?

Oh, forgot.  What happens if you disconnect IDE2 hard drive and just leave the DVD there as master - does MS find it then?

Nick

I have no idea on the IDE wire, I just use the standard, cheapo ribbon that comes with the drives and such.

The jumpers are set, DVD Master, and HDD slave.

I have attempted them as CS, and it makes no difference.

As for disconnecting the IDE2 HDD, I wouldn't know, at that point, grub freaks out and won't boot. After using an XP disk to fixmbr, the drive is just ducky.

---

### Post by scruffybeard on 2007-11-10
> **JBAlaska said:**
> If it's seen in hardware manager,it's probably what you think (unsupported FS),there are a couple of drivers that will allow windoze to"see" the ext3 partition.

explore2fs and Ext2 IFS For Windows are 2 that I know of.

For the DVD problem:
Check your jumper settings,then check your pre assigned drive letters in windoze for a conflict.

If that's all good,it may be that winblows does not like the mix, you might have to swap secondary drives on the IDE bus.

**Edit: Linicks, your a faster typist than I am lol**

I'm not so worried about XP being able to see the Linux partition, but I will try it to see if that helps the IDE channel.

With the DVD, the drive letters are fine, and the jumpers are fine. As soon as I have a few hours, I'll rip apart the case to get the drives close enough together to try the Linux drive on another IDE channel.

Problem comes in that I have a huge case, and short ribbons. I would love to move the DVD down closer to the HDDs, but prying off the face plate of the case is a troublesome feat that I have only accomplished once. I still have no idea how I did it, but I'll tinker around a bit.

---

### Post by scruffybeard on 2007-11-29
**Bit of an Update!**

I had, for a bit, given up on running a dual boot on this computer. I decided last night to try installing Fedora, just to see if maybe things would work out differently.

I haven't the foggiest idea how this happened, but on hdc, which is my "linux" drive I ended up with the swap, ext3, and an NTFS partition after Fedora installed.

Low and behold, the DVD drive works in XP, even though Linux is sitting on hdc.

Now, I'm not a big lover of Fedora. I like the name, but I am having mad issues with pirut. As such, I will attempt to install Gutsy in it's place, keeping the small NTFS partition to see if that might not resolve this issue.

If this does not solve it, the other thing might be that I did not install the bootloader to the MBR, but rather to hdc, then I just change boot order in BIOS to access Linux.

Either way, we'll figure this out.

---

### Post by scruffybeard on 2007-12-13
Well, sort of. I figured out that the problem is with the bootloader. If anything other than the normal MBR boots Windows, then Windows won't recognize the DVD drive. Something about the mix just makes Windows sick, and since I am not the only user of this computer, Windows does still need to remain perfectly functional.

Things work wonderfully as long as grub is not the one to boot Windows. Thing is, if grub does boot Windows, the DVD drive will still work as long as the Linux drive is not attached. It's more bizarre nonsense from Micro$oft.

But fear not fellow open sourcers. Scruffy has a plan.

What I'm going to attempt is keeping the stock MBR in place, but having grub or lilo on a USB stick. I think this may be possible due to [this thread]("http://www.debianhelp.org/node/1116#comment-41435") from [debianhelp.org]("http://www.debianhelp.org").

This new idea will be the topic of a new thread since it really has no bearing on this thread.

Thanks for everyone who has helped with this issue, and I look forward to making things fun things happen once I get a nicely functioning dual boot.

---

