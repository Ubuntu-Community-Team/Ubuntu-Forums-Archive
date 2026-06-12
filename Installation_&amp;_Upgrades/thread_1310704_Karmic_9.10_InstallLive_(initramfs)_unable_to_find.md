---
title: "Karmic 9.10 Install/Live: (initramfs) unable to find a medium containing a live [fs]"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by PorcelainMouse on 2009-11-02
I burned the x86-64 installation/boot .iso to DVD media.  I choose "Try..." and then I get another splash screen.  Soon, that goes away and my monitor shows it switched resolutions.  The screen is all black/blank.  When I hit any key, I then see many "stdin: error 0" messages going back to the top of the text display.  Then a message from BusyBox tells about the 'help' command.  And, at the bottom it says: "(initramfs) unable to find a medium containing a live file system" .  If I type help I get the BusyBox list of commands.

Looks like this:
```

stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0

BusyBox ...
...

(initramfs) unable to find a medium containing a live file system

```

(I see this was reported three weeks ago about the beta, but no replies.  Must not have been addressed before release?)

---

### Post by PorcelainMouse on 2009-11-03
Sorry.  I just assumed that since I used bittorrent, I couldn't have downloaded a corrupt file.  I guess that's not true, though I'd really like to know how that could be the case.

---

### Post by Sinsinnati on 2009-11-18
I had a similar experience when beginning to install 9.10. Everything was the same up until the "stdin: error 0" output. The message that followed the second keystroke was in regard to "switching to secret passwords". I'm credulous with regard to torrents as well, but I suppose I'll give the mirror a try.

---

