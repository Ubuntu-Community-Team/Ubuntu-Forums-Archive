---
title: "Logitech G11"
date: 2009-07-13
forum: Hardware
---

### Post by SaxMeister13 on 2009-07-13
OK, let me say before I get flamed that I've done a LOT of searching, both on this site and on the Internet in general, trying to get this keyboard to work, and [this thread]("http://g15tools.nfshost.com/forum/viewtopic.php?f=4&t=67") is the only thing I could find remotely similar to my problem.

I'm trying to get a G11 (not a G15, it doesn't have the LCD) to work under Jaunty.  I installed through Synaptic g15daemon, g15macro, libg15-1, and libg15render1 (at this point, xev would show separate keystrokes such as "X86Launcher" instead of just duplicates of the F1-F8 keys).  Then, working loosely off the community documentation [(link]("https://help.ubuntu.com/community/LogitechG15")), I modified /usr/share/X11/XKeysymDB so that the special keystrokes in xev had appropriate titles - G1-G18.

Now the problem I'm having is that I can't seem to make the desktop register the G-keys.  I can go into, say, Keyboard Shortcuts and assign G1 to minimize, but when I exit and try G1 on an active window, nothing happens.  More to the point, this also means that in programs like ZSNES and Nexuiz (my new favorite FPS) I can't assign these keys to actions.

So close, but yet, so far...can anyone help me with this last problem?

---

