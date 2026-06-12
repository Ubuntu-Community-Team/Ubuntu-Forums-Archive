---
title: "Wubi Install Taking 36+ hours?"
date: 2008-08-11
forum: General Help
---

### Post by heroimprisoned on 2008-08-11
Hey everyone.  I posted this in the install help forum, but haven't really gotten any useful advice yet, so maybe those of you familiar with Wubi can help me a bit more.

I choose to install using Wubi after tons of failures with almost any disc-based distro of Linux.  They always caused something to freeze up somewhere along the line.  Wubi worked fine at first, for the first time ever, and I was pretty stoked.

When my computer went to restart, though, I chose to boot into ubuntu to finish the install.  The process **crawled** like you would not believe.  36 hours later, my progress bar was sitting at 95%, looking for packages to remove, and I decided to restart because something was obviously wrong.

I ran JkDefrag on all my drives before running Wubi.  My hardware rundown is as follows:

AMD 64-bit 3200+
Chaintech VNF4 Ultra
2 gigs RAM
GeForce 8800GT
WD Raptor 74GB (the drive I was putting ubuntu on)
Maxtor SATA 300GB (storage)
Maxtor IDE 320GB (more storage)
Logitech G15 keyboard
Logitech G5 mouse

I figure that for an installation to take so long, there has to be some kind of hardware problem.  Someone on another forum suggested running wubi with the 32-bit installer to see if that would help.  Does anyone agree that would be a good choice?

The fact that live CDs don't work on this computer kind of leads me to think that there is some sort of hardware incompatibility issue at hand, here.  I really want ubuntu on this hardware, please don't condemn me to a life of XP.  Heh.

---

### Post by pytheas22 on 2008-08-11
> I figure that for an installation to take so long, there has to be some kind of hardware problem. Someone on another forum suggested running wubi with the 32-bit installer to see if that would help. Does anyone agree that would be a good choice?

Yeah, something really bad must be happening.  Normally it only takes about ten minutes for wubi to finish the install after it restarts the computer.

Installing the 32-bit version of Ubuntu is worth a try.  It's not likely to solve the problem, but it can't hurt.

Did you try the Ubuntu live CD.  If so, what happened exactly--were you able to boot to the desktop?  If it hung at a certain point, what was on the screen when it was hanging?  Did you get an error messages?

You could also try using the alternate CD, which uses a text-based installer.  This might help, if the bug that's the causing the problem is only in the Ubuntu installer, not Ubuntu itself.  To download the alternate CD, go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box that says, "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

Also, does wubi actually finish the installation after 36 hours?  Or did you just give up at that point?  If the installation did finish, were you able to use Ubuntu at all thereafter?

With some more information, hopefully we can sort this issue out and get your Linux working.

---

### Post by heroimprisoned on 2008-08-12
> **pytheas22 said:**
> Yeah, something really bad must be happening.  Normally it only takes about ten minutes for wubi to finish the install after it restarts the computer.

Installing the 32-bit version of Ubuntu is worth a try.  It's not likely to solve the problem, but it can't hurt.

Did you try the Ubuntu live CD.  If so, what happened exactly--were you able to boot to the desktop?  If it hung at a certain point, what was on the screen when it was hanging?  Did you get an error messages?

You could also try using the alternate CD, which uses a text-based installer.  This might help, if the bug that's the causing the problem is only in the Ubuntu installer, not Ubuntu itself.  To download the alternate CD, go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box that says, "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

Also, does wubi actually finish the installation after 36 hours?  Or did you just give up at that point?  If the installation did finish, were you able to use Ubuntu at all thereafter?

With some more information, hopefully we can sort this issue out and get your Linux working.

Thanks for your reply.  Let me give you a run down of what's been going on.

I haven't tried using a 32-bit version of ubuntu yet.  That's going to be my next attempt at a fix.  The ISO is downloading now, along with the alternate CD.  Problem is, I don't have any way to burn a CD.  Oh well, I'll figure that part out.

Whenever I try a live CD, it stops on the first progress bar you get, with the ubuntu logo right above it.  The bar moves really, really slow at first before just stopping altogether.  No error messages or anything.  EDIT:  This is true of basically every linux live distro I have tried.  Nothing loads on this computer, and I have literally no idea why.

I didn't let the 36+ hour install go.  I felt like it was really unlikely that it would work properly after taking so long.

Someone linked me this:

