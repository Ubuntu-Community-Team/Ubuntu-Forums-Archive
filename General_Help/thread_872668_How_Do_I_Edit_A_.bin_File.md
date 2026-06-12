---
title: "How Do I Edit A .bin File?"
date: 2008-07-28
forum: General Help
---

### Post by Mark76 on 2008-07-28
I'd like Cairo-Dock to start up with transparency already enabled (cairo-dock -F).  I tried doing it by editing the exec command in the .desktop file but that didn't work so I think I have to change it in the .bin instead.  The only problem is I can't open the .bin in a text editor.

And before anyone says; "use compiz-fusion" I like the icewm/ROX set up I have right now and have no desire to change WMs :p

---

### Post by BennBuntu on 2008-07-28
you'd need a hex editor (ie ghex2), but I think that's the wrong way to do it. you'll just see hex or  binary values. Need to find a config file or recompile from source.

---

### Post by BennBuntu on 2008-07-28
I think easiest way is to change the startup command, if the usual method's not working for you(I don't know ice wm), could you make a shell script to launch it with the right arguments?

---

### Post by Mark76 on 2008-07-28
Actually I'm using rox-session to manage my sessions. If you don't already know (and I've no reason to see why you should) applications are added to start up in Rox by dragging the app's .bin to a filer window and creating a sym-link.

It's a marvellously simple method, but *very* inflexible.

---

### Post by Yannick Le Saint kyncani on 2008-07-28
> **Mark76 said:**
> I'd like Cairo-Dock to start up with transparency already enabled (cairo-dock -F).

Hi Mark76, you could put $HOME/bin/ in your $PATH and have a small ~/bin/cairo-dock stub which would basically only contain :

#! /usr/bin/env bash
exec /usr/bin/cairo-dock -F "$@"

That's how I do it anyway. May it help.

---

### Post by Mark76 on 2008-07-28
Remind me where my $PATH is again.

Thanks :)

---

### Post by Yannick Le Saint kyncani on 2008-07-28
> **Mark76 said:**
> Remind me where my $PATH is again.

Well, you won't be able to use my solution without some basic bash understanding, so if you feel like trying it out, you should start looking for a bash tutorial and work your way up from there.

Beside, some basic bash understanding would be good at some point anyway.

---

