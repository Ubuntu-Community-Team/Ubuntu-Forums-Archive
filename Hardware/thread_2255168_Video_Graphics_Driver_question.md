---
title: "Video Graphics Driver question"
date: 2014-12-02
forum: Hardware
---

### Post by michael-piziak on 2014-12-02
On my PCSX emulator, I can choose between Xvideo Driver and Open GL Driver.

What is the difference ?

---

### Post by carlwsnyder on 2014-12-02
The Xvideo driver should work with software acceleration (using the main CPU) only, but work on just about any system which can display the emulator.

The OpenGL driver is supposed to work if your GPU (video driver) supports hardware based graphics acceleration under the OpenGL standard.

---

### Post by michael-piziak on 2014-12-02
I have tested PCSX many times with the Xvideo driver selected and tested it many times with the OpenGL driver selected.  
The end result:  The OpenGL driver will not work properly with larger resolutions selected.  The sound is choppy and the game play slows down.  Only the Xvideo driver works well for me.
p.s. I'm using an Intel Core 2 Duo system (4 gigs ram).

Thanks so much for your reply.  I am now marking this thread as solved.

---

