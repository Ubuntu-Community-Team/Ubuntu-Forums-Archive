---
title: "[SOLVED] Annoying Strange Lockup Issue"
date: 2008-10-28
forum: General Help
---

### Post by RobOrr on 2008-10-28
This has been happening for a while now (i think since around the previous recommended updates came through ~ 2 weeks ago) and its annoying, and odd. 

I'll be using my computer, firefox will have been opened and is normally still open when this happens, and my internet traffic drops to zero, both upload and download. after its dropped to zero, firefox locks up, i cannot click on my shutdown menu button, and I cannot load any new programs. the "starting firefox" / "starting azureus" etc shows up on the bottom panel, the process starts sleeping in the system monitor, and everything goes balls up. the strange thing is all the programs that dont use the internet work fine as long as they were already open when the thing happens. odd things i noticed in system monitor were that X-session-manager becomes uninterruptible, as does firefox, and a process called lsd-release which disappears quickly after i load the system monitor. Hardware wise nothing is overheating or anything like that, and the time it takes for this to happen after login varies between 20 minutes and 6 hours. also, using Ctrl Alt Backspace fails, it prints a few lines, the last one being boot local scripts, but doesnt go any further than this. It's a big puzzler for me, anyone got ideas?

---

### Post by RobOrr on 2008-11-11
Fixed by upgrading to 8.10 . I guess it probably did have something to do with the kernel change, but this is only a theory.

---

