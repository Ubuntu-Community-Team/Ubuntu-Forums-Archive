---
title: "Using LowMemorySystems wiki for a Fluxbox installation"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by mohapi on 2006-02-01
Rather than hijack the other Fluxbox thread (which has some snazzy photos in it, I might add), I opted to open another one.

I have been following the wiki for [LowMemorySystems]("https://wiki.ubuntu.com/Installation/LowMemorySystems"), but it seems to be missing a step or two.

After the server install and the *sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic*, a *startx* command gives an error message. Something about no X session, or something. I can't read the whole message.

However, as I understand it, I should create a ".xinitrc" file with

```
exec fluxbox
```
in it. It seems to work, but then the *startx* command causes an awful lag to start, and I never get past the X cursor. I can't get out of the lag except by CTRL-ALT-BACKSPACE.

What am I missing? :-k

---

### Post by mohapi on 2006-02-03
Once again I have managed to answer my own question, which just goes to show that I am far too reliant upon these forums. What can I say? I really dig the help I get here. (No sarcasm in that, either.) :mrgreen: 

It seems I just wasn't waiting long enough. As a troubleshooting measure, I did an identical setup on a Dell XPS M170, which is about 20 times faster than the old Compaq. The Dell lagged for a few seconds, then dropped me into the Fluxbox desktop.

I moved back to the Compaq, rebuilt the Fluxbox install and let it sit for about five minutes. It lagged and lagged and lagged ... and then up came the lovely blue Fluxbox desktop.

At the wrong resolution. But hey, who cares? It worked, didn't it? \\:D/ 

Cheers!

---

