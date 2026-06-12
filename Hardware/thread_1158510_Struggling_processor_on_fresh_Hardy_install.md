---
title: "Struggling processor on fresh Hardy install"
date: 2009-05-13
forum: Hardware
---

### Post by pabacon on 2009-05-13
I've just upgraded my compaq TC1000 tablet from XP to Xubuntu (Hardy 8.04).

I've already found that it takes very little to use much, if not all or the CPU - even the system monitor alone uses 20-30%!

I should make it clear at this point that it wasn't great on XP but I expected the reduced footprint of Xubuntu might improve the situation, so far it seems worse.

How can I identify the cause for this? Is it likely to be caused by missing drivers, incorrect configuration, a nackered processor or all of the above? How should a linux novice go about diagnosing this type of issue?

The processor is a Transmeta Crusoe TM5800.

Any help would be greatly appreciated!

Phil

---

### Post by jerrrys on 2009-05-14
i do not run a tc1000, but i do run an older box...so for what its worth...on mine, with nothing pulled up, it will set there and idle at the same 20 to 30%. so i dont see this as an issue.  however when i pull up something, say like firefox, it still shows the same 20 to 30%. throw in some music and it still shows about 30%...

a quick internet search shows that you are probably running 512meg of ram. so im wondering if you are having a lot of swap activity going on. that would drive up cpu usage...

one last suggestion would be to try an even lighter linux, like 'feather', there are several to choose from...

hope this throws some light on the subject...

---

### Post by pabacon on 2009-05-14
Thanks for your response jerrrys - some useful suggestions there.

Merely launching firefox takes the CPU usage straight to 100% where it stays until I close the window, even staying on the vanilla google home page. During this time, any other tasks become painstakingly slow - even just switching back to the system monitor took around 5 seconds.

The tablet has been upgraded to 1GB RAM and the usage of both this and the swap file are both fairly inactive. I'll check this when I'm next home though so as not to waste anybody's time.

I've looked into some other lightweight distro's but was drawn to Ubuntu for the ease of install and well-renowned support.

Thanks again for the advice, I'll update again when I've run a few more tests next week.

Phil

---

### Post by jerrrys on 2009-05-14
"I've looked into some other lightweight distro's but was drawn to Ubuntu for the ease of install and well-renowned support."

that says it all...

---

### Post by pabacon on 2009-05-14
I don't know how to read into that! Do you mean:

1. Great summary of Ubuntu! Or
2. You're an idiot, stop wasting my time!

---

### Post by jerrrys on 2009-05-14
Great summary of Ubuntu! that says it all...

---

### Post by Favux on 2009-05-14
Hi pabacon,

You might want to try the top command and look at your running processes.  There might be something hogging your CPU you could adjust or turn off.  Type "man top" in a terminal.  I've seen some threads discussing how to use it and how to examine CPU usage.  So search the forum with "top" etc.

---

