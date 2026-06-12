---
title: "[SOLVED] Window focus handler breaks"
date: 2008-11-25
forum: General Help
---

### Post by jon.mithe on 2008-11-25
Hi,

I'm having a problem where my window focus goes strange.  Ubuntu starts up and everything is well, then half an hour, and hour, <insert random time period>, it breaks.  The problem is if I have multiple windows open 1 has focus (title bar goes coloured, text etc enters), I then click on another window (e.g. select a new email in thunderbird).  The new appliction gets the event (i.e. my email will open) but the window itself does not get focus (i.e. the previos window still has focus), so keyboard events etc are passed onto the old window.  This poses another problem becuase if 2 windows are overlapping, the top on being in focus, and I click on the one below, it does not get the focuse / come to the top.  The only way I can get windows to have focus is if I click on the title bar itself.

I dont know if this is a know issue, it seemed to happen yesterday after I updated my pc.  Although, I dont know what was being updated or whether that was actually the cause.

The only applications I have been using are eclipse (uptodate ganymede), thunderbird, firefox and the occasional console.

Anyone know of how to fix this?

My setup is dual screen via ati config pair modes.  Standard dual core dell pc, and a fully uptodate ubuntu 8.10.

Strangely enough, my sound has also been having issus since a few days ago.  Either it works, does not work, or works with a reduced quality and slows fades out over ~a minute to silence.  Stuck on this as well.

Any help would be great cheers,
Jon

---

### Post by CatKiller on 2008-11-25
Do you have Desktop Effects enabled? Compiz has an option to control whether clicking on a window gives it focus. Perhaps yours has been set to the wrong one?

If you have CCSM installed (*sudo apt-get compizconfig-settings-manager* if you haven't) you can change this setting on the General Options -> Focus & Raise Behaviour tab with the Click To Focus option.

Otherwise, you can change the focus behaviour of Metacity (the default, simple window manager) by running ```
gconf-editor
``` and looking for the */apps/metacity/general/focus_mode* key.

EDIT: Re-read your post, and noticed that it's an intermittent problem. These solutions may help you get the correct behaviour back after the problem's occurred, but I guess we'd need to know which window manager you're using to pinpoint the cause.

---

### Post by jon.mithe on 2008-11-27
Hi,

Thanks for the reply.  Yeah sorry forgot to mention, not using any 3D effects or anything, just a bog standard setup.  Oddly enough I havnt had the problem yesterday or today, so fingers crossed it has fixed itself!  Were a load of updates on th elast couple of days, maybe of of them fixed it.

Cheers, 
Jon

---

