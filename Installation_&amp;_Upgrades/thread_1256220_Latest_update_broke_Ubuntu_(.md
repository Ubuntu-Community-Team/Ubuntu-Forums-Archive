---
title: "Latest update broke Ubuntu :("
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by javyn999 on 2009-09-02
Hey all.

Have a rather strange, yet major problem since I applied the latest update to Ubuntu day before yesterday.  

After updating, my OS seems to be completely hosed.

First off, after rebooting after the update, Compiz starts crippled.  My desktop cube has become disabled, the Compiz wallpaper drawing feature disabled, half (but not all) of my window animations are disabled.  

Figured it was a small glitch, but after re-enabling everything in Compiz, and rebooting again, it's back to the same way when I log in. 

Also, Firefox is completely screwed up too.  Now, my back button does not work, my bookmarks are missing, things I type into search engines or login screens simply do not work.

I found that issue on this form regarding Firefox, and the fix suggested going into /home/yourname/.mozilla/firefox and changing the name of the profile and restarting Firefox.  After I did this, Firefox refused to start at all telling me that another instance of FF is already open, which of course, it isn't.

Also, Deluge and Nicotine do not run at all now.  The windows open, but they grey out and never come active.

This behavior is identical for all users who try to log into that computer.

Does anyone have any ideas as to what's going on, and if there is an easy fix?  

I'm hoping there was some stupid glitch during the update process that can easily be remedied by a CLI command.  If not, I guess I'm going to have to reinstall Jaunty, which I'd rather not do since Koala is so close to coming out.

I'd appreciate any help.

---

### Post by stlsaint on 2009-09-02
do you remember what update you went thru?

---

### Post by garvinrick4 on 2009-09-02
Sounds like you went from Jaunty to Karmic to me. It has happened
to most all of us in between Alpha stages doing daily upgrades. It
is a test phase for the OS and bad things can happen. Sometimes you
just have to clean install Jaunty upgrade to Karmic reconfigure to
your liking and not think about it. Alpha 5 here tomorrow. I just did clean install and waiting for Alpha 5 because mine was in a state of chaos. Other people I talk to are looking good after an
 dist-upgrade of a few days ago, you never know. To me it is the
only real help I can do is test everyday and report bugs. If you do
not want melt downs stay away until stable distribution is available. But you miss the feeling when you find a work around or the agony of the meltdown.

---

### Post by javyn999 on 2009-09-02
Thanks guys, but I did not install Karmic.  I just hit yes when I was prompted for the automatic update 2 days ago.  I didn't pay attention to what exactly was in the update, but I don't think Ubuntu is sneaking alpha versions of Karmic in the standard Jaunty updates.  :)

---

### Post by Luca_turicci on 2009-09-02
> **javyn999 said:**
> Thanks guys, but I did not install Karmic.  I just hit yes when I was prompted for the automatic update 2 days ago.  I didn't pay attention to what exactly was in the update, but I don't think Ubuntu is sneaking alpha versions of Karmic in the standard Jaunty updates.  :)

Not "sneaking" but you can update to 9.10 from the update manager, when Alpha 1 came out I remember seeing it on the Update manager, it said a new version of Ubuntu was available, 9.10.

---

### Post by javyn999 on 2009-09-03
Well, I'm a fool.  I realized my gf put 3 seasons of Star Trek TNG on my hard drive which ate up ALL my space and was causing the problems.  

But since I'm here, I may as well ask, how does one flag a topic solved?  :)

---

### Post by automaton26 on 2009-09-03
You just click on "Edit Tags" and add a "solved" tag - they removed the old system.

I was going to suggest that a graphics-related update can cause ATI drivers to stop working - you have to uninstall and reinstall Catalyst drivers again...

But you sorted out your own problem, which I guess makes your ST:TNG avatar image even more relevant :)

---

### Post by javyn999 on 2009-09-03
Thanks.  I feel incredibly foolish, but am very grateful for all the responses !!!

---

