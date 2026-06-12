---
title: "dead keys on Acer Aspire 8930"
date: 2009-02-24
forum: Hardware
---

### Post by tmetro on 2009-02-24
On an Acer Aspire 8930 laptop there are a pair of keys that I'd like to remap to something more useful than their keycaps indicate. Specifically I'm referring to a key with a Euro symbol that appears above the left arrow key, and a key with the dollar symbol that appears above the right arrow key. (I'm not sure what the thought was behind these keys, and why they weren't placed somewhere more appropriate, like part of the number pad.)

The keys appear to do nothing under Ubuntu 8.10, and this is confirmed by a lack of keypress events in xev. I tried several different choices for model and layout in GNOME's keyboard preferences, but I have a suspicion that I need to look at things at a lower layer.

Is there a tool that will let me see the raw keyboard data from the kernel outside of X? Maybe a /proc or /sys file that can be viewed? I saw the showkey command, but it looks like it operates at a layer after keymaps, which won't help if it is the mapping that is the problem.

 -Tom

---

### Post by jauntybluefish on 2009-11-01
I have an Aspire 5050 with the same 2 dead keys.
I currently use Jaunty.
Any ideas how we can remap these please?

Andy

---

