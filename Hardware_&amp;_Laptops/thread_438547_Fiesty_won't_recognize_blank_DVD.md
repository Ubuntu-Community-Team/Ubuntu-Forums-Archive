---
title: "Fiesty won't recognize blank DVD"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by midlandman on 2007-05-09
Hi, I posted this in the "General" section without much results. So I thought I'd try here.
I'm trying to burn a data dvd ( a few AVI files) and I'm not having much luck. All I'm doing is wasting blank dvds.
No matter what program I use, all it does is close the dvd, and doesn't burn anything on it. So I'm left with an empty dvd that's closed.
If I put a blank CD in, a window comes on asking me what I want to do. But when I put a dvd in, a window comes on saying "Cannot mount volume...invalid mount option when attempting to mount the volume".
Can someone help me out with this? All I want to do is burn the AVI files on a DVD so I can install them on another computer.
When I try with k3b, when it click "burn" I get an error-"could not determine size of resulting image file". And it doesn't offer any resolutions at all.
As well, I notice that when I go to "My computer", it shows my file system and floppy drive, but no cd/dvd rom when I have a blank dvd in. But it shows with just a regular cd.
I tested my drive to see if the problem was with the dvd/cd rom itself, but I played a dvd without a hitch. But for some reason Fiesty doesn't seem to recognize a blank dvd.
Any ideas?
Thanks.

---

### Post by Foxmike on 2007-05-09
Well, open a terminal and copy/paste the following:
```
grep "dvd" /etc/fstab
```
Can you post the result?

---

### Post by midlandman on 2007-05-10
Thanks, Mike. But nothing happens when I paste that command into terminal.

---

### Post by midlandman on 2007-05-11
bump

---

### Post by babysteps on 2007-06-10
Here's something that's gotten me a little further in a similar quest to burn data to a DVD-R.  

[http://ubuntuforums.org/showthread.php?t=42085](http://ubuntuforums.org/showthread.php?t=42085)

"Ad Noiseam" instruction got my Sony DVD Burner to go being seen as just another USB device to becoming mounted. I've gotten to where in Gnomebaker the properties for the two CD/DVD devices to have abilities to burn everything except DVD-RAM, and yet, neither drives can actually burn a DVD.  The blanks are correctly seen, but the actual burning will not start.

Anyway, hope you have better luck.

---

