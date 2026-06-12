---
title: "Installing on ancient hardware?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by ve4cib on 2009-04-10
I have an old (read: "ancient") desktop that I would like to put Ubuntu (or any other Linux distro) on.  The specs are:

CPU: Pentium 1 @ 100MHz
RAM: 72MB (upgraded from the original 16)
HD1: 1.5GB
HD2: 6GB

The hardware is in good shape.  It's still happily running Win95 and serving as an answering/fax machine.  But I'd really like to be able to do more with it.  Like buy USB and Ethernet cards and have drivers for them.  And being able to look at the web without worrying that the antivirus hasn't been updated in... over a decade.

My biggest hurdle (besides the generally-ancient CPU) is that the BIOS won't boot from the CD-ROM.  And since pretty much all distros ship as bootable CDs that leaves me in a bit of a bind.

I'm honestly not sure what distro I should be looking at.  Damn Small Linux I know is designed to support older hardware, but I've found it to be less-than-pleasant to work with.

I've played around with low-memory installations of Ubuntu before; I've managed to create a usable desktop installation on a 2GB thumbdrive, so storage space isn't a concern.  I'm more worried about whether a 2.6 kernel will run on 100MHz, and whether or not 72MB or RAM is enough for Fluxbox and some applications.

So, to sum up:

1- how can I install a relatively-modern CD-based distro on a computer without CD-ROM-boot support?  I assume I need a boot floppy, so where can I find one (or good instructions on how to make one)?

2- what distro would you suggest as being the best to run on these limited specs?  I need something with a GUI (probably Fluxbox, though JWM is an option too).  Application-wise I don't need a lot: a web browser (Dillo probably), some sort of document-writer (will AbiWord run on such low specs?), CUPS, Samba, and a handful of other small apps.


I've been hunting around Google off-and-on, but I figured I'd toss the question out here too just to get some extra input.  Thanks for any and all advice you can give me!

---

### Post by spcwingo on 2009-04-10
You can try building slackware with jwm and only light apps, other than that I would say strip the machine for parts, or use it to learn cli (try an Ubuntu cli only install).

---

### Post by ve4cib on 2009-04-10
I'll look into Slackware as an option.  Another thought that occured to me was to use it as a thin-client and set up a server on another computer in the house that it logs into.  Slightly more work to set up, but it might eliminate some of the hardware limitations.

Ideally the system should at least mimic the same level of functionality as its current Win95 setup.  I don't need flashy graphics, but a basic window manager and a handful of basic applications are necessary.  Otherwise it's probably better just to leave it as Win95; it's got a printer hooked up to it, and as a word-processor/answering machine/fax machine it does a very good job.  I don't want to lose any of that functionality; I want to make it do that *and* more if possible.

Turning it into a cli box is simply not an option unfortunately.  Family members besides myself should be able to use it, and they're not the types to sit down and learn how to use Bash.

---

### Post by cariboo on 2009-04-10
I have DSL installed on a similar computer, I just tried it as an experiment, it seems to work well, I haven't turned it on for 6 months, but I seem to remember I had a bit of a problem getting an ISA nic to work on it.

Jim

---

### Post by marshag63 on 2009-04-28
How about Feather Linux?

[http://featherlinux.berlios.de/docs.htm](http://featherlinux.berlios.de/docs.htm)

MarshaG.

---

