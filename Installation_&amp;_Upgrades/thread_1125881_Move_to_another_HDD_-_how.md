---
title: "Move to another HDD - how?"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Thanh-BKK on 2009-04-14
Hi.

I'm running Ubuntu Hardy as the sole OS on my machine (no dual boot, no Windows) and it's sitting on a 80 GB HDD. 

Now i got a new, larger, HDD and would like to move, or rather "copy", it there. So that i can take out that (fully installed and working) 80 GB HDD, put in the newer 120 GB HDD and have the identical system running immediately, just with more space.

What i am trying to do is upgrade to a newer Ubuntu version (9.04) and, in case it fails, all i need to do is swap HDD's instead of starting from scratch, which would take days if not weeks. Also, of course, having 40 GB's more won't hurt either even though the current HDD is only about half used. 

Under Windows i know of software that boots from a floppy or a CD and simply clones one entire HDD, including boot sectors, to another. I would now assume that Ubuntu can do the same as it can boot the entire OS from a CD..?

Or can i, alternatively (and maybe even faster?) do a plain fresh install on the new HDD and then copy all contents from the old "home" partition to the new one? Will EVERYTHING be in there, i.e. customized settings, installed apps etc?

I have been running Ubuntu as sole OS for a year now but still don't know too much about what's under the hood :)

Kind regards.....

Thanh

---

### Post by Unanimated on 2009-04-14
There is a utility that you burn onto a CD, and provides many options at boot, such as formatting hard drives and the like. I would assume that it would have something similar to 'cloning' an entire hard drive, though I've never used it myself. I think it's called 'Ultimate Boot CD' or something like that. I'm not completely sure, but you should Google it.

Also, if you just copy your /home folder, it will NOT have all your installed applications. Your photos, music, videos, and application SETTINGS will all be there, however.

---

### Post by Mark Phelps on 2009-04-15
Check out Clonezilla.  You can get it from distrowatch.com.

---

### Post by Jakey_TheSnake on 2009-04-15
There is a "Copy" option in Gparted. Boot from a LiveCD with both HDDs in, delete any existing partitions on the new, copy the old, paste it, and then just click/drag the bar to expand it to your full new HDD's size. 

Press Apply.

Unplug old HDD, boot from new. See if it works. If it does, might as well format the old one and have it as a strictly backup HDD. 

:)

---

### Post by Thanh-BKK on 2009-04-15
Hi :)

Thank you all for the replies. I am currently downloading CloneZilla, that looks promising (i used Norton Ghost back in the stone age) and seems tro do exactly what i need to get done.


In case it fails, how exactly would i do the "copying" in Gparted, or is that self-explanatory? I.e. i know how to copy FILES but entire partitions..? And, specifically, how do i make the computer "find" Ubuntu in the new HDD once connected as boot drive, i guess i need to at least install Grub on it, no? Or does Gparted also copy the boot sector?

And, last but not least, is that a graphical process or will i need to work in CLI? In that case i would need an instruction as i obviously can't go online to look up the steps while i'm about to do that on my computer :) I'm not shy to use the command line, just i yet don't have the "driving license" for it and am scared to type something wrong and shoot down my system which so far runs flawlessly :) All data by the way (apart from what's in "home") is on a separate physical HDD, so even hosing the system wouldn't mean data loss - still major inconvenience.

Kind regards....

Thanh

---

