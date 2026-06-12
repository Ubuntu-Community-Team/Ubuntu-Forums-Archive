---
title: "Upgrade from 8.04 to 8.10 and a lump of now apparently useless computer bits...."
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by trentend on 2009-03-12
The upgrade from 8.10 to 8.04 appeared to go okay, unfortunately a restart gave a lie to that appearance.

My system is absolutely shredded, it would seem.

Initially boot didn't work because of the IOMMU problem.  Changing the bios sorted that out, but:

Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)

on the new kernel boot was a problem, but booting to the old kernel appeared to solve that problem.  Except x wouldn't start.

No problem, so I boot into recovery and try 

apt-get update && apt-get upgrade

This showed errors and stated that it was required to;

dpkg --configure -a

this went so far, but then aborted due to "too many errors".

xstarts (in low resolution) and progresses as far as asking for username and password, but at that point I have a lovely orange screen with a moveable mouse cursor and nothing else I can do.  Booting back into the recovery kernels wors, but I can't get dpkg to progress further.

I'm stuck.  There are a whole heap of settings (like messenger account settings) that I only have on this machine, and a stack of archives email.  I know I should have backed them up, but it's not practical. I should have stayed with 8.04, but I have bought some external soundcards that I need for a particular application, and they're only properly supported on later kernels....and I have 8.10 working nicely on a couple of other machines, and smoothly enough for me to reconsider my previous decision only to go with LTS versions on important (production) machines to be unnecessary.

...so here I am.  Perhaps went into the upgrade a little too relaxed and underprepared, and now I have a terrible mess that I don't know how to unwind.

I'm nothing like a Linux guru.  I have installed and used a number of desktop installations, and have setup some specialist linux server/appliances (webserver, mailserver, trixbox server).  I need to follow guides, though.  I don't know what I'm doing.

If anyone can give me an idea about how I might be able to repair this system (either back to 8.04, or forward to 8.10), so that I can use it and retrieve my settings and data, I would be grateful.

I appreciate this was an unwise gamble on the upgrade succeeding, without appropriate preparation. Let this be a lesson to you all. I. am. an. idiot.

---

### Post by trentend on 2009-03-13
Okay, no suggestions so far.

Is it possible to repair an existing installation by installing over the existing one? ie it would be necessary not to re-partition the drives.

I want to preserve, more than anything else, /home and particularly all of my firefox bookmarks, passwords, etc.

Any idea how I can copy that elsewhere?

I can boot up into the command line shell, but there are too many dependency errors for dpkg --configure -a to run (it aborts saying too many errors).

---

### Post by OrangeCrate on 2009-03-13
You can't back up on versions, you need to do a fresh install. I think the only advice that most of us could offer you, is to pick either 8.04 or 8.10, install it, and then leave it alone.

---

### Post by trentend on 2009-03-13
....sorry, inadvertent multiple post....

---

### Post by trentend on 2009-03-13
> **OrangeCrate said:**
> You can't back up on versions, you need to do a fresh install. I think the only advice that most of us could offer you, is to pick either 8.04 or 8.10, install it, and then leave it alone.

I think that's pretty much the assumption that I had arrived at.  Thanks for confirming it, though.

My big concern is getting all of my data and settings off the hard drive. It's a LVM partition with a separate boot partition.

I know I want to copy /home - will that get me things like my evolution configs? - there are old mail accounts that I'm not 100% sure of the settings (I know /home is the location for what's currently in my maildir), also I need my firefox configs, as it's probably the only place that I have passwords for certain sites stored - and it saves me a whole lot of messing about if I can avoid having to find them again.

I have a spare disk (or two) and some usb caddies.  How do I mount them to copy stuff (I'm predominantly a linux desktop person, although the command line isn't completely alien to me)?

Is it possible to install ubuntu to a new hard drive, and then recover the data from my LVM partion on the other disk at my leisure?

I know the data is there, I need to recover it in the easiest, safest, way possible.

Thank you in advance for any guidance anyone can give.

---

### Post by listener on 2009-03-13
If you just really need to access the data there, and are able to create (free up space for) a new installation... then you'd be able to mount the original installation's partition to access your data and retrieve it.  You could even try doing this from a LiveCD, really.  I'd say you do need a new installation, rather than trying to repair the existing one.

Once you've secured your data, you could just turn that partition into a data partition.  That seems the easiest way to go to me.

Good Luck

---

### Post by trentend on 2009-03-13
> **listener said:**
> If you just really need to access the data there, and are able to create (free up space for) a new installation... then you'd be able to mount the original installation's partition to access your data and retrieve it.  You could even try doing this from a LiveCD, really.  I'd say you do need a new installation, rather than trying to repair the existing one.

Once you've secured your data, you could just turn that partition into a data partition.  That seems the easiest way to go to me.

Good Luck

Okay, that's the direction I'm going to be heading in.

Do I need to do anything to the current disk to stop it booting?  I actually have some hot swap (I think) drive bays in the machine, so I'll slide it out, perform the new installation on a new disk, and then take it from there.

---

