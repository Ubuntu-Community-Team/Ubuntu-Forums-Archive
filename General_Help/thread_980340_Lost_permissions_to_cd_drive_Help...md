---
title: "Lost permissions to cd drive?? Help.."
date: 2008-11-12
forum: General Help
---

### Post by trendal.toews on 2008-11-12
I have been running this 8.04 since it came out and I recently stuck a unmarked cd into the drive to see what was on it.  It was a basic music cd.  Just a few tracks on it.  For whatever reason it wouldn't play of the cd so I copied one track to my desktop. Trying to play the track off the desktop crashed Audacious.  Now any cd I stick in the same drive I can't access.  It errors out with "You do not have the permissions necessary to view the contents of "cdrom1"."  When I right-click>properties>permissions I get "the permissions of cdrom1 could not be determined"....??   

Whats up here?

As I was writing this I though to try my other "DVD" drive. Tried multiple cds and now the other drive, same thing.

I think the music cd was just coincidence, it was acting funky before that, nothing I can really put my finger on, the user experience just seemed, well, "different". 

Thanks

---

### Post by cariboo on 2008-11-12
Check to see if your cdrom drive is still mounted, a simple:

```
df -h
```

will tell you if it is still mounted. If it is still mounted in a terminal type:

```
sudo umount /dev/scd0
```
or
```
sudo umount /dev/scd1
```

which ever one is you cdrom drive

See ithat gives you back control of your cd-rom drive.

Jim

---

### Post by trendal.toews on 2008-11-12
Okay tried your suggestion and it worked.  THANKS.  But then I tried the original cd and, same result.  So i got curious.  The original cd was a Ultimate Boot CD for windows that I was trying to copy and make a new one.  It appears like my Ubuntu doesn't like that cd.  I can view windows cds like sp3 install cd, vista install cd, but not the UBCD 4 win.  All the other cds i tried worked so, I'm calling it solved for now.  If i had another UBCD i would try loading it to see if it was the cd or the data on the cd.  I'll just use one of those lame windows machines to copy and make a new one.  :-s

---

