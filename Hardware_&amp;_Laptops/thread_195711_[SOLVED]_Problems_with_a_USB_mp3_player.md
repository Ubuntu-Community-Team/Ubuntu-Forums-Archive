---
title: "[SOLVED] Problems with a USB mp3 player"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by Eisenwinter on 2006-06-13
Hi, I have a 1GB mp3 player.
Everything is fine, it is mounted, I can add files and etc, there's only one problem, Ubuntu says there is only 18.4MB of free space, even if there are NO files inside the mp3 player's drive.

Is there a way to fix this, make ubuntu recognize the player has a total of 1GB space instead of 18MB?

Thanks.

---

### Post by JSchwage on 2006-06-13
Could you specify what kind of MP3 player you have? Otherwise I can't help you much here.

---

### Post by Eisenwinter on 2006-06-13
Samsung H.I.Tech (not sure if that's it, but that's what the box says)

---

### Post by g_rael on 2006-08-25
I had similiar problem with my USB sticks,
try this:

brouse to the stick's top level folde.
view/show hidden files, (activate)
refresh.

look for a "trash" file !

On my dapper drake, it doesn't properly delete... it just transfers to a trash folder.

---

### Post by zambizzi on 2006-09-06
OK, this gets us half-way there.  I was down to 2.4mb but was able to get back to 57mb after deleting the "trash" folder.

However, that's a far cry from 1GB - how can I make Ubuntu recognize all 1000mb and not just 57mb?

Thanks again!

---

### Post by szf on 2006-09-06
Is there any chance that there's a second partition on the USB drive for the remaining 900 MB? Is the ~50MB area a partition to hold the firmware for the device?

Btw... holding down the 'shift' key when deleting files in Nautilus will remove them completely - not move them to .Trash-username...

---

### Post by zambizzi on 2006-09-06
It's doubtful that it's the firmware partition since I can drop mp3s in there and play them on the device.

When I mount an external hard drive w/ multiple partitions it mounts them separately and I get more than one icon on my desktop (and listed in nautlius) so I'm skeptical of that as well.

There's nothing to indicate that either of these are possible.  Let me know if there's something else to look for.

One thing to note, I recently upgraded my Gentoo laptop to Gnome 2.14 from 2.12 and now it shows up there as 57.1MB as well - on 2.12 it was 998MB.  So, I think it's sufficient to say there's an issue w/ udev and this device.  I just don't know what it is.

Thanks for the tip on the shift key...I spend way too much time on windows at work...;)

---

### Post by szf on 2006-09-06
Hrrm, well that was shot-in-the-dark #1... have you tried re-formatting the device?

---

### Post by zambizzi on 2006-09-07
Ayup.

It's got a built-in utility for doing that, I ran it a few times...doesn't seem to make any difference.

It's funny, because I fill up the 57MB and fire up the device...the first thing it says is "Free space: 943MB...".

The little bastard!  :evil:

---

### Post by szf on 2006-09-07
I'm stumped.

---

