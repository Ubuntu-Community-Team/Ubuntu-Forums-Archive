---
title: "Adding Internal CDRW and DVD drive Manually"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by TheForkOfJustice on 2006-10-29
This is the story:

I installed Ubuntu. Out of two drives, only one (my DVDROM) is mounted because I installed Ubuntu from that drive. I believe that is a common issue.

My DVD-ROM is listed (and I believe this is everyone's case) as '/media/cdrom0' and not '/media/dvdrom' with what appear to be links called 'cdrom' in '/media' and '/'. I wish to change the folder to '/media/dvdrom' as well as all other necessary changes.

I also wish to add my CDRW drive which is not mounted in a folder by Ubuntu AND get both drives to load icons on the desktop when I put a disk in either.

IIRC, my DVDROM and CDRW are listed as hdc and hdd, respectfullly, in GnomeBaker. 

DVDROM looks like this in fstab:

> 
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
I realize I may have to do all of this manually. No problem.

I outlined it pretty well so can you tell me how to edit and add these drive mounts?

EDIT

And no, they are not automounting (for some reason).

---

### Post by garba on 2006-10-30
actually, there shoudl be no need to add static fstab entries for your cd/dvd writers/players anymore: try commenting out any reference to hdc and hdd in the fstab file, gnome should get the proper info through HAL.

---

### Post by TheForkOfJustice on 2006-10-30
Okay, my cdrw is the one that mounts in /media/cdrom0 and yes, it does create an icon on my desktop.

Now my DVD-ROM...that is another issue.

What is a DVD-ROM mount supposed to look like in fstab?

EDIT

**garba**

I was having drive trouble before I started poking at my fstab, so that's why I started the thread. HAL wasn't detecting when a normal CD was put in my DVDROM when it is capable of reading from one. I haven't tested an actual DVD yet but DVDs aren't what I'm worried about.

I'll have to look for my DVDs tomorrow and actually test that.

---

