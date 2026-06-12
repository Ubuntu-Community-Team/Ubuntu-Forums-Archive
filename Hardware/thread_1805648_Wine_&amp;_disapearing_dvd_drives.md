---
title: "Wine &amp; disapearing dvd drives"
date: 2011-07-16
forum: Hardware
---

### Post by SatanSpawn on 2011-07-16
Hi new here, but not to Linux... however i am new the the idea of mounting removable media to the label of the medium... this seems stupid to me, however after a lot of goggling, i still can't seem to find a solution!

I"m going to assume that the fix for this will be really simple, and i just missed it!

ok I'm trying to read a dvd (movie) in wine, but the config has forgotten my DVD drive's location, so from what i understand i have to create a link to the cdrom/dvdrom in the 'dosdevices' folder.  OK when i tried this

```
sudo ln -s /dev/dvd d:
```

i get an error saying no way to open a block device... that used to work, b4 the whole mounted on labels BS...

ive tried other things, but i am at a a loss, any suggestions?

---

### Post by SatanSpawn on 2011-07-16
I said
> that used to work, b4 the whole mounted on labels BS...

meaning that the '/dev/dvd' was a link to /dev/hdc, or /dev/sr0 same as /dev/cdrom...
or am i totally off my rocker?

---

