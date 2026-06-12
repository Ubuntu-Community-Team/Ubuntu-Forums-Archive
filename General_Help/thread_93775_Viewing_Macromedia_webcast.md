---
title: "Viewing Macromedia webcast"
date: 2005-11-22
forum: General Help
---

### Post by cavaughan on 2005-11-22
I wanted to watch the Earth to America recordings on AOL, but found that they don't work at all. As far as I can tell it's done through Macromedia Flash Player (which I have installed).

Basically, if you go to: [http://comedy.aol.com/tcf](http://comedy.aol.com/tcf)
can anyone get the content to play? If so, how?
BTW, I don't think this is something Windows specific as it works on my Mac OSX.

Thanks for any input.

Curtis

---

### Post by jmooney on 2005-11-26
This wound up working for me:

sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc

Then comment out FIREFOX_DSP="auto" and add the line FIREFOX_DSP="none"

# which /dev/dsp wrapper to use
## FIREFOX_DSP="auto" ## The default setting
##
## This is supposed to fix the problem with Macromedia flash plugin.
FIREFOX_DSP="none" ## Set by Joseph K. Mooney on 11/25/05
## ## Confirmed working on [www.abum.com](www.abum.com)


Of course, your could just change "auto" to "none" but, whenever I modifiy a config file, I like to leave a note to myself explain what I did, when I did it, why I did it, and if it worked.

but suit yourself.

---

### Post by cavaughan on 2005-11-27
Nope that didn't change anything. I should explain that Macromedia Flash Player seems to work fine otherwise. But on the site I gave you can watch video segments of a show. Part of it works - i.e., choosing the segment. But the videos themselves do not show. Why?
Maybe there's some sort of a plugin mismatch? I'm thinking maybe Macromedia Flash hands off the video to a certain player?

Curtis

---

### Post by Chris Tucker on 2005-11-28
perhaps the site uses a real video stream (windows media/realmedia/quicktime...) instead of flash, and everything around it is flash.
try installing mplayer and the mplayer mozilla plugin, and all video codecs available.
i could try this and tell you if it works, but my high speed isnt hooked up yet.

---

### Post by cavaughan on 2005-11-28
Thanks for the reply but I do have mplayer and plugin installed. 

It's not critical at all of course. But I was thinking there might be an easy fix.


Curtis

---

