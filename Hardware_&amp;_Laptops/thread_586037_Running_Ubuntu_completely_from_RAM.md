---
title: "Running Ubuntu completely from RAM?"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by bdonkey on 2007-10-21
Hi all,

I was wondering: is there a way to choose to load Ubuntu completely into RAM sometimes? Something like the Live CD, but loading to ram only sometimes, with the distribution installed to the HD.

I'm hoping to do this so that on battery power, I can reboot into a mode that just fetches all the apps and everything into memory at boot, and then shuts down the hard drive. Of course, I realize that opening files and saving data would not be possible without some sort of temporary ram filesystem like in the Live CD, but this mode would be awesome for doing something like just surfing the web or watching a video, where loss of data isn't really a problem since only the web cache would be lost, etc.

I realize that I could also just boot the Live CD ISO from the HD, but I'd like the benefits of using the same apps and system as I do if I were to just boot normally.

Is this possible? Thanks in advance.

---

### Post by kidders on 2007-10-23
Hi there,

What you're describing is possible, although it would take some work to get it right. For one thing, your applications would have to be tweaked to leave as small a RAM footprint as possible, and their complexity may have to be reduced somewhat, to reduce their dependence on some of the more space-consuming external libraries ... assuming, of course, you don't have RAM to burn.

Essentially, you would need a small disk partition (or perhaps a CD or similar) to handle the initial stages of the boot procedure, create RAM filesystems & unpack a compressed minimal Linux install into them. From there, you would have two choices:[LIST=1]
[*]Set aside a small amount of internal hard disk space for use as virtual memory.
[*]Simply switch off your hard disks.
[/LIST]
#2 seems to be your preference, however the resulting system would become unstable if heavily loaded, so reasonably basic tasks (such as web browsing) would most likely be the limit of what you could expect to do.

As you mentioned, you *could* use a LiveCD to achieve the same effect ... and it would be capable of handling far more punishment ... but running Linux off an optical drive can be sluggish, and having to re-burn the CD every time you wanted to make an alteration to its content would get tedious very quickly, so I can understand why you might be attracted to a "RAM only" setup.

While Ubuntu is a great choice for many environments, I wouldn't consider it particularly suitable for your purposes, tbh. Something like DSL or Gentoo would offer you far more flexibility in terms of the total size of your system, and how RAM-hungry it is. Certain distros are specifically designed to allow you to create systems with very restricted hardware & technology support, so you could create something highly responsive that booted almost instantaneously, and left you with enough free RAM to actually do something useful with.

In your shoes, my first step would be to set aside some disk space, and use it to create a standard Linux system that was as lean as I could make it, while retaining any functionality I thought might be useful. I would then configure it as though it were already running solely in RAM, compress it, create an initrd smart enough to unpack it at boot time & give it a try. Incidentally, I don't see any reason why such a system couldn't be made to hold onto certain information (eg browser histories or newly installed applications) between boots, if you thought that would be useful. As part of the shutdown procedure, you could have the install rewrite the archives it was unpacked from when it booted up.

---

### Post by bdonkey on 2007-10-23
Thanks for the suggestions, kidders! I'll try looking at DSL and Puppy Linux, too. I'm just getting into linux after switching from windows, and I'm pretty excited about the openness of the system. I think Gentoo requires too much compiling, though ... :-/

Also, you brought up another cool point: the fast boot speeds. It'd be great to have a linux based instant-on minimal desktopt, just like the ones that some computer manufacturers are embedding into their motherboards for multimedia playback.

---

### Post by kidders on 2007-10-23
Hey again,

You're right about Gentoo ... and it's not even *close* to suitable for someone who's new to the Linux platform either. :-( The main reason I mentioned it is that its design would make it quite easy to create something very small and very tailored (as opposed to just being "small" and "tailored" hehe) to a purpose such as multimedia playback.

> **bdonkey said:**
> It'd be great to have a linux based instant-on minimal desktopUnfortunately, _instant_ on Linux would require physical modification of your motherboard. There are however various ways of radically decreasing the time it takes for a Linux system to go interactive (ie finish enough of the boot-up process to be able to respond to user input), but that's something to worry about *after* you've built a workable RAM-based OS.

---

### Post by fargle on 2007-10-24
A few years ago I did this with a Mini ITX system that I used as a server.  It had a low-power Via C3 chip in it, and we used it for storing my audio collection in conjunction with an Audiotron.  The wife loved it!

Anyway, this was running Trustix 2.0.  What I did was, installed from CD to the hard drive, but created the partitions at the end of the drive, and just big enough to install.

Then, I booted off the drive, but just to single user mode.  I then created a new partition at the front of the drive to hold the new startup volume and used the tar pipe trick "tar cf - . | (cd /newvol/system ; tar xf -)" to copy the whole hierarchy to a subdirectory on the front partition.  Then I had to fix some directories up (nothing in /dev, etc) in that hierarchy.  Once it was happy, I made a tgz file of it at the base of the partition called system.tgz.

Then the fun: I took the standard initrd startup script and put custom code in at the end that would create a tmpfs filesystem, mount the hard drive, untar the tgz file into it, and then do a pivot_root onto it to make it the system drive.  If you look at a standard script, that's basically what it does at startup - pivot_root from the initrd to the newly-mounted system drive.

There were lots of tweaks I had to do, but hopefully you get the gist.

For updates, when I would see that the system wanted to do updates, I would just chroot over to /storage/system (where the first partition was mounted by the ram-based system), which was the hierarchy I used to build the tgz file for the ramdisk, run the updates there, then leave chroot  and tar/gz it up to a new ramdisk archive and reboot.  It's also good to have a second ramdisk script that will load from, say, systemold.tgz with the previous system on it in case you screw up.

Hacky?  Yes.  But it worked very nicely for several years, and that was one power-sipping server with a low-power processor and no drive spinning 95%+ of the time unless audio was being played!

Hope this gets you started.

---

