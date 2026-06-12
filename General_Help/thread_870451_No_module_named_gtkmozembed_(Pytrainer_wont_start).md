---
title: "No module named gtkmozembed (Pytrainer wont start)"
date: 2008-07-25
forum: General Help
---

### Post by flogger on 2008-07-25
Hi I hope someone can help...

I have installed Pytrainer on a AMD 64 machine running Mint Linux's XFCE addition (it is the latest Beta but should be full release this week so seems pretty stable).

Pytrainer lets me use my Garmin GPS and record my training on the bike including routes taken, speeds, heart rate etc...

Anyway I saw in another post you could use Ubuntu's Repositories and install the Gutsy version in Hardy (which mint is based on).

I installed everything and the dependancies via Synaptic but on start up nothing happens. Running from the terminal I get this trace...

nick@nick ~ $ pytrainer
Traceback (most recent call last):
  File "/usr/bin/pytr", line 38, in <module>
    from pytrainer.main import pyTrainer
  File "/usr/lib/python2.5/site-packages/pytrainer/main.py", line 38, in <module>
    from extensions.googlemaps import Googlemaps
  File "/usr/lib/python2.5/site-packages/pytrainer/extensions/googlemaps.py", line 19, in <module>
    import gtkmozembed
ImportError: No module named gtkmozembed
 
I searched the net and found a suggestion to install firefox-dev to install gtkmozembed but I still get the same error.

Any help would be greatly appreciated. I am doing a new ride in the jungle round KL and want to know where I have been!

Nick

---

### Post by flogger on 2008-07-26
install....


sudo apt-get install python-gnome2-extras

---

