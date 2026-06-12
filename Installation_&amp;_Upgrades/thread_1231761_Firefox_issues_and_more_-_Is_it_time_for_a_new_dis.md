---
title: "Firefox issues and more - Is it time for a new distro?"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by spaceboy909 on 2009-08-04
I've been using ubuntu off and on for 2-2 1/2 years now.  It has its' pros, but has it's cons too.  I've grown increasingly frustrated with running into bugs or roadblocks over simple things.

Anyway, recently, I upgraded my laptop from Ibex to Jaunty hoping that it would solve some of the glitches that were cropping up.  It seems to have made things worse.  The biggest thing is that it killed my wifi, which I had manually setup, which takes me 3-4 days to relearn how to do it every time I have to redo it.

On my Ibex desktop, apparently firefox was part of one of the recent upgrades, and now, the last.fm website won't work anymore and does not display properly, and neither does gmail, of all things.  I can get gmail to work if I switch it back to the 'old version'.

So, something about recent upgrades has killed my firefox gmail and last.fm, and who knows what else that I just haven't run into yet.

I would like to get this browser issue fixed, but honestly, I'm completely worn out on Ubuntu.  At this point in time I can safely say that I've had far worse of a time with Ubuntu than I've had with Windows XP, but I do want to be able to keep using linux for some things.

So, in addition to any fix tips for the above, I'm thinking about switching to Mandriva or PCLinuxOS and I'd like some opinions on the best, user friendly distro to check out.

---

### Post by ptn107 on 2009-08-04
last.fm and gmail work fine with Ubuntu 9.04 64-bit & Firefox 3.0.13.  You can try backing up your bookmarks and then do the following in a terminal to clear out your firefox profile:

```
rm -r .mozilla/firefox/
```

---

