---
title: "konsole python session not reading PYTHONPATH"
date: 2008-09-15
forum: General Help
---

### Post by croese on 2008-09-15
I'm running 64-bit Kubuntu Hardy and I've noticed that if I use Konsole's session function to make a python interpreter session, it won't pick up on my PYTHONPATH variable and so sys.path won't get any new dirs added to it.  I can open a normal shell instance and start python that way and this WILL pick up on var and add the dirs like normal (so I know I setup the variable correctly).  The only guess I have is that the python session is using an already running python process and so is skipping the whole var search part of its startup.

This is more of a convenience problem than anything since I can get it to work by going the slightly longer way, but I'd like to see if there's a way to change this behavior and make it a little easier to use (I'm a programmer and, hence, tend to go the lazy route for repetitive things and just use shortcuts :)).

Any ideas?

---

