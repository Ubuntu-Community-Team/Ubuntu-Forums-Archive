---
title: "HP netbook 110-3101sa - dead screen"
date: 2011-12-05
forum: Hardware
---

### Post by F.G. on 2011-12-05
the story so far...
my friend got a second hand HP netbook off ebay. it had Windows 7 starter, but wasn't working very well.  so we reinstalled it from the recover partition. after that it still wasn't working that well, so i put Ubuntu on it for him, installing it into the windows home partition, over writing it (there were already a couple of partitions taken up with 'HP tools' and recovery stuff). then ubuntu was working ok, flash is very choppy though, my friend tries to boot into windows (which is no longer there, but still appears in GRUB) and breaks the Ubuntu installation.

so, at his request I delete all the recovery partitions and install Mint 12 over the whole disk in a single partition. now everything is working fine. the netbook owner leaves it turned on, goes to the shops, comes back to find that the screen has gone blank. 

now the screen does not light up at all (no back light or anything). with hard reboots etc. the screen appears completely dead. but the netbook does sound like it is working. so, if anyone has any suggestions on what has happened, or how to fix this, i'd be very gratefull.
have i somehow managed to fry the GPU?? if so, is this OS related?? can using the wrong distro break my hardware??

thanks for all and any replies.

---

### Post by F.G. on 2011-12-06
bump.

surely some-one has an idea of why this screen is dead?? the netbook didn't suffer any physical trauma, so i'm a bit surprised that it would just die like that.

---

### Post by Mark Phelps on 2011-12-06
You said it wasn't working well ... but you didn't indicate what was wrong. How long did you use it before you installed Mint?

Don't have a netbook and all too often, new PCs are configured by the OEMs to use fancy SPLASH screens that don't tell you anything about what it going on.

See if there is a way to get into the BIOS and set it to NOT display the splash screen upon boot.  At least that way, you will see some messages scrolling and perhaps be able to see the last message that indicates why it won't boot anymore.

---

### Post by F.G. on 2011-12-06
thanks for your relpy.

when it arrived, with win7 starter, in general it seemed to struggle, being very slow to open stuff etc. flash didn't really work, and was super choppy.

it seemed better with ubuntu, (although my friend had some issues with codecs and such like, and broke the ubuntu installation).

when i left it with mint12 on it, it seemed to be working fine. i don't know how heavy the usage was before it broke, but it worked for about three or four days and was probably booted up at least a couple of times per day.

so i've tried tapping esc, f10, f6 and f2 while booting and don't get anything on the screen. when i say it's dead, i mean truly dead, no back-light, no text, nothing which is why i think it could be a hardware issue.

i plugged it into an external monitor to see what i could see while booting, but didn't see anything (i guess i expected to see a mirror screen of what should be going on if it was physically broken). so i either the os is stopping it from working or the gpu is.

---

