---
title: "Something is failing in move to Intrepid, and I'm thinking hardware"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by clanmackay on 2009-03-15
Hey friends,

I am experiencing problems in a move from Hardy to Intrepid, but I don't strictly think it's related.  Details:

I simultaneously changed out my monitor and pulled an old CPU from storage.  I had an Intrepid installation CD burned, and I tried to run the installer.  Always I would get the main installation menu, then the Ubuntu logo and progress bar, but after that the results would be inconsistent.  The monitor would lose a signal then receive a new signal; pretty sure that an acceptable resolution was being negotiated.  Then, failure: sometimes it would stabilize at powered-on black, sometimes it would stabilize at a corrupted screen display (mouse cursor and random-looking patterns.)

I thought at first it might be my monitor (my video card not being able to drive it, for instance) so I swapped it out for one that had previously worked in Hardy.  Still having the same problems.

I swapped in a Hardy drive.  That started, on a hd boot, with no problems.  Still failure on the install CD, though.  I tried it again (sixth time overall) and I did get the installer up (with that awesome graphic, painted by I-don't-know-who.)  I installed Intrepid over this old Hardy drive, as a new install, as it contained no data I needed and /usr/local and /home were full of junk and I figured a fresh install was faster then sorting out the mess.  :^)

I successfully installed Intrepid, removed the install CD, and booted.  Failure, every time.  Again, sometimes it would stabilize at powered-on black, and sometimes it would get to the beige background, with a mouse cursor, and the login sound (I set it to auto-login) would play.

I again swapped out the hd, to a very old Debian drive.  That started -- multiple times -- with no problem.  Swapping back the Intrepid drive, this continued to fail.

I thought there might be a regression problem in Intrepid, so I burned a Hardy installation CD and tried to boot off of it.  Same problem.

So, yeah.  There is obviously something very brittle with my setup, and I'm thinking video card at this time, but before I start swapping out more hardware willy-nilly (I would have to buy a new card, as the only old one I can find is -- wow -- VLB), I wanted to run it by all of you.  I trust these boards and you are, to put it mildly, much more friendly than anywhere else I could ask these questions.  :^)

Thanks!

---

### Post by tommcd on 2009-03-15
I don't think it is necessary to be swapping out hard drives unless you suspect a faulty drive.

It sounds like either your video card is bad or you are not using the correct video driver. Did everything work ok in Hardy before upgrading to Intrepid?

What video card do you have? And what video driver are you using? Boot up the 8.10 live CD and run **sudo lspci -v | grep - vga** to list your video card. And **lsmod** will list your drivers.

---

### Post by clanmackay on 2009-03-15
> **tommcd said:**
> I don't think it is necessary to be swapping out hard drives unless you suspect a faulty drive.

I agree, except that I wanted to see if the problem surfaced on previously-working installations.  Is there a flaw in my reasoning?  There very well may be.

> **tommcd said:**
> It sounds like either your video card is bad or you are not using the correct video driver. Did everything work ok in Hardy before upgrading to Intrepid?

This is what's really baffling.  Yes, it did work in Hardy, but in the interim this box was in storage (I was using Intrepid on another machine.)  So when I was doing the drive swapping, I was trying to determine whether it was a consistent failure of the video card when I tried to boot from something else.  And as far as I could tell, it *always* worked with the other drives.  This could be coincidence, but it would be a rather large coincidence.

> **tommcd said:**
> What video card do you have? And what video driver are you using? Boot up the 8.10 live CD and run **sudo lspci -v | grep - vga** to list your video card. And **lsmod** will list your drivers.

I *can't*, though, because (as I definitely should have noted) neither the 8.10 nor the 8.04 discs work as live CDs, either.

I'm really thinking video card at this point, unless someone else will steer me away.  The coincidence of the 100% success rate on the other drives is bugging me, though, so before I drive to Fry's....

---

### Post by cariboo on 2009-03-16
You more than likely have a problem with the video driver/monitor configuration. Intrepid uses a newer version of xorg-xserver. I would suggest starting in recovery mode and running xfix, once it is done select resume to continue to your desktop. Make sure you fully update your install before enabling the restricted video drivers.

Jim

---

### Post by clanmackay on 2009-03-22
When I try an Intrepid disk, the menu loads.  I can select the Live CD or the Installation.  I get past the Ubuntu logo with the KITT-style scan, up to the point at which the bar starts filling left-to-right.  It inevitably stops at 2.75 segments.  Here is what I've tried:

Both live and install for the following:
* Intrepid burned to a CD at normal speed
* Intrepid burned to a CD at 1x
* Intrepid 1x CD with "all_generic_ide=1" specified
* Intrepid burned onto a DVD-R, with and without all_generic_ide

I've tried both the integrated video card and a third-party PCI video card.  Both display graphics, but cannot get me past the point described.

I've unplugged every USB device other than my keyboard.

I've disconnected every hard drive and tried to run in Live mode.

I've used two different (internal) optical drives.

I've used a Hardy disk, which behaves the same, except that it stops at 2.6 segments rather than 2.7 (this has *got* to be diagnostically relevant, yes?)

My memory passes the memory test.  My CD MD5 hash is correct.  The CDs work on other PCs.

I thought that leaving the screen at the 2.75 segment point might do something eventually.  It did.  After twenty minutes, I was thrown to text mode, where appeared "BUG: unable to handle kernel paging request at DF783000", and a bunch of stuff that followed from there.

I have tried to boot off the hard drive onto which I previously installed Intrepid, in Rescue mode, to try cariboo's suggestion.  This, too, throws errors without getting to a graphical mode; namely, EXT3 inode errors and modprobe failures.  Pretty sure that install is toast, but I cannot, of course, re-install.  Is there a way to launch the CD in recovery mode?

What is left?  The motherboard?  A failure of *both* a DVD-RW and 48x CD-ROM drive, each of which worked fine in Hardy?  I don't have to explain how maddening this is.  In 1995 I bought a book at Best Buy that had a Slackware CD in the inside back cover.  Installing it was much like soldering a crystal radio together.  It's fifteen years later, and Ubuntu has always "just worked" for me.  Aargh.  I'm tired of soldering irons.

---

### Post by clanmackay on 2009-03-22
Oh, yes, wrong section, but is there a way to subscribe to email notifications of new responses in this thread?

---