[http://forums.tweaktown.com/f69/sata-bios-question-26543/](http://forums.tweaktown.com/f69/sata-bios-question-26543/)

In the other thread, but I can't really figure out what it means to me and how I should adjust my bios settings.  I don't have a straight up choice between RAID/ACHI/IDE.  I'll try some things.

---

### Post by ago on 2008-08-12
While the installer is running you can press ctrl+alt+f2 to get a terminal and from there you can run system monitoring tools such as ps, df, top, free... and check where is the bottleneck.

---

### Post by heroimprisoned on 2008-08-12
> **ago said:**
> While the installer is running you can press ctrl+alt+f2 to get a terminal and from there you can run system monitoring tools such as ps, df, top, free... and check where is the bottleneck.

This is also a good suggestion, but can you be a bit more specific?  This is my first time using any *x, so I'm going to need a bit more hand-holding than usual.

---

### Post by ago on 2008-08-12
Quite simple, when the install runs slowly press ctrl+alt+f2, you will get a terminal where you can type commands. Just write a command and press enter (often q exits the command). The commands above give info on running tasks, memory, disk space etc... There are many commands to use and you can find several guides on the net.

---

### Post by pytheas22 on 2008-08-12
> Thanks for your reply. Let me give you a run down of what's been going on.

I haven't tried using a 32-bit version of ubuntu yet. That's going to be my next attempt at a fix. The ISO is downloading now, along with the alternate CD. Problem is, I don't have any way to burn a CD. Oh well, I'll figure that part out.

Whenever I try a live CD, it stops on the first progress bar you get, with the ubuntu logo right above it. The bar moves really, really slow at first before just stopping altogether. No error messages or anything. EDIT: This is true of basically every linux live distro I have tried. Nothing loads on this computer, and I have literally no idea why.

I didn't let the 36+ hour install go. I felt like it was really unlikely that it would work properly after taking so long.

Someone linked me this:

[http://forums.tweaktown.com/f69/sata...uestion-26543/](http://forums.tweaktown.com/f69/sata...uestion-26543/)

In the other thread, but I can't really figure out what it means to me and how I should adjust my bios settings. I don't have a straight up choice between RAID/ACHI/IDE. I'll try some things.

That's strange that no Linux live CD likes your computer.  What's the model of your motherboard?  There are a few that Linux doesn't like, but it's rare.

As per ago's suggestion, you might want to login on a terminal and see if you can figure out what's going on.  'top' is a good command to try (just type 'top' and press enter; press 'q' to quit); it will list system processes with the most resource-intensive at the top of the list.  Is there one process tying up all of the CPU or memory, and if so what is its name?

I'm thinking more and more that the alternate install CD might help you as well, so I'd give that a shot.

I don't think that the RAID/SATA stuff is going to help.  If Ubuntu were having trouble detecting your hard disk, it might, but I don't think that hard disk issues would cause the installer not to start at all.  So I wouldn't spend too long worrying about the hard-disk options in the BIOS.

Finally, one thing that may help is to unplug all non-essential components from your computer--sometimes certain pieces of hardware can cause problems.  Remove everything besides the keyboard, CD drive and motherboard.  If you can launch the installer then, then you know that it's some piece of hardware that's causing the hanging.  This isn't likely, but again, it won't hurt and I can't think of many other options beyond what's already been mentioned.

---

### Post by heroimprisoned on 2008-08-12
> **pytheas22 said:**
> That's strange that no Linux live CD likes your computer.  What's the model of your motherboard?  There are a few that Linux doesn't like, but it's rare.

As per ago's suggestion, you might want to login on a terminal and see if you can figure out what's going on.  'top' is a good command to try (just type 'top' and press enter; press 'q' to quit); it will list system processes with the most resource-intensive at the top of the list.  Is there one process tying up all of the CPU or memory, and if so what is its name?

I'm thinking more and more that the alternate install CD might help you as well, so I'd give that a shot.

I don't think that the RAID/SATA stuff is going to help.  If Ubuntu were having trouble detecting your hard disk, it might, but I don't think that hard disk issues would cause the installer not to start at all.  So I wouldn't spend too long worrying about the hard-disk options in the BIOS.

Finally, one thing that may help is to unplug all non-essential components from your computer--sometimes certain pieces of hardware can cause problems.  Remove everything besides the keyboard, CD drive and motherboard.  If you can launch the installer then, then you know that it's some piece of hardware that's causing the hanging.  This isn't likely, but again, it won't hurt and I can't think of many other options beyond what's already been mentioned.

My mobo is a Chaintech VNF4 Ultra Zenith VE.  I haven't seen anything to suggest that it's just linux incompatible, so I'm at a loss as far as that goes.

I attempted to use the 32-bit ISO through wubi and didn't have any luck with that, either.  The RAID setting also didn't help, big surprise.

I guess it's back to trying to use the alternate installer.  I just have to find a burner to use and I'll give it a shot, but I also have to repartition a HD somewhere along the line, I guess. Bah.  I was hoping to avoid that with wubi.  Oh well.

I'm going to run the terminal next time I install, I'll update with my results.

---

### Post by jimmyhacker on 2008-08-13
i can say WUBI "sux" or needs a new version?because i was downloaded the biggiest iso file?(aprox. 641 MB)and its not detects instalation files on virtual CD and i must download 715 MB and i have a limit of internet.On the installation i get some errors made by Monitor.i was downloaded xubuntu and i get same error.i think its made by my hardware configuration or WUBI haves?Pls post it to my inbox.

Sorry for my Bad english.

Regards.
Jimmyhacker

---

