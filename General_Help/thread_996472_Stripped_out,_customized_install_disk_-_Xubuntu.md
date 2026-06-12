---
title: "Stripped out, customized install disk - Xubuntu"
date: 2008-11-28
forum: General Help
---

### Post by JvSivers on 2008-11-28
Hi there,

I've been banging my head against a wall all day trying to piece together a customized Xubuntu (8.10) installation disk. What exactly I'm attempting to do is this:

I would like to put together a 'dumb' computer (actually, several), used as a demonstration/presentation machine for a particular bit of software we're working on (ok, not me *personally*). Ideally these machine's will have no extraneous software on them whatsoever, no OpenOffice, no power saving tools, not even FireFox if I can manage it -- all it needs are dirt basic administrative tools and our software.

The units we'd like to run these on are not hefty machine's. they're relatively generic all-in-one units (1GHZ VIA CPU, 512MB RAM minus onboard video) with ELO touchscreens. We've decided Xubuntu is probably the best namely because the touchscreen works out of the box and xfce is the lightest interface we could think of (I know it's not *the* lightest, but it'll do)

What I've tried thus far is as follows (and I am a bit of a Linux n00b so bear with me if I say or think something stupid):

[INDENT]- The first thing I attempted was [Recontructor](http://reconstructor.aperantis.com/) -- initially it looked, but after a while of playing with it it didn't seem to do quite what I was looking for. Although it looks good when dealing with a live-CD (albeit a bit confusing to work with at times), when making an "Alternative CD" (installation CD) it wasn't quite so useful. Perhaps I was doing something wrong, but all the documentation I was reading seemed to more-or-less ignore the alternative options (I'm assuming for a reason). Also, I'm aware of it's limited support for graphical tweaks in X.[/INDENT]

[INDENT]- After this the [Ubuntu Customization Kit](http://uck.sourceforge.net/) -- that got thrown own relatively quickly.[/INDENT]

[INDENT]- Took at a look at the Ubuntu minimal install CD (figured I should be able to replace gnome with xfce if I had to), but that didn't seem to do it as (I'm under the impression) it just downloads the packages from the Ubuntu repositories during the installation, instead of storing them on the CD. Even if I'm wrong on that one I'd still have to do a "alternative installation" on all the machine's?[/INDENT]

[INDENT]- Tried Instalinux.com, I misunderstood what that was intended to do, my bad.[/INDENT]

[INDENT]- I also read up on preseeding and adding premade preseed files to the ISO, mounting, and installing from there. Although, I did have some issues with that, namely that I'm a n00b, so my reaction to some of the instructions, both on the Ubuntu site and elsewhere, was something along the lines of "wot?". I'm honestly not sure if adding some well thought-out preseed files to an Xubuntu install CD would do what I'm looking for. And if so I'd need to strip out a whole chunk of default packages to which...I wouldn't know the name of*[/INDENT]

[INDENT]- Beyond all this just some misc googling has turned up nothing for me.[/INDENT]

So am I out to lunch on this idea? Is what I'm trying to do even going to work (or better yet making sense)? Have I missed anything in the steps I've taken? Or can anyone suggest something else?

Thanks for any help, and there is any additional information needed I'd be glad to supply it.

*Also, is there somewhere I'd be able to find a list of packages that can safely be stripped out of a default X/K/E/Ubuntu installation?

---

### Post by theRightNee on 2008-12-30
with those specs i don't understand why you don't install using the alternate cd and remove the files after  installation?

---

