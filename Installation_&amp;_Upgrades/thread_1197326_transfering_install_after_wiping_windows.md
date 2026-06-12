---
title: "transfering install after wiping windows"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by daeiros on 2009-06-26
Hello. I've been playing around with Ubuntu for A while now and I like it a lot. I've recently decided/been forced(long story) to ditch Windows completely and expand my Linux partition. One small problem, Windows had all sorts of weird and useless partitions 3 to be exact and 4 is the maximum, so in order to make a swap partition, I had to do my Ubuntu install on an extended partition. So now my question is, how do I go about transfering my install to the newly freed up 50 gigs of primary without losing all the wonderfull programs I've downloaded and all my other stuff? Tried to get this one on my own but I'm still a bit gunshy with partitions after the last time when I was installing Ubuntu to start with and that funky program decided to stick a sliver of unformatted space in front of my windows partition and move everything down when all I told it to do was cut off the end so I could make one for linux, and ended up with an unbootable computer. Hopefully I havent already destroyed it again by wiping out those 3 partitions, but I guess I'll find out when I reboot, because my laptop doesn't like to hibernate properly. Yeah I think I'll make this a double question, any tips on how to fix the hibernation Issue? It tells me that the soft reset failed because the device wasn't ready, but after a reboot it does resume right where I left off, I would just like to be able to close the lid without having to reboot every time, and without killing my battery by leaving it on. Sorry for the long rambling post, but I'm pretty wired right now.

---

### Post by paul_be on 2009-06-26
If I were you I would back up all the stuff on the windows partition to an external drive, or the linux partition if you can.  Then use a program like gparted and delete the windows partitions and reformat them as one large partition using ext3 or ntfs or whatever you want.

Also if grub is your bootloader (not something on the windows side) deleting the windows partitions should have no affect on the linux installation

---

### Post by daeiros on 2009-06-26
That's already done, I have one big ext3 partition then an extended partition with my Linux partition and my swap partition on it. With windows gone and ALL my stuff transfered over into Linux, it's a tad bit cramped in here and I want to spread out into that nice big ext3 partition without having to use it as a second hard drive, I just need to move my install out of the extended partition and onto the primary since the extended wont let me resize.

---

### Post by paul_be on 2009-06-26
I wouldnt move the install of linux if it is working ok.  Linux does not care what type of partition (primary or extended/logical).  Only the MBR/Windows cares about this.

---

### Post by daeiros on 2009-06-26
Yeah, I suppose you're right, I was just hope to stretch out in that nice big new partition instead of having to use it as a second hard drive, my drive isn't really big to start with, and I'm currently running on less then a third of it for the OS and the swap combined, so it's a little cramped. In that case then, is there some way I can make it so the package manager will install to the other partition so I can put those real beefy programs on the big partition? Like I said, I'm still fairly new, I'm a fresh convert from the idiot-proof windows, and I don't want to fool around with things too deep till I learn a bit more, so I don't break anything.

---

