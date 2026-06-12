---
title: "nautilus dvd write speeds all wrong"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by taygan on 2006-06-08
Yesterday I was burning ISO images no problem, PLEXTOR DVDR PX-740A, it defaulted to 8x.  today my options are Maximum possible, 125x, 94x, 62x, 31x, 18x  ummmmm...  I did the security update today..

My PLEXTOR CD-R PX-W5224A still shows the correct 52x on down to 4x.

Any ideas how to reset this?

Device Manager on the CD-R (the working one) shows storage.cdrom.write_speeds list 9173, 7056, 5645, 4234, 3528, 2822, 1411, 706

Device Manager on the DVD-R (the broken one) shows 22160, 16620, 11080, 5540, 3324

I suppose I could mess with these, but I don't want to burn out the drive.  It WAS detected correctly before, but now is messed up.

(Clean install Dapper Drake 3 days ago.)

thanks.

EDIT: I wonder if everything is okay, and that the 125x is actually cdr for a 16x dvd?  It doesn't exactly match up with the other cd player though.

Things are still burning fine, it just doesn't look right.

---

### Post by mpvano on 2006-07-18
With the Nautilus CD Burner and Serpentine, or with cdrecord, my LG GCC-4160N Drive consistently burns at 4X instead of the correct 16X speed. This is not a media problem - the drive status reports this all the time.

I have the feeling that this problem has gotten worse since the last kernel update, but I am not certain.

I have tried changing all the places I could find that can affect the drive speed, but it makes no difference.

I think something's seriously broken in the driver.

As per my usual comment, the bug reporting system seems to be badly broken and I can't login (due to an apparent bug in "malone" for users with certain account information) so I can't report this bug to the "see-no-evil" developers!

I don't see any reports of this problem there, but there are reports of a similar problem "confirmed" there with dapper and DVD writers. I wonder if it has something to do with the difference in meaning of write speeds for DVD writers (they're 4 times as fast for 1X as CD writers)?

hope someone looks at this someday....

Mario

---

