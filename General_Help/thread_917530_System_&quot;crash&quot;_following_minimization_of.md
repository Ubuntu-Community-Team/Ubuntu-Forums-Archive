---
title: "System &quot;crash&quot; following minimization of firefox"
date: 2008-09-12
forum: General Help
---

### Post by drewhenson on 2008-09-12
I am actually not sure what is causing this issue. However, the following screen shots show what happens when I minimize firefox (but only sometimes, not always):

[http://i37.tinypic.com/wjcgox.jpg](http://i37.tinypic.com/wjcgox.jpg)

[http://i33.tinypic.com/2i6l73p.jpg](http://i33.tinypic.com/2i6l73p.jpg)

I am then unable to do anything to correct the issue but shut down and reboot my laptop. I can still type into the screen that appears, but entering text doesn't do anything (as in, commands entered don't do anything). It has happened several times (~5) in the past two weeks. One time, it "recovered" and rebooted, without me doing anything (although unsaved work was still lost). Other times, it simply stayed like that and did not correct itself (although if left long enough the screen would go blank, as if it were working correctly and locking the screen, although moving the mouse would seem to do nothing). I have no idea if this is gnome failing, or ubuntu (as it seems unlikely a firefox crash or error would cause this issue).

Any help concerning this issue would be appreciated.

-drewhenson

PS: I am new to the forums, so hello all. I have found the help here invaluable in the past, and have just decided to register because of this issue. Thanks again.

---

### Post by HyperHacker on 2008-09-12
Looks like the X server (basically, the GUI) crashed. You should be able to type commands there, even if they don't show up on the screen.

---

### Post by drewhenson on 2008-09-12
How then do I go about correcting this issue, as it happens repeatedly? Or how do I recover from it without rebooting?
Thanks,

-drewhenson

---

### Post by rfdeshon on 2008-09-12
It's doubtful anyone can tell you how to prevent this just from the behavior. Next time it happens, tail /var/log/messages and see if there is anything probative in there /var/log/Xorg.0.log would also be helpful since it seems Xorg is crashing. If there are errors there, they should help track down the problem. If you can't actually run any commands from that screen, hit Ctrl+Alt+F1 to get to a console.

---

