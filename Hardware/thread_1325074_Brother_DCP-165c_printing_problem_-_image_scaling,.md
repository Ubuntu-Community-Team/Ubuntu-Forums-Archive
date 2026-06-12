---
title: "Brother DCP-165c printing problem - image scaling, cut off"
date: 2009-11-13
forum: Hardware
---

### Post by Shampyon on 2009-11-13
I picked up a pack of DVD labels at ALDI and I've been trying to set up a template I can use to print onto them. It doesn't have any bundled software as far as I can tell, so this is the only way.

I'm trying to get the printout to look like this:
[IMG]http://i35.tinypic.com/i3gdh1.png[/IMG]

but after experimenting with the printer settings a dozen or so times it always either comes out the wrong size or offset like this:
[IMG]http://i33.tinypic.com/zxqnhs.png[/IMG]

The weird thing is I've printed PDFs and ODTs before and they came out fine. It's just plain images that are giving me a hard time...

---

### Post by Shampyon on 2009-11-19
SOLVED.

Previously I simply altered the configuration files after the Karmic upgrade. This left the multifunction working, but for some reason the printing misaligned.

I did a complete removal of the Brother scanner and printer packages, which reset all the relevant configurations to default, then restarted the computer. I then reinstalled the packages and make the relevant configuration edits afresh, restarted my computer and multifunction, and everything was back to normal.

---

