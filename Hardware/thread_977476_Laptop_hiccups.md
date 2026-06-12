---
title: "Laptop hiccups?"
date: 2008-11-10
forum: Hardware
---

### Post by Oliver Acevedo on 2008-11-10
Hi, I was wondering if anyone has had a similar problem to this. I've search around in google and haven't found anyone having exactly the same symptoms. 

The problem is that when I'm on battery, the laptop "hiccups". Every once in a while, it'll freeze just for a second and then the hard drive does this weird "tch.. dddooiing..." and then "click click" sound. (forgive my vague attempt to type out sounds...)

Anyways, it only does this either after it's been idle for a bit, or when it's been idle and then as soon as I click on something it'll freeze and do the sounds thing and then go back to normal.

It's not a huge drag because it's still working, but it does get kinda annoying when I'm trying to fly through things and every now and then I gotta wait for the hard drive to "do it's thing". 

I assume it must have something to do with the energy saver script I ran but I tried to reverse the effects to no avail. Can anyone confirm this and/or let me know how to get it working normal again? Thanks!

---

### Post by HermanAB on 2008-11-10
It may have something to do with the log daemon.  If you wish to spin the HDD down on a laptop, then you should also disable syslogd to prevent it from writing to disk and causing it to spin up again.

'Hope that helps!

Herman

---

### Post by Oliver Acevedo on 2008-11-11
I've disabled the syslogd and the klogd but it still keeps doing it. I also noticed that the fan comes on as well. What else can it be? I've tried to find anything else on this subject but I'm not even sure what it's actually doing.

---

### Post by Oliver Acevedo on 2008-11-30
Bump.

Still no luck trying to figure this out. Really annoying, sometimes I'll open up firefox and start typing an address but nothing will appear till after like 3 seconds of typing, then it just spits everything out at once. What's up with this?

---

