---
title: "Gnome apps settings are not persistent.  Please help me fix this!!"
date: 2008-11-20
forum: General Help
---

### Post by jimmy the saint on 2008-11-20
At first I though that I was having issues with Rhythmbox not remembering what I did between sessions (Rhythmbox sessions, not Ubuntu sessions).  Then I started having similar issues in Gedit.

In Rhythmbox, I have to manually connect to my daap share every time I open the program.  It used to remember it between sessions.

In Gedit I have to select the code highlighting mode EVERY TIME I open a document or start the program.  This sucks because snippets rely on the highlighting mode selection!  

I have come to realize it is because settings aren't being saved.  Can someone help me troubleshoot this because the issue sounds small, but I am trying to learn how to program here and it is a major usability issue here.  I am tempted to wipe my .config and .gnome2 folders but that is probably not the way to go!

Thanks
JTS

---

### Post by jrib on 2008-11-20
What if anything does this command return:
```
find ~ ! -user $USER
```

Please include the command you ran and the full output in your response

---

### Post by jimmy the saint on 2008-11-20
```
home/bluto/.nvidia-settings-rc
/home/bluto/storage/lost+found
/home/bluto/.dbus
find: /home/bluto/.dbus: Permission denied
```

---

### Post by jrib on 2008-11-20
okay, so it does not seem to be an ownership issue.  Let's troubleshoot a specific setting.  Go to gedit, edit -> preferences, and click "enable line numbers".  Does this change persist after closing gedit and opening it again?

---

### Post by jimmy the saint on 2008-11-20
Yes it does.  In fact, now that i think about it, most settings do persist so I guess I went a little overboard in my description.  The ones that I have found thus far which don't are the highlight mode and the daap share in rhythmbox

I'm thinking I jumped the gun here.  I no longer think they are related, or that my problem goes beyond the individual quirks.  I am not going to mark this as solved because I don't want anyone thinking that this thread will solve their issue.  Thanks for trying to help jrib!!

---

### Post by jrib on 2008-11-20
Yeah, sounds like it's app-specific then.  I don't really use those apps though.  Good luck

---

