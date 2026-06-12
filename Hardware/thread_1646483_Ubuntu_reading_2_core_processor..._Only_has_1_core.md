---
title: "Ubuntu reading 2 core processor... Only has 1 core ..."
date: 2010-12-15
forum: Hardware
---

### Post by Nath4n on 2010-12-15
I have an Acer D255 it has a Intel Atom N450 which is single core.  I have on my task bar the CPU scaler and it shows the option for two cores to control.  I ran top in a terminal, it too shows two cores.  In system monitor it is also showing two cores.  Help me understand please how a single core chip is showing up as dual core?  I'm very confused.

---

### Post by akand074 on 2010-12-15
The Intel Atom has Intel's Hyper Threading Technology. It gives each Core 2 threads. Meaning one core can do two things simultaneously. Operating systems look for threads, not cores. Windows would also show you have 2 "cores".

---

### Post by Nath4n on 2010-12-15
Im able to scale both threads?  So in effect it thinks it has two cores?  So I guess there is no point in having two separate scaling tools on my task bar?  One for each thread?

---

### Post by akand074 on 2010-12-15
Well, you could scale each thread. To an OS a thread = a core. So to it, you have a dual core even though based on technicality, you don't. Personally, from my experience, with Hyper Threading on the new Intel chips (although people may disagree) the system runs almost as effective as having another core. Though your thread is marked as solved so I'm glad I could be of help.

---

### Post by Nath4n on 2010-12-15
> **akand074 said:**
> Well, you could scale each thread. To an OS a thread = a core. So to it, you have a dual core even though based on technicality, you don't. Personally, from my experience, with Hyper Threading on the new Intel chips (although people may disagree) the system runs almost as effective as having another core. Though your thread is marked as solved so I'm glad I could be of help.
   Thank you so much for clearing that up for me!!!!  One more question though, should I bother with scaling both threads, or would scaling one do the trick?

---

### Post by akand074 on 2010-12-16
> **Nath4n said:**
> Thank you so much for clearing that up for me!!!!  One more question though, should I bother with scaling both threads, or would scaling one do the trick?

I'm not positive if scaling one would effect the other, I don't imagine it would. But it's not a big deal I suppose. I'm sure there is an applet that would scale "all" threads.

---

### Post by Nath4n on 2010-12-16
Thanks a lot for clearing that up.  I was at first thinking my netbook had the wrong processor installed!

---

### Post by cascade9 on 2010-12-16
> **akand074 said:**
> Well, you could scale each thread. To an OS a thread = a core. So to it, you have a dual core even though based on technicality, you don't. Personally, from my experience, with Hyper Threading on the new Intel chips (although people may disagree) the system runs almost as effective as having another core. Though your thread is marked as solved so I'm glad I could be of help.

I'll disagree. 

[http://ixbtlabs.com/articles3/cpu/ci7-turbo-ht-p1.html](http://ixbtlabs.com/articles3/cpu/ci7-turbo-ht-p1.html)

Hyperthreading might be slightly more useful on lower end, single and dual core chips, but its still nowhere near 'having another core'.

---

### Post by akand074 on 2010-12-16
> **cascade9 said:**
> I'll disagree. 

[http://ixbtlabs.com/articles3/cpu/ci7-turbo-ht-p1.html](http://ixbtlabs.com/articles3/cpu/ci7-turbo-ht-p1.html)

Hyperthreading might be slightly more useful on lower end, single and dual core chips, but its still nowhere near 'having another core'.

Well, just using a computer algorithm to test it on certain applications isn't entirely accurate of overall performance. I mean there are lots of applications that aren't designed for multi-threaded CPUs. Some games don't even support more than a single core. So for some applications, you can even disable lets say 2 of 4 cores and only get a minor to no performance decrease. You said it's slightly more useful on lower end CPUs which is true, but I think it's because higher end CPUs are already powerful enough to run most applications/overall the OS at full power. In Intel's quad core hyper threaded to 8, when does anyone even need more than the 4 cores? The very odd task, or the very odd time when your running lots of stuff. What I'm saying is, for general use. For example if I opened 8 applications at the same time they will all open almost instantly as if I pretty much had 8 cores.

I'm just basing this off personal experience. I've religiously used a single core, a single core hyper threaded, a dual core, a dual core hyper threaded, a quad core, a quad core hyper threaded, and a six core hyper threaded. And I had CPU monitors running the whole time. From what I've noticed, each thread is used rather equally. I don't even notice a big difference between a quad core and a six core. On average, a single thread never even goes beyond like 15% most of the time. But when I encoded a 10GB DV grab once on my previous i7, all 8 threads went to 100% and the encoding went blazingly fast. 

So basically what I'm saying from my experience, for general use (opening/closing tabs and applications, running several minor tasks simultaneously) they are almost equivalent. I haven't really tested it on gaming and other intensive tasks often enough to speak. But this is what I've noticed based on my general usage. In the end, obviously an extra core trumps an extra thread on the same core, but for multi threaded applications and general use, it's pretty effective.

Sorry to keep this solved thread going, just thought I'd clarify what I meant, and voice my experience with the topic.

---

