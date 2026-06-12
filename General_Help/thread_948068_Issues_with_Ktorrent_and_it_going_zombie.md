---
title: "Issues with Ktorrent and it going zombie"
date: 2008-10-14
forum: General Help
---

### Post by Ximal on 2008-10-14
I have a problem that ktorrent goes to uninterrupted and will stop using the network but still show it is using 600 plus megs of memory in the ram.. It typically freezes up severely and it slows the system down.. 

Is there a way to fix this bug ? is it a known issue ?

Also .. Why am I using ubuntu if it has a shelf life like windows 3.1 and 95 and 98 and ME did... Why does it stop supporting it's users and close the repositories at the eol date... Is there no way to connect to the newer repositories ? or is that all she wrote ? Because if so.. I can go back to using different linux distros if needed... I'd like much more to have the security of repositories staying in place etc... I was wandering if ubuntu is going to slow down their support end of life dates etc... I'm just unsettled when it comes down to this.. Because I am learning so much from this community... Though it's stability is awesome... how will it last if the repositories keep closing ?

---

### Post by lokkur on 2008-10-23
I have same problem what is.

thank you 
Lokkur

---

### Post by jubantu on 2010-05-18
Have the same problem under Ubuntu 10.04. Any solutions yet?

---

### Post by soltanis on 2010-05-18
Have you tried doing

```

pkill -9 ktorrent

```

When that happens? Consider switching clients to something more stable.

---

### Post by cespinal on 2010-05-18
> **soltanis said:**
> Have you tried doing

```

pkill -9 ktorrent

```

When that happens? Consider switching clients to something more stable.

Dude.... this post is two years old :D

---

### Post by gewone on 2010-11-17
Guys, it may have been two years since this thread popped it's sherry, yet issue's still there.
I'm running Ubuntu 10.10 (Maverick Meerkat), and this just struck me. Process turned zombie on me.
'[htop]("http://htop.sourceforge.net/")' shows one of my four CPU cores constantly on 100%, although zombie process 'core of choice' seems to differ.
At one check, it's CPU #1 that's maxing out, next time I check it's CPU #2, etc.
Funny thing is there is no parent process, which is usually the case when SIGKILL (kill -9) wont do the trick.

Talk about weirdness. Please let the developers come to us with ideas.

---

### Post by SeijiSensei on 2010-11-17
I'm not a developer, but are you running this in Kubuntu, or are you using ktorrent on a GNOME machine?  In the latter case, you'll see more memory usage because you have to load all the libraries to support a KDE application on top of the libraries GNOME uses.

My ktorrent (on Kubuntu 10.10) reports something like 859M of memory usage, but only 22M of that is resident and unique to ktorrent.  Over 600M comes from shared libraries that other programs (like the KDE desktop) are using.

I don't recall ever having CPU issues with ktorrent, and I've used it for quite some time now.

---

### Post by gewone on 2010-11-17
Thanks for your quick reply SeijiSensei!

I'm actually running Ktorrent over GNOME, mostly because I was displeased with the way Qbittorrent did things. However, like I stated, process is lock/stuck like one smoking barrel at the moment. I usually find my ways to cope with zombie processes, often by abruptly killing its parent. However, in this case I don't seem to find any other solution but an actual reboot. I like my 9 days uptime though, so I'll give it a few more go's until I give up, but I'm pretty close! ;D

---

### Post by SeijiSensei on 2010-11-17
Perhaps you should consider deluge instead of ktorrent if you're not running a KDE desktop?

---

