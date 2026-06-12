---
title: "Disabling Focus Stealing Prevention w/o Compiz"
date: 2008-09-25
forum: General Help
---

### Post by lorenbr on 2008-09-25
I am working on an easy way to keep a terminal close at hand without it getting in the way.  I tried to follow the tutorials that embed one, but discovered that this old beat up machine I am trying to configure for ubuntu doesn't have the video chops for Compiz (or so it tells me), so I've settled on Tilda, which isn't so bad.

The problem is that when I hotkey it open, I then have to actually click on the window to give it focus so I can use it.  That really kills the convenience factor of being able to open the terminal with a quick key.  Off the Tilda wiki it says you need to "disable focus stealing prevention."  But I can't figure out how to do that.  From the googling I did, it looks like this can be done using Compiz, but as far as I can tell, even if Compiz is installed, it won't do ANYTHING unless the graphics card supports it.  So that option is out.  I checked out the forums, and the only thread I came up with ([http://ubuntuforums.org/showthread.php?t=298912](http://ubuntuforums.org/showthread.php?t=298912)) had no firm resolution one way or the other, and was over a year old.  I'm hoping that maybe with Hardy, or some there is a way to fix this?  Alternatively, if there is some way to get Compiz working, at least for the minor, non-graphical preference changes it provides...

---

### Post by fsando on 2008-09-26
Posting just to 'bump' this.

I have the very same problem with openoffice.
If compiz is disabled (ie. no desktop effects) and another openoffice window is alread open:

Opening a new window will generally open in front but without focus. This has all kinds of unfortunate implications as you write of do other things expecting it to happen in the visible window and not in some other NOT-visible window (and no telling which).

If the newly opened file needs some initial action (ie opening a data file that needs conversion, openoffice will present a dialog) then the dialog is not raised to the front. To activate it you have to activate any other openoffice window. It's as if openoffice has its own active/non-active stack irrespective of Ubuntu's

This is extremely annoying and sometimes even dangerous as someone described how he accidentally posted his logon/password in an im-session.

I've seen tons of posting regarding this some even marked as 'solved' though I haven't found anything that solves it for me yet.

---

### Post by qwertz333 on 2010-10-29
To avoid this behaviour that fsando described (new OpenOffice document opens in front but without focus), you must disable focus stealing prevention in Compiz:

CCSM - General Options - "Focus & Raise Behaviour" tab - set "Focus Prevention Level" to "Off".

 I've been having this same problem and this solved it for me. It is definitely a Compiz thing, because when Compiz is off and KWin is running (even with focus stealing prevention on), this doesn't happen.

Btw this doesn't only apply to OpenOffice - it also happens when I start some applications via keyboard shortcut or open their windows from the systray - they appear on the screen, in the foreground, but without focus. Turning off focus stealing prevention in CCSM solves all this.

---

### Post by fsando on 2010-10-30
> **qwertz333 said:**
> To avoid this behaviour that fsando described (new OpenOffice document opens in front but without focus), you must disable focus stealing prevention in Compiz:

CCSM - General Options - "Focus & Raise Behaviour" tab - set "Focus Prevention Level" to "Off".

 I've been having this same problem and this solved it for me. It is definitely a Compiz thing, because when Compiz is off and KWin is running (even with focus stealing prevention on), this doesn't happen.

Btw this doesn't only apply to OpenOffice - it also happens when I start some applications via keyboard shortcut or open their windows from the systray - they appear on the screen, in the foreground, but without focus. Turning off focus stealing prevention in CCSM solves all this.

I don't use compiz. In fact I don't use any visual effects at all so I don't think it has anything directly to do with Compiz.

---

### Post by courteous on 2010-12-17
Is it possible to set keyboard shortcut (or even ALT+TAB) to return focus to Tilda? 
[This HOWTO]("http://ubuntuforums.org/showthread.php?t=530764") doesn't resolve the issue of trying to give back the focus to Tilda.

---

