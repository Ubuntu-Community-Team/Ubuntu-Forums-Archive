---
title: "Why hibernate won't work - a big clue."
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by Zad_ok on 2005-06-30
Since I've been spending really far too many hours trying to get hibernate to work reliably on my desktop, I thought I would share what seems to be a big clue as to where it stumbles. This will hopefully allow someone more knowledgeable than me to make it work reliably and allow a lot of other people to share this useful feature.

Hibernate works on my machine - but only about 50% of the time. Very strange! I was messing with the file /etc/default/acpi-support which you have to edit to get hibernate to work as detailed in the wiki (wiki.ubuntu.com//HoaryPM) and commented out the USE_DPMS line:

# Should we switch the screen off with DPMS on suspend?
#USE_DPMS=true

What this does is allow you to see what is going on during the hibernate process right up to the time when the PC switches off. It was very interesting to me as all I could see before was the screen going blank and nothing happening.

After all the memory has been freed, the last thing the system does is write the resume data out to the disk, in my case to the swap file. This is where it gets interesting.

If hibernate is going to work properly, the write to disk phase goes like lightning, about two seconds I would say, and the PC then switches off immediately.

If hibernate is going to fail, it takes about ten seconds to write each single percent. In other words it would take around 1000 seconds (around 17 minutes) to hibernate! I just give up and hit the reset button when this happens. Something is obviously seriously wrong at this point.

I'm sure someone with more knowledge of Linux than me would know, or at least have some suggestions, as to what is causing this seemingly random behaviour.

I'm very happy to try out suggestions, answer questions and so on.

I shouldn't be spending all this time on one thing, but it just niggles me that it's so nearly working! I'm hoping we can uncover something useful and post it as a "How to" for others to read and to make Ubuntu even better.

---

### Post by phen on 2005-07-01
have you tried to search bugzilla? i think i heard about this bug before, maybe you find a solution there!

cheers kai

---

