---
title: "Wraparound Workspaces?"
date: 2008-08-19
forum: General Help
---

### Post by fiddler616 on 2008-08-19
Hello,
I'm a big fan of workspaces. They're nice in general, but they're especially great (for me at least) when I'm learning Python--I get three columns, put the tutorial in one, gedit in the other, and the Terminal in the third. Being a picky Linux user, I don't like hopping from WS 3 to 1. I know it's a half second of extra work, but it just doesn't sit well. Don't ask. So what I was wondering was whether it was possible to either:
a)Have three workspaces in a triangle, or...
b)Have wraparound workspaces--hitting right from WS 3 sends me to WS 1, and vice versa. I'm sure this could be solved from the Cube, but I really don't want to use that.
Thanks in advance (if nothing else for putting up with my insanity :) )

---

### Post by el-mar01 on 2008-08-19
If you have the workspace switcher on your panel and you haven't got Compiz enabled then just over your mouse over the workspace switcher and roll your mousewheel .. im sure you could get to WS 3 to 1 quicker than half a second.

---

### Post by fiddler616 on 2008-08-20
That doesn't work...

---

### Post by 0g_Trans_Fat on 2008-08-20
If you are using compiz, Open up CCSM, go to General Options > Desktop Size, and change the Horizontal to 3.

If you arent using compiz, right click on the workspace switcher and change it to 3.

---

### Post by fiddler616 on 2008-08-21
The workspace switcher is on three.
Three by two, actually.
[] [] []
[] [] []
(ASCII rendition)
And every now and then when I'm trying to do something normal, like scroll in Firefox after switching workspaces, it'll scroll through the WSs instead of the maximized firefox...
Maybe this just isn't a hill worth dying on?

---

### Post by jmk123 on 2009-02-04
i know this is old, but count myself in the need wrap around workspaces crowd.  it kept me from gnome for years.  been when kde4 turned out to be a bit of a charlie foxtrot, i tried it out.
i count this as my number 1 pet peeve.  if you have a 2x3 and you are in WS #3 and hit -> it should go to #1!!!! mac osx goes to #4.  what's the point of having a 2d structure if you treat it like a linear array!?!?! 
</rant>

install compiz.  the desktop wall has a tick mark for wrap around.
now can someone please explain to me what the difference is b/w viewports and virtual desktops and workspaces?  i see those terms used all the time and i don't know the difference.

---

### Post by thundermonty on 2009-02-04
i don't know of any.

---

### Post by ZeroEx on 2010-01-07
sudo apt-get install compizconfig-settings-manager
Category: Desktop  (third one from the top for me?)
Feature: Desktop Wall

go to tab: Viewport Switching
check: Allow Wrap-Around

---

### Post by 1longtime on 2010-04-28
Any options for this WITHOUT using Compiz?

I just abandoned the Compiz "bling" due to heavy performance issues, but I miss being able to jump from workspace4 back to workspace1.

---

### Post by estragib on 2010-05-31
The [metacity developers decided against]("https://bugzilla.gnome.org/show_bug.cgi?id=89315") it. If you're willing to roll your own, there *is* a patch. I personally disagree with their decision and [rationale]("https://bugzilla.gnome.org/show_bug.cgi?id=89315#c19") but yeah well.

---

### Post by junk998 on 2012-02-20
To enable workspace switch wrap around in metacity, issue this command:

```
gconftool -s -t boolean /apps/metacity/general/workspace_switcher_keyboard_cycle true
```

---

### Post by ZeroEx on 2012-03-22
the gconftools line in the above post doesn't work the allow wrap-around is checked in ccsm desktop wall  Still no wrap-around in ubuntu 10.04  What's left?

---

