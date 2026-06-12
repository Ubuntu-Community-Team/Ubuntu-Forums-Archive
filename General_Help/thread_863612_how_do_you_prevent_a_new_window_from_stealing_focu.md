---
title: "how do you prevent a new window from stealing focus? (gnome)"
date: 2008-07-18
forum: General Help
---

### Post by unebaguettesvp on 2008-07-18
for those of you not familiar with gnuplot:

how do you prevent a new window from stealing focus in gnome? is there a blacklist or something that i can tell gnome to not raise a specific window? in this case, gnuplot.

for those of you familiar with gnuplot:

i am launching gnuplot and then setting the term to x11 and then plotting sin(x). as the plot window pops up, it steals the focus away from the terminal. i really don't want that to happen because i'm using a ruby script to launch gnuplot. i tried "gnuplot -noraise" from the command line. that didn't work. i tried "set terminal x11 noraise". that didn't work either. i found this: [link]("http://objectmix.com/graphics/139281-control-gnuplot-via-popen-how-get-focus-back-caller.html"). i have the same problem. they suggested that it might be the window manager. but they didn't resolve it either. so, i went to compiz and turned off "Auto-Raise", set the "Auto-Raise Delay" to 0. that still didn't work. i'm out of luck. anything else i should try?

---

