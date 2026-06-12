---
title: "Printing from Firefox revisited..."
date: 2005-11-08
forum: General Help
---

### Post by canadianwriterman on 2005-11-08
Sorry to bring this up again, but I've been trying to get Firefox to print properly in Breezy and can't yet.

Black is fine, but colour is washed out. Colour prints fine in other apps. Here's what I've tried:

One post recommended a clean install because of a fix supposedly in the final release. Did a clean install, but it didn't fix the problem.

Deleted .mozilla file, but did not fix the problem.

Tried the gtklp solution recommended in [http://www.ubuntuforums.org/showthread.php?t=24850&highlight=gtklp](http://www.ubuntuforums.org/showthread.php?t=24850&highlight=gtklp).
However, there must be more to it than just DLing gtklp and changing the front of the print command to gtlk. Now I get an error message saying that it can't find a printer. Is there some further setup of gtklp needed?

---

### Post by Arktis on 2005-11-08
This isn't the same problem as the other user had, and so his fix of deleting the config files for mozilla would obviously not work for you.  The link you give is also to a topic concerning a separate problem, so the solution there may not help you either... it depends on where the problem lies.  I searched the forums a few times for your particular issue and came up empty.

I suggest you file a bug report.

---

### Post by canadianwriterman on 2005-11-08
[QUOTE=Arktis]This isn't the same problem as the other user had, and so his fix of deleting the config files for mozilla would obviously not work for you.  The link you give is also to a topic concerning a separate problem, so the solution there may not help you either... it depends on where the problem lies.  I searched the forums a few times for your particular issue and came up empty.

I suggest you file a bug report.[/QUOTE]

You're right, Arktis, the other posts have usually been because Firefox couldn't print at all. I was hoping that my problem, while not related, could be solved in a similar fashion. I'll also check the Firefox forums, but they aren't very good with Linux problems as a rule. Thanks.

---

### Post by Arktis on 2005-11-08
Good luck. ;)

---

### Post by irv on 2005-11-08
I am jumping in not knowing all the facts of the problem, but I know there is a problem with printing from firefox, Linux version, not the Windows verison. I am running Breezy 5.10 and the first time I tried to print from firefox I got a Postscrip error printing to a HPLJ 1300. The only way I could fix it was to install a HPLJ4 driver. This brings up the question; Could your problem be a driver issue and the way firefox handles printing through that driver. In other words, maybe you might want to try different drivers (older ones newer ones, etc), to see if it makes a difference.

---

