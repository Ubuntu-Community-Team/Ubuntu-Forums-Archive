---
title: "Mouse &quot;freezes&quot; when using evdev"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by muzzie on 2005-09-05
Some of you may have seen my previous thread regarding my keyboard freezing when I'd toggle my KVM (figured that one out) now I am having an issue with my mouse freezing when toggling my KVM!

Everytime I'd toggle my kvm, I'd lose control of my mouse.  I disconnected all other USB devices from the KvM to make sure it wasn't any of them causing trouble, but that didn't fix the problem.

Finally, I decided to change my mouse protocol in xorg.conf back to "ExplorerPS/2" from what I had set it to "evdev".
The problem immediatly stopped!

I tested this multiple times to make sure, and the results were consistent.  If I toggle my KvM with the evdev protocol set on my mouse, the mouse "freezes". I am guessing it registers the mouse being disconnected, but not being plugged back in.

This sort of sucks, because I was relying on evdev to give my support of all 10 buttons on my mouse, instead of the 7 "ExplorerPS/2" offers.

Is there any particular person/group that supports evdev whom I may contact about this issue? It's definitely an unpleasant bug.

---

