---
title: "ugly setup problems"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by itsjames on 2005-04-10
Hello, I have a feeling this situation might be a bit unsolvable, but if there's any possibility of getting ubuntu working, it's worth a shot.

First quick problem is that setup doesn't recognize my wireless card.  Oh well, I can live with this for now.  My roommate who is installing ubuntu as I type this is wondering if it's possible to use a WPA, since there doesn't seem to be the option in setup.

Onto the horrible problem which I currently have:  when I try to start up, X screws up, I get a garbled ascii message telling me this, but at this point everything locks up.  Since I have no network connection, I can't ssh in and try and edit xconfig manually.  What can I do (if anything)?

Anybody ever run into this problem before?

---

### Post by Nis on 2005-04-10
More information needed, particularly hardware.  What brand/model wireless nic are you trying to use?  What graphics card and monitor are you using?  What do you mean 'locks up'?  Can you not even login under text mode?

---

### Post by itsjames on 2005-04-11
When I booted the machine using -s I noticed quite a few errors (mainly sound related -- modprobe was going crazy, but linux really hates this motherboard's onboard audio, so I can live with it).  X config file looks ok,  but I'm feeling somewhat disinclined to mess about with this trying to get it to work considering how frustrating it is.

When I say "lock up" I mean the keyboard completely stops reacting to input, so does the mouse.  Not much fun!

---

