---
title: "Periodic Freezing for X minutes at a time"
date: 2008-09-22
forum: Hardware
---

### Post by compu73rg33k on 2008-09-22
Ever since version 7.10, my laptop will periodically freeze for up to 5 minutes. It does it under all conditions too - high usage (watching a video, torrenting, firefox open, etc. all open) but also under low usage (just staring at the desktop). It doesn't respond to ctrl+alt+backspace or even SysRq + Alt + B (and other SysRq) commands. Nevertheless, after a couple minutes it does catch up to speed. It's not a hardware problem either b/c this doesn't happen in Windows, only Ubuntu (not sure about other linux distributions). This is really frustrating when I'm in the middle of something like going through my homework and I have to sit and wait for it to unfreeze to scroll down the page. It's especially *annoying* when I'm playing music b/c the sound still works, but it stops progressing the song so it just repeats the same millisecond of sound over and over.

Anybody else experience similar issues on a laptop or other computer in general? It used to happen on my desktop as well, but since 8.04, it's stopped doing it on my desktop. I thought for a while it may be because of harddrive encryption as if the hard drive is freezing (because the hard drive light on my laptop always stays the same state during these periodic freezes (it's either on or off, which ever state it was currently in when the freeze started).

And sometimes it doesn't even unfreeze and "catch back up" like just now :( and I have to turn it off w/ the power button.

---

### Post by compu73rg33k on 2008-09-24
attached is my lspci

---

### Post by paulisdead on 2008-09-24
If you got another box, can you ssh into it and maybe run top.  You could also leave a terminal running top open to try and see if you can figure out what process is holding up the system.  Not sure if the screen still updates when it locks up in your situation, so it may or may not work.

Hopefully this will at least give you a spot to start from.

---

### Post by compu73rg33k on 2008-09-24
> **paulisdead said:**
> If you got another box, can you ssh into it and maybe run top.  You could also leave a terminal running top open to try and see if you can figure out what process is holding up the system.  Not sure if the screen still updates when it locks up in your situation, so it may or may not work.

Hopefully this will at least give you a spot to start from.
Alright thanks. The idea of sshing in sounds clever, but I'm afraid it's probably just going to hang when trying to connect. Nevertheless, I'll try it out and see if I can't get some results from top. Thanks for the tips.

---

