---
title: "[system crash] smplayer restore window"
date: 2008-10-27
forum: General Help
---

### Post by kakyoism on 2008-10-27
I have encountered a problem lately:
smplayer is the frontend of mplayer.
If I have two smplayer instances running at the same time with both videos paused, when I try to restore one of them, the entire screen is dead.
No keyboard input is working, including ctrl-alt-backspace, ctrl-alt-F#, etc.

The only way to wake up is a hard rebooting...

Help!

---

### Post by DaVince21 on 2008-10-27
Did you try changing the video renderer to something else? It's possible that the selected renderer can't open up twice and somehow chokes...

---

### Post by kakyoism on 2008-10-27
I used to use x11, but it gives me wrong aspect ratio.
Then I've been using gl or gl2 for a while, it's been working for half a year now. But the problem in my post just came up lately.

Anyways, I don't think such a problem should have frozen the entire window managing system, don't you think so?

---

