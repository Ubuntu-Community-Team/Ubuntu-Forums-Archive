---
title: "Window titles disappear if visual effects are enabled"
date: 2008-10-17
forum: General Help
---

### Post by unclejames on 2008-10-17
Running an Acer Aspire One, using Intrepid Ibex, latest build.

When you enable visual effects, the title bar disappears from all windows. Returning back to 'no' visual effects makes the title bar return.

It has worked correctly back when I first installed Intrepid, but software updates broke this; how can I get it working again?

---

### Post by CJ56 on 2008-10-17
Just a couple of thoughts -

Do you have the CompizConfig Settings Manager installed? If not, you can find it in Synpatic Package Manager and install it from there

If you have got it, go to the Effects section and make sure that Window Decoration is checked

If that fails, you could go to the Utility section in CompizConfig, go to Workarounds and un-check the Legacy Fullscreen Support

---

### Post by unclejames on 2008-10-17
Hi there, thanks for the reply.

Window Decoration is checked; and the Legacy Support doesn't appear in my compizconfig.

I suspect it's related to a bug in Jockey GTK, which is currently open.

---

### Post by HornedOne on 2008-10-19
Its an issue with CompizFuzion.  I had that issue earlier today, and it looked like my windows were frozen in place.  I found that turning off Opacity did the trick.

---

### Post by loomsen on 2008-10-19
> **HornedOne said:**
> Its an issue with CompizFuzion.  I had that issue earlier today, and it looked like my windows were frozen in place.  I found that turning off Opacity did the trick.

Not a to desirable trick tho ^^ Opacity is one of the main features imho.
However, what about fusion-icon? Ain't that most common? 

Oh, and open up your System Monitor and check how many instances of emerald --replace are running.

Startupskripts often don't exit, then you might have changed the cmd in compiz to emerald --replace as well, and, just to make sure it is running, another one into startup applications... However, I found 6 of them running all the time.

And if it is persistant, turn on the debugger log for compiz, let it log a while, like till that whole thing happened a couple of times, and then read it. grep to filter, for instance, if log is 
/var/log/compiz_log_xxx


cat /var/log/compiz_log_xxx | grep Error 

would repeat strings in respective logfile containing errors, usually written to the same line with a module that caused the error message.

You should get the debug symbols too, otherwise the log ain't too usefull.

---

