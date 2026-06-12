---
title: "Seemingly random Pidgin crashing"
date: 2008-11-30
forum: General Help
---

### Post by PidginCrash on 2008-11-30
Ok, I've been across Google searching for an answer to this problem, but all the situations I can find seem different.

My problem is this.

On Ubuntu 8.10, with all updates installed, Pidgin randomly crashes while I have it running. It is connected to an extremely stable wired connection.

There doesn't seem to be an obvious trigger. When the program crashes, it simply vanishes from the screen, and its icon in the top right of the screen (if you'll forgive my poor terminology there) vanishes. There is no graphical grey out, requiring a force quit or anything of the sort.

This can happen in the middle of a conversation, or when Pidgin is just sitting up in the top right with nothing open on screen and no one online.

In Pidgin, I have two accounts. One is a MSN account and one is a Jabber account. MSN connects via normal (not http) mode, and Jabber uses SSL/TLS. Local aliases are the same (one source mentioned a crash based on this, but it seemed the suggest the crash was instant).

The most likely factor for a crash I can reason is the OTR plugin (pre-installed with Ubuntu) which I make daily use of, but I suspect most don't thus the crashes going unnoticed.

However, as I said earlier, I've been unable to definitively link use of OTR to crashes.

So, in closing I'm posting this to see if anyone has had a similar problem that I'm not finding on Google. I simply don't have the time to search for hours for a solution like I used to.

I am currently running Pidgin from the terminal with -d appended, which I believe is displaying debug info. I am hoping that when/if Pidgin crashes the terminal will capture the cause. Is this sound reasoning?

---

### Post by padrehomer on 2008-12-01
I am experiencing the same thing, random "disappearance" of the Pidgin program happening after the upgrade to 8.10. I'm going to run the debug option as well and report back with what it spits out when it crashes.

---

### Post by Wartender on 2008-12-01
same problem here, although sometimes it does go grey and requires a force quit. The only plugin i have activated is the buddy notes plugin and i doubt it's that sice it was doing this before i activated it

---

### Post by padrehomer on 2008-12-01
Ok, I just tried to double-click on a name to message someone and it crashed, here is what debug caught:

(12:47:49) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(12:47:49) dbus: The signal "drawing-tooltip" caused some dbus error. (If you are not a developer, please ignore this message.)
Hash Manager Error : 5
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Aborted

---

### Post by padrehomer on 2008-12-01
Crashed again, but this time someone was sending me a file and I was trying to save it:

(13:42:16) GLib: /build/buildd/glib2.0-2.18.2/glib/gmem.c:175: failed to allocate 1024 bytes
Aborted

---

### Post by rkatz0 on 2008-12-01
Hi,

I upgraded from 8.04 to 8.10 and the latest Pidgin came with it (2.5.2). It is the 64bit version of Ubuntu. And my Pidgin is disappearing without a trace randomly as well.

---

### Post by elixr on 2009-01-16
Same here.  It's very frustrating.

---

### Post by khm on 2009-01-19
> **padrehomer said:**
> Crashed again, but this time someone was sending me a file and I was trying to save it:

(13:42:16) GLib: /build/buildd/glib2.0-2.18.2/glib/gmem.c:175: failed to allocate 1024 bytes
Aborted

Same thing here.  

Someone has to know what's going on....

---

### Post by Percolator on 2009-02-01
I have a similar problem. After chatting about 10 minutes, when I receive files it behaves weird or crashes. It might also crash for no apparent reason or I don't receive messages anymore because it has crashed (or the module which receives the messages) but Pidgin remains open so I don't really notice that it's not working anymore. Very weird behavior which makes me think of a memmory leak or something.

I really wander when Pidgin 2.5.4 will be available through Update Manager. If it's not being kept up to date by Update Manager, there is no point in keeping that Pidgin version and one might just do all the compiling work by himself :roll:

---

### Post by kevdog on 2009-02-01
Just compile the pidgin from source -- its not that hard!!:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by khm on 2009-02-04
Tried that. Does not prevent crashing (at least with my experience).

---

### Post by cometa2k7 on 2009-03-04
Pidgin seems to randomly crash on me too - I occasionally get fed up and switch to Emesene because of it.

Pidgin seems only ever to crash on me when I'm running Exaile, which recently has been quite frequent so whether this has anything to do with it I don't actually know - not enough evidence for a causal link.

---

### Post by darthpaul on 2009-03-19
i'm also having this problem.  it just crashed on me while i was trying to move a file from one hard drive to another. i'll try to run it in debug mode and post anything if it crashes.

---

### Post by darthpaul on 2009-03-20
mine randomly quit and this is what i got from my terminal.  i took out the buddy names for obvious reasons. and the line that goes:

"E: shm.c: mmap() failed: Cannot allocate memory" 

repeated almost for the length of the terminal. 

(16:12:18) blist: Updating buddy status for [email]---------@gmail.com[/email] (XMPP)
(16:12:18) nautilus: saved blist online
(16:12:18) jabber: Recv (ssl)(279): <presence from="--------@gmail.com/gmail.FE7C6161" to="--------@gmail.com"><priority>24</priority><caps:c node="http://mail.google.com/xmpp/client/caps" ver="1.1" ext="pmuc-v1 sms-v1" xmlns:caps="http://jabber.org/protocol/caps"/><x xmlns="vcard-temp:x:update"/></presence>
(16:12:18) blist: Updating buddy status for [email]-----@gmail.com[/email] (XMPP)
(16:12:18) jabber: Recv (ssl)(292): <presence from="-----@gmail.com/gmail.FE7C6161" to="-----@gmail.com"><priority>24</priority><caps:c node="http://mail.google.com/xmpp/client/caps" ver="1.1" ext="pmuc-v1 sms-v1 vavinvite-v1" xmlns:caps="http://jabber.org/protocol/caps"/><x xmlns="vcard-temp:x:update"/></presence>
(16:12:18) blist: Updating buddy status for [email]------@gmail.com[/email] (XMPP)
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
pidgin: pulse.c:200: pulse_new: Assertion `p->context' failed.
Aborted
paul@paul-desktop:~$ 

hope this can help someone

---

### Post by karunkun on 2009-03-25
Same thing's been happening to me.  Its bad enough that for a while I switched to ayttm, which has its own set of problems.  Meh.

---

### Post by The_Montgomery on 2009-03-25
Have you tried running it in debug mode?  Run it from a Terminal like so:

```
pidgin -d
```

If nothing else, it might help you see where it's hanging up.

---

### Post by Pyper on 2009-04-16
I have the same problem with Pidgin exiting seemingly at random. I am running 1:2.5.2-Oubuntu1.1 on (I think) the latest Kubuntu distro. It crashes right after I hit enter to send a message. In this case is it a certain key/mouse combination triggering it? or another manifestation of the unknown glitch.

---

### Post by NFblaze on 2009-04-16
this probrably wont pertain to most of yall...but I used to get the segmentation fault crash.... and thats eve nafter it was completely removed and reinstalled....its still gave me that crash...

Well... what seemed to be the problem was the Buddy Ticker  plugin...after i disabled it it stopped crashing tho...so try that.

---

### Post by squee on 2009-04-27
I've had similar problems after version upgrades. I found that a clean install (instead of dist-upgrade) usually solves the issues. I havent had time to do a clean install yet due to exams, but the first day I get the chance I'll do it.

---

### Post by pbrito81 on 2009-08-04
I had this issue after adding a msn contact who had just changed their msn account email. The error was about pidgin trying to alloc 1,5Gb ram! It happenned just after some log messages about that contact.

Worked fine after removing that contact.

---

