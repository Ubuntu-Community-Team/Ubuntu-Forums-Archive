---
title: "Unable to get USB to DVI adapter working"
date: 2017-11-12
forum: Hardware
---

### Post by russdwright on 2017-11-12
I'm running Ubuntu 17.10 on my HP All-In-One PC. I've been pretty happy with it, but want more screen real estate.

Before installing Ubuntu, I purchased a StarTech USB to DVI video adapter. I connected it and no dice.

I researched the product and found no drivers online, so I looked for something generic. I then discovered the adapter is using MCT technology instead of DisplayLink.

In diving a little deeper, I learned there was a "workaround" using fakexrandr. I got that installed but still nothing.

I was wondering if anyone out there has been able to get this setup to work and, if so, how?

---

### Post by DuckHook on 2017-11-12
Welcome to the forums, russdwright.

I know nothing about *fake xrandr* and little enough about 17.10 (still on Xenial), so what you are trying to do seems pretty bleeding edge to me. My only comment is: will this even work in 17.10? To my knowledge, Aardvark uses Wayland, so X is no longer in the picture. I haven't fiddled around with all of the new stuff in Aardvark yet, so my comments are admittedly a shot in the dark, but you may wish to check out if xrandr is still valid first.

---

