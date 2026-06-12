---
title: "[SOLVED] Pidgin opening AWN"
date: 2008-09-05
forum: General Help
---

### Post by Dougie187 on 2008-09-05
Ok, So this is a really weird problem, and I am about 99% sure it doesn't belong in this forum, but I am not sure which one it belongs in, so if anyone wants to move it feel free.

Anyways, I am also about 99% sure this is something stupid that I did configuration wise.

The issue I am having is related to Pidgin. When I log into pidgin I have my Google Talk account, my AIM Account, my IRC Account, and my MSN Account. Out of all of those, my MSN is the only one that alerts me when I get new emails. Now, when I click the "3 new emails" thing, and then select "Open all mail" it opens Avant-window-navigator instead of a new tab in firefox. So then I get this awkward duplicate copy of AWN Floating on top of the other one that I have, and hotmail doesn't open.

Basically, I just need someone who knows where this setting is in pidgin, or how to change the way pidgin tries to open a website. Thanks!

---

### Post by Genius314 on 2008-09-05
I'm not entirely sure, but try checking in Pidgin: Tools>Preferences, then go to the Network tab, and click "Configure Browser." This should have the programs that are launched to check emails and websites in Pidgin, so it is probably here somewhere.

---

### Post by Dougie187 on 2008-09-06
I went into that, but that just opens up the Preferred Applications config window. And I have already messed with that enough to where it *should* just open a new tab in firefox, but it's not working how I would expect.

---

### Post by Dougie187 on 2008-09-06
Sorry, *repost*

---

### Post by overdrank on 2008-09-06
Hi and please do not create multiple threads on the same issue. Threads merged :)

---

### Post by Dougie187 on 2008-09-07
Just as an update.

I found out that its not just how pidgin handles the brower, because if I get a URL in an IM then it opens in firefox just fine, but only when I get the new email notification does it open an AWN dock.

I am curious if anyone knows how to go about finding all the programs that have been run recently, because I sort of think, that somehow there is a link somewhere that runs AWN, but I don't know what its called. Again I know this is a long shot, but maybe someone knows how to do it.

---

### Post by Dougie187 on 2008-09-07
Ok, so again, just an update.

I just found out that the issue appears to be with gnome-open instead of pidgin.
So if anyone knows how to change the way gnome-open works with html files it would be great for some help.

Thanks.

---

### Post by Dougie187 on 2008-09-07
Again!
Solved now.

The issue ended up being, some how a launcher got made called firefox that was told to run avant-window-navigator.

I just had to remove ~/.local/share/applications/firefox.desktop

---

