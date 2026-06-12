---
title: "new window don't have focus"
date: 2008-08-21
forum: General Help
---

### Post by mod-jkl on 2008-08-21
Hi,

I'm using ubuntu 8.04.1 and have the following problem: sometime, when a new window is created, it appears behind the current window that have the focus.
It often appears in the following configuration: I'm reading a mail in thunderbird (the mail has its own window, it is not in thunderbird main window). Then I launched a new firefox window and this window appears behind the mail window (note: te firefox window starts in full screen mode).

Is this a known bug ?

---

### Post by Sycron on 2008-08-21
Can you give me a screenshot ? Are you sure that thunderbird is not always on top ?

---

### Post by mod-jkl on 2008-08-21
I can try to do a screen shot tomorrow (I'm on a xp pc now).
In this sample, thunderbird is on top, then a firefox window is lanched and it appears behind the thunderbird window. What you see then is thunderbird and behind, firefox.

---

### Post by mod-jkl on 2008-08-21
And yes, thunderbird is not always on top (most of the time, this behaviour doesn't happen)
If I click on  the firefox window, it comes on top

---

### Post by Yleeyas on 2008-10-03
Hi mod-jkl,

I was having the reverse problem  with FF 3.0.3, and found there is an about:config preference called: browser.tabs.loadDivertedInBackground

Set this to 'false', and see if that doesn't solve the problem. (you may have to restart FF, I can't remember)

Good luck.
yleeyas

PS: Do you have any other applications running with 'always on top' enabled. This seems to be causing problems with window focus functions.

---

### Post by krazyman on 2009-02-25
I see this is a few months old, but I'm getting this as well. If I go CTRL-N in Thunderbird, the window is on top, but not focused, so when I start typing, nothing happens until I click the window title bar (ggrrrrr!!!!!)
Also, If I use the firefox quicklaunch button in the top panel (gnome here), firefox starts minimised, with the taskbar button flashing for attention.
This also affects flash player fullscreen mode. I have to minimise firefox to see my fullscreen video... Took me a while to work that one out!
mod-jkl, did you get it fixed in the end? If so, how?

---

### Post by mixmaster on 2009-02-25
Check your windows preferences to make sure that you do not have 
"Select windows when the mouse moves over them" 
set.  This will cause the focus to behave unpredictably for someone not used to that setting.  Personally I much prefer it and I hate applications which insist on stealing the focus during initialisation.

---

### Post by krazyman on 2009-02-25
Negative captain...

---

### Post by Yashiro on 2009-02-25
Are you using Compiz or Metacity Window Manager?

---

### Post by krazyman on 2009-02-25
Nope, standard gnome.

---

### Post by auklet2k on 2009-08-08
I had found this solution for your problem. Actually I was annoying by this issue for a while. Thought it was fault of Xorg or hal.

Fix this problem by choosing different part of SCIM.
[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/293001](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/293001)

---

