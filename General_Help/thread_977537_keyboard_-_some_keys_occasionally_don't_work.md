---
title: "keyboard - some keys occasionally don't work"
date: 2008-11-10
forum: General Help
---

### Post by pshotton on 2008-11-10
I am experiencing regular problems with programs that expect keyboard input (xterm, Thunderbird compose window, etc). Sometimes (several times a day) I start typing and realise that half my keys are not working (always the same set). If I alt-tab to another window and back again, it all starts working fine, until the next time.

Just occasionally the program waiting for keyboard input hangs, and any other window that's also waiting for keyboard is hung too. Windows that aren't waiting for keyboard (like navigator windows) are fine. When this happens I can ctrl-alt-F1 to a virtual terminal and everything is fine. The only solution is to kill X; on restart everything is fine.

Running Ubuntu Intrepid 2.6.27-7-generic, 
X.Org X Server 1.5.2, radeon driver module (v6.9.0), on
ATI Technologies Inc M56GL [Mobility FireGL V5250] 
on a Lenovo T60p

Any help or suggestions gratefully received.
Thanks
Phil

---

### Post by pshotton on 2008-11-12
I've cured this by turning off Assistive Technologies. Must have turned it on accidentally when playing with new features in Intrepid. Everything is now fine.

Cheers
Phil

---

