---
title: "Problem restarting after suspend/hibernate"
date: 2008-09-13
forum: Hardware
---

### Post by epitaph on 2008-09-13
Let me say I don't really follow many bug changes but I was extremely surprised when, one day, not thinking, I suspended the laptop and it worked!

This was one of my main gripes with Ubuntu (the other being fglrx and compiz hating each other). I tested Hibernate and it worked flawlessly also. **Resume from each of them works flawlessly.**

The problem arises when I decide to restart or shut down the computer. If I tell Ubuntu to restart or shut down the computer, it proceeds normally by unloading all kinds of files but it just stops at a black screen without actually turning off and there is no activity on the laptop hard disks at all. It appears the battery LED blinks occasionally, though I'm not sure that has anything to do with it at all.

Essentially, this kind of stinks. What kind of things could I try to possibly figure out why restart won't work after suspending to memory or disk?

---

### Post by pytheas22 on 2008-09-14
I've had similar problems where the computer goes into suspend mode alright but ends up in a zombie state, with a blank screen, when I try to resume...fortunately these issues have all gotten fixed by updates.

But a good place to start looking for information is your system log, which you can read by going to System>Administration>System Log, or opening the file /var/log/syslog in a text editor.  See if it logs any activity at the time that you try to resume the computer (each entry has a timestamp so it's easy to keep track of).  It's possible that it doesn't resume enough to the point where the logging daemon starts back up, which would mean that nothing would get logged.  But hopefully enough of the system is able to resume that some information gets dumped to syslog regarding why it's failing to complete the waking up.  If you see any messages that look relevant, please post them here.

Also, when it hangs at the blank screen, does anything happen if you press control-alt-backspace or control-alt-F7?  What about trying to turn the numlock or capslock keys on or off--do you see the lights on your keyboard change at all?  This information is useful for figuring out how much your system is able to wake up before it crashes.

---

### Post by epitaph on 2008-09-14
Oops, I think I might not have worded the post entirely clearly.

The suspend and hibernate features work perfectly. Meaning I can resume from them without any issue whatsoever. I can suspend/hibernate/resume multiple times with no issue.

When I decide to "Shut Down" or "Restart" the computer is when the black screen shows up (and there are no lights on the keyboard, pressing anything does nothing, I think even fans turn off...)

I know lots of people have issues with suspend features, it's a pretty tall order to get it working properly. It's like Ubuntu unloads itself fine and then never actually sends the message for the system to actually shut down.

Thanks for the reply!

---

### Post by pytheas22 on 2008-09-14
Alright, sorry for misreading your first post.

When you shutdown or restart, does the computer go through a normal shutdown process--i.e. do you see the Ubuntu logo and the orange bar emptying out?  If so, it's probably just an acpi issue where Ubuntu isn't able to actually cut the power off.  This is a common issue on many computers and is not serious; you can just cut the power manually without risk of damaging anything.

If the computer isn't shutting itself down gracefully, then that's a problem, so let us know.

---

### Post by epitaph on 2008-09-15
The operating system shuts down fine, there's no sign in the logs that it hasn't and there are no issues when I turn the laptop back on. So I guess I just deal with it for now.

Thanks for your replies.

---

