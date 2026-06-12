---
title: "Packages unavailable for Feisty?"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by agostonbejo on 2009-01-30
Hi everyone,

I've been having problems with installing packages on my kubuntu feisty lately. The adept package manager seems to find much fewer packages than it used to, and even if I click e.g. 'request install' on wine, it doesn't say 'install' in the 'requested' column, it stays on 'no change'.

At first I though my packaging system is messed up (which is btw. still quite possible), but I can't seem to download packages directly from [http://packages.ubuntu.com/feisty](http://packages.ubuntu.com/feisty) either. E.g. both on the page [http://packages.ubuntu.com/feisty/i386/flex/download](http://packages.ubuntu.com/feisty/i386/flex/download) or [http://packages.ubuntu.com/feisty/i386/bison/download](http://packages.ubuntu.com/feisty/i386/bison/download) all the links seem to be dead. (By which I mean that I randomly clicked about 5-10 of them, and all those were dead.)

Is it possible that feisty is not supported anymore to such an extent that all or most of the packages have become unavailable? If this is the case, isn't there a backup site/repository where I can still download packages for feisty from?

(Yes, I'm forced to stay on feisty, because later versions of Ubuntu don't recognize my Olympus digital camera -- this is a known problem, by the way, I think there's also a bugzilla for it, but at least some discussion in forums.)

Thanks a lot,
Agoston

---

### Post by perlluver on 2009-01-30
> **agostonbejo said:**
> Hi everyone,

I've been having problems with installing packages on my kubuntu feisty lately. The adept package manager seems to find much fewer packages than it used to, and even if I click e.g. 'request install' on wine, it doesn't say 'install' in the 'requested' column, it stays on 'no change'.

At first I though my packaging system is messed up (which is btw. still quite possible), but I can't seem to download packages directly from [http://packages.ubuntu.com/feisty](http://packages.ubuntu.com/feisty) either. E.g. both on the page [http://packages.ubuntu.com/feisty/i386/flex/download](http://packages.ubuntu.com/feisty/i386/flex/download) or [http://packages.ubuntu.com/feisty/i386/bison/download](http://packages.ubuntu.com/feisty/i386/bison/download) all the links seem to be dead. (By which I mean that I randomly clicked about 5-10 of them, and all those were dead.)

Is it possible that feisty is not supported anymore to such an extent that all or most of the packages have become unavailable? If this is the case, isn't there a backup site/repository where I can still download packages for feisty from?

(Yes, I'm forced to stay on feisty, because later versions of Ubuntu don't recognize my Olympus digital camera -- this is a known problem, by the way, I think there's also a bugzilla for it, but at least some discussion in forums.)

Thanks a lot,
Agoston

The end of life cycle has come for Feisty, Updates and Packages are no longer available for download.  [http://news.softpedia.com/news/Ubuntu-7-04-No-Longer-Supported-94357.shtml](http://news.softpedia.com/news/Ubuntu-7-04-No-Longer-Supported-94357.shtml), the only option to get new packages is to Upgrade to 7.10 - 8.10.

---

### Post by perlluver on 2009-01-30
You can change your sources to ```
http://old-releases.ubuntu.com/ubuntu/ feisty main restricted
``` you will have to use the old-releases link to get updates, and the like.

---

### Post by icanfly0307 on 2009-01-30
Feisty hit it's end of life a long time ago. Upgrade to 8.04 or 8.10. I'm guessing that Ubuntu is closing down the repos for 7.04

---

### Post by agostonbejo on 2009-01-31
Hi guys,

thank you very much for both the information about how to find a server that still provides feisty packages (it works, I'm happy now), and confirming the fact that feisty is really not supported now anymore.

Cheers,
Agoston

---

### Post by agostonbejo on 2009-01-31
Btw. I would mark this thread as solved as described in [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads), but in "Thread Tools" I can see no option called "Mark this thread as solved".

(What I have is:
- show printable version
- email this page
- subscribe to this thread
- add a poll to this thread)

---

