---
title: "No sound after Hoary upgrade (partly my fault)"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by Coutsos on 2005-04-29
Hi

Last night I decided to upgrade to Hoary, and after rebooting this morning (I had it downloading and installing the necessary packages overnight) I found that no sound was playing at all. After looking around a bit I found the unofficial ubuntu guide for getting sound to work properly ([here](http://ubuntuguide.org/#configuresoundproperly)).
After following that, I still have no sound. Except this time, if I *try* to play sound (ie, a song in Rhythmbox), I get an error "Could not open resource for writing" followed by "Could not pause playback" (previously, it would play but I couldn't hear anything).
Then I read somewhere that this was a problem with the newer kernel installed with hoary, and that using the old kernel would work fine. So I tried this but it seems that when I tried the instructions in the guide I ended up making things worse, so I still get those errors.

Any way I can at least fix things so that I'm back to the way things were right after the Hoary upgrade?
I'd rather not have to reinstall from my Warty CD's and then have to download all the Hoary stuff again if it's avoidable.

---

### Post by Coutsos on 2005-04-29
OK, apparently I've got *some* sound. I tried xine, and I did have sound in media played there (xine is set to use esd).
But still, no sounds from Gnome or Rhythmbox.

Any ideas?

---

### Post by Coutsos on 2005-04-29
Awesome.

I had nothing to do today, so I did a fresh install from a 5.04 ISO. I still had the no sound problem, but at least I didn't get the errors I had before. Looking through the thread stickied at the top, I found [this](http://ubuntuforums.org/showpost.php?p=142576&postcount=43) post, and clicked to turn off just the "IEC958 Capture Monitor" setting, and sound started playing immediately.

All I care about now is WHY?!

---

