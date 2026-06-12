---
title: "Opera crashing during fast tab opening"
date: 2008-09-25
forum: General Help
---

### Post by wetling on 2008-09-25
I'm using Ubuntu 8.04 x64 and I've got a problem where, if open Opera tabs too fast, the CPU goes to 100% and I've got to force a quit.

When I restart the browser, it says

> It appears another Opera instance is using the same configuration directory because its lock file s active: /home/*username*/opera/lock
Do you want to start Opera anyway? 

So I click Yes and then restart with the same tabs and I get a message that says

> There was a problem initializing Opera Mail.
Store Init failed
Engine Init() failed

I've tried 

> sudo apt-get remove opera 

Then downloaded the .deb file, but when I reinstalled, all my tabs were still there and the problem remained. 

I've never used Opera for mail.  

Thoughts?  Thanks.

---

### Post by lewiz on 2008-09-27
I think the best way to get a fix for this is:

1. remove your opera
2. install opera deb from [http://www.opera.com/download/](http://www.opera.com/download/)
3. re-test
- if the issue no longer occurs then you'll need to log a bug for whatever version of opera you were previously using... they'll probably want a stack trace along with it
- if the issue still occurs, put a post to the opera forums for help

---

### Post by wetling on 2008-10-10
Well, I tried to uninstall it, but when I reinstalled, it showed me the same tabs.  Oh well.  Maybe the next version will work better.

Oh yeah, I also posted at [http://my.opera.com/community/forums/topic.dml?id=251049&t=1222397771&page=1#comment2744136]("http://my.opera.com/community/forums/topic.dml?id=251049&t=1222397771&page=1#comment2744136") but that didn't turn out to be very helpful.

---

### Post by wetling on 2008-12-17
As an update, reinstalling Ubuntu (8.10 x64) didn't help.

---

### Post by jivanyatra on 2008-12-23
Hey, long-time Opera user here, though I've only recently begun to use Linux substantially.

From my experience, your error message stems from the fact that another instance of Opera is running and has stopped responding.  Go to your System Monitor and look under your processes tab, and see if there's another instance of Opera that you can force quit before you start Opera again.

From my understanding, by hitting yes, you're agreeing to use settings that are locked up by another, non-responding instance of Opera.

I get an issue where Opera locks up for 10-15 seconds if I try to do anything before a page fully loads, whether it's scrolling down or switching to another tab.  Anyone else have this problem?

---

