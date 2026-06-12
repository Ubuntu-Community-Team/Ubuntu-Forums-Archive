---
title: "Copying text in a terminal keeping its colors"
date: 2008-07-18
forum: General Help
---

### Post by busante on 2008-07-18
Hi!

Pretty new to Ubuntu here and so far my experience is a pretty nice one.
One of the few things bugging me is that I'm unable to copy text in a terminal keeping its colors.  I think it should be possible because, in the case of urxvt, it's possible to ctrl-shift-leftclick on a certain char and it shows you certain attributes like foreground color, background color, boldness, etc.  I mainly need it for using with the screen+irssi combination to copy colored topics in the channels where I am operator.

Thanks for your time and for any help you can offer. :popcorn:

busante

---

### Post by schauerlich on 2008-07-18
> **busante said:**
> Hi!

Pretty new to Ubuntu here and so far my experience is a pretty nice one.
One of the few things bugging me is that I'm unable to copy text in a terminal keeping its colors.  I think it should be possible because, in the case of urxvt, it's possible to ctrl-shift-leftclick on a certain char and it shows you certain attributes like foreground color, background color, boldness, etc.  I mainly need it for using with the screen+irssi combination to copy colored topics in the channels where I am operator.

Thanks for your time and for any help you can offer. :popcorn:

busante

Terminals don't usually preserve formatting. Perhaps you can use color tags from within irssi to reformat the text once you get it copied into the terminal. See this page for color codes:
[http://www.irssi.org/documentation/formats](http://www.irssi.org/documentation/formats)

---

### Post by busante on 2008-07-18
> **EDavidBurg said:**
> Terminals don't usually preserve formatting. Perhaps you can use color tags from within irssi to reformat the text once you get it copied into the terminal. See this page for color codes:
[http://www.irssi.org/documentation/formats](http://www.irssi.org/documentation/formats)

Ah yeah, i know that page. Quite helpful when you try to customize your irssi, although irssi's documentation seems to be far from complete. My current workaround is using [http://scripts.irssi.org/scripts/topics.pl]("http://scripts.irssi.org/scripts/topics.pl") which records previous topics and is able to set them again. Was just hoping for a better (direct) solution, as urxvt seemed to be able to read the formatting when asked to. :-k

Thanks for your answer. :-)

busante

---

