---
title: "installing vista from recovery disc after ubuntu installed first"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by homeriq5 on 2009-01-06
I recently had to reformat my entire hard drive and had to install ubuntu first because I didnt have the recovery discs that came with my computer on hand.  I'm planning on installing windows from this recovery disc tomorrow, however I have some concerns about the installation.  Most of the dual booting guides I have found, such as the one available on pcmag.com, used just the regular vista cd's to do a clean installtion of their system, not from a recovery disc.  Will using the vista recovery disc that came with my system be any different?  Do I have to worry about it automatically erasing my ubuntu partition?  I have a sony vaio fw and I am using the disc that I made from the recovery partition from the hard drive

---

### Post by Immolatus on 2009-01-06
Thats a rough one. I'm not too sure about vista but I know xp HAD to be installed first on the drive. So, I think you'll end up just having to reinstall vista-->shrink it to make room for ubuntu--> reclaim old data from the recovery image you made from within vista.

---

### Post by Mark Phelps on 2009-01-06
Not having access to the "recovery disks", I have to guess ... but generally, such disks completely "recover" your original installation, that is, they restore the machine to the state is was in when you first unpacked it.  They do that by 1) wiping the drive, 2) creating new partition(s), 3) reloading the original OS + apps from a compressed image.

This can take HOURS to do, so be patient with it.

When done, you will most probably have to create your account again, from scratch.

If you want to save any files or favorites, best copy them off to an external drive or USB stick before you do the recovery.

And, yes, it will completely erase any Ubuntu installation you have on the box.

---

### Post by homeriq5 on 2009-01-06
you guys are right, the vista recovery disc that came with my sony did not give me an option to preserve the existing installation....damn.  I guess I'll hold off from installing linux again for a while, it seems like some of the hardware on my new laptop isnt supported yet anyway.

---

### Post by joroberts on 2009-03-04
Hi, Not wanting to hijack this thread but I'm new to all of this and just wondered if someone can tell me if you need to reformat your hard drive prior to using the recovery CDs to reinstall vista?

So far I've had errors because presumably it cannot work on the ext3 (i think) format of the drive to recover it? Error code is 0xd0000017. I believe it should be NTFS but i have no clue how to sort this out. I've looked on here for advice and this thread is as close as i can work out.

Could some one please post the 'easy' way to format the drive. I'm not worrried about losing ubuntu at the moment because i'm going to reload it as a dual boot (am finding that none of my other equipment will work with it; printer, ext hard drive, bluetooth dongle, wifi, channel4 catch up etc etc :( )

Thanks in advance for any help.

Jo

---

### Post by Mark Phelps on 2009-03-05
Without access to your "recovery CDs", all I can do is guess -- because they come in different versions.  

Some contain a full compressed image of the MS Windows OS, will completely wipe the hard drive, completely reformat it, and reinstall the entire system from scratch.  These typically take HOURS to complete.

Others only contain a boot image and actually restore the OS partition from a "hidden partition" on the drive.  These work a lot faster, but if you've wiped or overwritten the "hidden partition", they won't work.

If you have the first kind, you shouldn't have to do anything other than boot from the first CD. It should then take over and do everything after that.

If you're getting an error message when attempting a recovery, I'm guessing you have the second kind -- and if you wiped or overwrote your "hidden partition" with Ubuntu, you have no recovery option available.

---

### Post by mitch_77 on 2009-04-19
hi there, i'm sorry if i get into this thread but i have a question related to this topic:

i have jaunty on a toshiba a135 and i'd like to shrink it a bit to install vista (i know, i know.."why would you do that?"...i don't like that either but since this is my girlfriend's ex laptop, i want her to still play a bit with it...and, as i read somewhere.."chicks don't like ubuntu" :(...but anyway..)

i have those damn recovery discs and i was wondering if i can extract in some way JUST the OS...not all that crap that comes with it.

could that be possible? create in some way an .iso with just the OS? did anybody of you folks ever try this?

i have the serial so what i need is just the raw OS.

thanks,
mitch

---

### Post by Mark Phelps on 2009-04-20
Recovery disks are designed to restore a machine to its original state.  They're built by each OEM, and without access to the disk, it's impossible to say what's on it or exactly what it will do.

That said, my guess would be -- no.

And, be sure to use the Vista Disk Management utility to shrink your Vista OS, don't use GParted or the Ubuntu installer.

And, if you have more problems, don't keep hijacking this thread --  start a new one.

---

