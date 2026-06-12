---
title: "[SOLVED] Problems with relatively new HDD, but it's still somewhat usable...."
date: 2008-09-11
forum: General Help
---

### Post by Predator106 on 2008-09-11
Hi, I just recently RMA'd a Raptor that one of my molex connectors fried (because you could put this connector in upside down) so I got my new HDD, and it worked and everything and after about a month(right about now), I decided to move Ubuntu onto that faster (and bigger) hard drive. So after using the command cp -dpR source dest , the files copied perfectly, etc. I then reinstalled GRUB on the hard drive (well, more like installed, same thing though), oh and this was formatted to Ext3 by the way. I turned off all my hard drives (removed them from the boot order) but even after I disabled them it would still boot to Ubuntu and notice the other HDD as mountable, which if it was running as Ubuntu, it would be no other HDD's mountable.

Anyways, apparently when you disable it in my ASUS BIOS, from being listed, it still boots (wtf is the point of disabling it...).

So I unplugged all the ones but the Raptor (the one with the copied Ubuntu on it), I booted it up and set it as primary in the BIOS, my BIOS took an incredibly long time to boot, like a minute or two, it was "stuck" after it recognized my ram, and after it gets unstuck it says something about an external USB, I don't have any USB's plugged in at the moment.

So it booted to GRUB, I went to the entry that was from the previous one (which worked), and then Ubuntu is booted, as far as Usplash, and gets stuck and just keeps trying to mount the filesystem, but it never fails... 

The whole entire boot process, my HDD light is constant ON, and the only time I hear the hard drive move the heads is when it first boots up and fires up the platter.

Is this what happens if a format failed, because it seems like the hard drive doesn't know what to do or something... It's really weird, I even tried unplugging EVERY peripheral, and same basic problem... 

This is SATA by the way.

Also note, I never had the problem before I formatted, but the thing is, after taking a really really long time for the BIOS to recognize it, (I can mount it and read/write), but same thing I would assume. But this is, of course when I am booting from the old HDD, and the Raptor is just acting as a regular secondary mount.

This is the weirdest thing I've ever seen....

---

