---
title: "Convert .iso/.toc to plain old .iso"
date: 2008-10-09
forum: General Help
---

### Post by SethD on 2008-10-09
Dear forum,

I somehow ended up with a bunch of Audio CDs that were copied into a .iso/.toc combination. The .iso's aren't really valid iso images on their own, so they cannot be burned without the .toc files. I can use cdrdao to burn the .toc files in combination with the .iso files, but that's not how I'd like to go about dealing with these images.

Is there any program out there that will take my .iso/.toc files and convert them into JUST an .iso that can be burned on its own? I want to be able to archive the .iso images (without the .toc files) in a format that is a "ture" .iso and burnable in any machine.

Thanks,
Seth

---

### Post by _sAm_ on 2008-10-09
I have never had any *.toc files myself, but I have had music cd in *.iso / *.cue

It looks like you can covert the .toc file to *.cue using cueconvert([http://manpages.ubuntu.com/manpages/hardy/man1/cueconvert.html](http://manpages.ubuntu.com/manpages/hardy/man1/cueconvert.html)) 

Then you can use cuebreakpoints to rip the *.iso/*.cue to single music files(guide; [http://aidanjm.wordpress.com/](http://aidanjm.wordpress.com/)). 

But as I understand it, the *.toc is(just as *.cue) a layout of the data inside the *.iso file. It dont take much space, so if you want to have the cd in a iso format then I dont understand why you want to remove it.

---

### Post by SethD on 2008-10-09
Sam,

Unfortunately it's a little more complicated than that. I need these iso/toc files to be in a format that I can convert to something like .wav or .flac without having to burn them back onto CDs again. Is this possible? How can I get these into a format that will let me really work with them. My end goal is to be able to convert them to FLAC files, but I can't figure out how to do that without RE-burning them to CDs and then ripping them as FLACs.

Anyone else?

Seth

---

### Post by mc4man on 2008-10-09
have no experience working with CDemu but maybe do so research ect. Seems it should allow you to properly mount the iso's and then *maybe* rip and encode to .flac

[http://cdemu.sourceforge.net/index.php#news](http://cdemu.sourceforge.net/index.php#news)

---

### Post by cong06 on 2010-05-10
So there's no solution?
Only solution is to re-rip the disk to an iso?

---

### Post by dino99 on 2010-05-10
[http://ubuntuforums.org/showthread.php?p=9233120](http://ubuntuforums.org/showthread.php?p=9233120)

[http://cdrdao.sourceforge.net/](http://cdrdao.sourceforge.net/)

---

### Post by cong06 on 2010-05-10
I guess I didn't explain.

I've already ripped a CD to a *.toc and bin? file.
The problem is the CD has alot of scratches so whenever I try and rip it takes forever.
I don't want to have to mess around with re-ripping it (I'm using 9.04, so ripping it to iso is an option, if I have 10+ hours of the computer sitting and spinning).

So, do you have any idea how I can convert my already ripped file?
cdrdao doesn't seem like it will work, unless I missed something.

---

### Post by cong06 on 2010-05-17
what's the point of the *.toc files, if they **only** work with Brasero, and won't be converted?

I ripped the CD, but I can't convert it into something that can be used, and re-ripping isn't an option since the Disk is already destroyed...

---

### Post by dandnsmith on 2010-05-17
Without having tried it, and not having used this iso/toc, I be trying to loop-mount the thing to access the innards of the iso or, failing that, just burn a new CD, and do the rip from that.

Sorry to belabour the (possibly) obvious, and hoping it doesn't cause you to go mad at me,

---

### Post by cong06 on 2010-05-21
> **dandnsmith said:**
> Without having tried it, and not having used this iso/toc, I be trying to loop-mount the thing to access the innards of the iso or, failing that, just burn a new CD, and do the rip from that.

Yeah, those are good suggestions. I never figured out how to "loop-mount" but the "burn a new cd and rip that" would have worked if I had been patient enough.
I deleted the original (toc) rip. I'll get that iso somehow.

---

