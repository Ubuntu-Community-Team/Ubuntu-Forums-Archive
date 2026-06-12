---
title: "Best method for syncing files between multiple computers?"
date: 2008-11-20
forum: General Help
---

### Post by gobbles414 on 2008-11-20
Hi all,

Thanks in advance for your help!

I want to sync files between my Windows Vista laptop and my Ubuntu 8.10 desktop, but have never done anything like that before.

_Here's an example of what I would like to happen_
I log into my Ubuntu desktop. I then log into my Vista laptop. Each computer detects the other, and a message is displayed on both asking if I would like to sync. I say yes on my laptop, and both computers accept my decision. "Normal" files such as music, videos, pictures, and documents will sync.

At the same time, "difficult" files will also sync: Firefox bookmarks with Firefox bookmarks, QuickBooks Simple Start data with QuickBooks Simple Start data (will use Wine/CrossOver to run in Ubuntu), Windows Calendar data with Evolution Calendar data, and Windows *Live* Mail (not Hotmail) contacts with Evolution contacts. All of my email accounts use IMAP, so syncing emails would be pointless. Perhaps a syncing program with some sort of macro option to record conversion processes...?

PS: Have any of you used a program called Unison? Would it be a good solution for me? Any other programs that might work for me?

---

### Post by snova on 2008-11-20
Well, I don't know about a GUI solution that will ask when you boot up, but rsync would otherwise do nicely. It operates over a network and is incremental.

"Difficult" files? Unlikely. The example conversions would be possible (or not!), but probably tricky to automate.

---

### Post by gobbles414 on 2008-11-20
> **snova said:**
> Well, I don't know about a GUI solution that will ask when you boot up, but rsync would otherwise do nicely. It operates over a network and is incremental.

"Difficult" files? Unlikely. The example conversions would be possible (or not!), but probably tricky to automate. Thanks for your reply!

Supposedly, Unison uses a GUI. According to the Unison homepage ([click here]("http://www.cis.upenn.edu/~bcpierce/unison/")), "Unison shares a number of features with tools such as configuration management packages (CVS, PRCS, Subversion, BitKeeper, etc.), distributed filesystems (Coda, etc.), uni-directional mirroring utilities (rsync, etc.), and other synchronizers (Intellisync, Reconcile, etc)... Transfers of small updates to large files are optimized using a compression protocol similar to rsync."

As you say, automation of some tasks may be difficult -- or even impossible in my situation. If one of my computers were a Mac, I would simply write a small program in Automator. :)

---

### Post by oldos2er on 2008-11-20
> **snova said:**
> Well, I don't know about a GUI solution that will ask when you boot up, but rsync would otherwise do nicely. It operates over a network and is incremental.

 grsync is a GUI version of rsync.

---

### Post by snova on 2008-11-20
Unison looks good. The trouble with rsync is that if you make changes to both sets of files, syncronizing them gets harder. So Unison might be the best option.

Getting it to start when you login wouldn't be very difficult now that I think about it. I just don't know how to do it on Windows is all.

---

### Post by johnkzin on 2008-11-21
I'm looking for something similar, but I have some specific needs.

1) I need to use SyncML to pull calendar data from Oracle Calendar

2) I need to sync all of the contacts/calendar data to Google (one option here is: SyncML to GooSync is viable, as I do have a GooSync account)

3) I would like to also sync bookmarks to Netvouz (the browser in question being Firefox, on Mac and Ubuntu), but this requirement is secondary.

I run both OSX and Ubuntu, in multiple places (currently 4 OS X boxes, an Ubuntu-UMPC tablet, and another Ubuntu box on the way).  I would like all of this to happen in an automated way (such as via cron), with some form of protection such as SSL.  I'd also like some of the transactions to be "one way" (such as "Oracle Calendar only sends data, no attempts are made to send data into Oracle Calendar"; and the ability to specify that Oracle Calendar's data will be written into Google's "Work" calendar).

Any thoughts?

---

### Post by gobbles414 on 2008-11-22
> grsync is a GUI version of rsync. I'm not sure how helpful this will be in my situation, since one of my computers is running Windows Vista.

> Unison looks good. The trouble with rsync is that if you make changes to both sets of files, synchronizing them gets harder. So Unison might be the best option. Unless someone suggests a better option, I think that I'll give Unison a try.

> Getting it to start when you login wouldn't be very difficult now that I think about it. I just don't know how to do it on Windows is all. How would I do it in Ubuntu?

> I'm looking for something similar, but I have some specific needs... And I thought my situation was difficult! If I find any information that might help you, I'll post it to this thread.

---

