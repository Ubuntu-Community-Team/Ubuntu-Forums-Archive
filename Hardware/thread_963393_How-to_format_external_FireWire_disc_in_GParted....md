---
title: "How-to format external FireWire disc in GParted...? Permissionproblem...?"
date: 2008-10-30
forum: Hardware
---

### Post by indiworks on 2008-10-30
I'm still new to Ubuntu (using it since 8.04) and would like to back-up the internal HD on my external FireWire drive. It was formated under OS X (10.3.9) using HFS+, I can copy to Ubuntu but I can't copy anything onto the FireWire drive ("The destination is read-only." and also: "The permissions of "Untitled" could not be determined.") See the attached screenshot for how this looks in GParted.

How can I format this drive under Ubuntu and for using it with Ubuntu? (I don't need to have it OS X compatible if this is not easy to to...)

Also: can you tell GParted to write zeros to a drive when formatting it? I'd like to do this with the internal HD before going for a clean install of the upcoming 8.10...

Thanks!

---

### Post by garyedwardjohnston on 2008-10-30
Try unmounting the drive before the format.

---

### Post by indiworks on 2008-10-30
> **garyedwardjohnston said:**
> Try unmounting the drive before the format.

Thanks for your answer! This works in terms of being able to format the drive...! But two problems remain:

* I still can't copy anything to the drive after formatting it with ext3 (was this actually a good choice for using it with Ubuntu for either back-ups and video editing?):
[I]
Error while copying "GParted_2.png"

There was an error copying the file into /media/disk.

Error opening file '/media/disk/GParted_2.png': Permission denied[/I]

And Properties > Permissions says: *The permissions of "disk" could not be determined.*

* The other remaining problem: when unmounting the drive it keeps spinning, the only way to shut it down is via the on/off switch on the drive, but this is not good at all... (Ejecting it under OS X used to spin down the drive as expected...)

Here another screenshot from GParted after formatting the drive.

---

### Post by indiworks on 2008-10-31
> **indiworks said:**
> I still can't copy anything to the drive after formatting it with ext3

I managed to reconstruct a solution someone told me about a while ago:

[B]Start Nautilus as root via the Terminal:

sudo nautilus[/B]

A new window opens and **through that window** you can copy stuff onto your FireWire disc - no more error messages!

Remaining problems:

- disc still does not spin down when unmounted

- this setup/restriction for FireWire use under Ubuntu 8.04 makes video editing *much* harder than it should ever be: I hope 8.10 fixes this...

There was a similar problem when trying to digitise video via Kino and FireWire: I first had to research some code and type it in the Terminal to get permissions to write to *my own* internal disc before I could digitise using the FireWire port - FireWire should be plug and play...! Why...?!

---

