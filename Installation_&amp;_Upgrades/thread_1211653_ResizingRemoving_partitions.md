---
title: "Resizing/Removing partitions"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by bondmatt on 2009-07-12
I dont think I will be brave enough to do this for a while if it would work but I am curious enough to ask. Can I remove the Vista backup partition on my hard drive and give the space to linux without a complete reinstall of Vista? I dont really mind reinstalling Ubuntu. Right now I have a 320gb hard drive with a 225gb Vista partition, a 75gb Ubuntu partition and a 20gb Vista backup partition (rough estimates on sizes).

Can that partition even go without 'terminating' vista (said PCLinux: 'hasta la vista, Vista')? Last time I took out Vista (by installing PCLinux) that backup partition did not back me up in any way. I called upon it in my hour of need only to be left on my own.  Luckily, I didnt put all my eggs in one basket and had made back-up-discs which were actually useful. However, I have lots of engineering software in Vista (CAD programs, FEA software, etc.) that were legally obtained (student versions) and I suspect that I would have a great deal of trouble reinstalling them.

What about the bios options? My bios doesnt seem to have an settings that can be edited.

Any enlightenment would be appreciated,
- Matt Bondy

---

### Post by peakpc on 2009-07-12
If you have already made your Vista Backup disks then your backup drive has no further use and you can use the space for Ubuntu if you like.

---

### Post by Revolutionary101 on 2009-07-12
I don't suggest resizing the Ubuntu partition because the last time I resized the Ubuntu partition, I had to reinstall it.

---

### Post by Mark Phelps on 2009-07-13
If your Vista came preinstalled on your machine and you want to be able to restore it at some future point, you should check with your machine vendor before you remove any partitions. 

Depending on how they configured your system, even though you have a recovery CD, that partition might still be needed in order to restore Vista, because sometimes, all the recovery CD does is boot you into a recovery environment (WinRE) and uses the image stored on the hard drive to do the actual recovery.

---

### Post by bondmatt on 2009-07-13
Now that you mention it Mark, when I ran the last recovery the discs were used to fix whatever went wrong with that partition (I think the problem was the master boot record) and then that partition was used for the recovery. As far as I recall, everything in that partition was rewritten but Im not sure if the discs could recreate it. Certainly not something I am brave enough to experiment with.

Thanks,
- Matt Bondy

---

### Post by vdawg on 2009-07-13
Man, UWindsor represent!

Anyways, if you don't really need the space I recommend you leave things be. The safest way to use that 20Gb would be to use Partition Magic (in Windows) and give it to vista instead of ubuntu.

Partition Magic is the best software that I've ever used when it comes to this stuff but maybe someone here may be able to help you with fdisk...

Edit: Just played around with gparted, it has a similar interface to Partition magic, but I don't know how good it is...

---

