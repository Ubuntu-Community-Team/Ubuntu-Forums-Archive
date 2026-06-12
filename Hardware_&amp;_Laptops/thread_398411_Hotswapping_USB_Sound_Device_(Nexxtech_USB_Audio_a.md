---
title: "Hotswapping USB Sound Device (Nexxtech USB Audio aka C-Media USB Audio Adapter)"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by Bjarne on 2007-04-01
Hello. I'm testing 6.06LTS on a laptop that I want to carry around with me from lecture to lecture. I'm currently only evaluating the live cd at home, but I want eventually to replace win2k with Ubuntu if I can get a few things worked out.

I'm trying to use a USB audio adapter that I picked up from Radioshack (The Nexxtech Audio Adapter, but I believe it's just a relabeled C-Media Audio Adapter). Ubuntu starts up fine and I hear the music that you get when you log in, and I can also play any music I want in Rhythmbox. All of that is great, so I'm pretty sure the audio adapter runs fine in Linux.

**The problem I'm having is when I want to unplug and replug the USB audio adapter.** I need to unplug the audio when I put the laptop in my bag or it won't fit/will break. Is there a proper procedure for doing this that I may have missed? If I have no sound programs running and I unplug the USB audio from my computer the OS doesn't seem to generate any errors at all.

I do get a notification in the kernel ring buffer (dmesg) when I unplug it, so the computer is recognizing that it's been unplugged. Here is the message:

```
[4299692.522000] usb 1-1: USB disconnect, address 2
```

However when I plug it back in to the same port I get no notifications in the ring buffer and Rhythmbox appears to play music, but there is no sound whatsoever.

When I try to *lsusb*, the program just sits there in D+ (uninterruptible sleep) status according to *ps aux*.

What can be done to get Ubuntu or Linux to handle the hot-swapping of my USB audio adapter? I more or less can't use Ubuntu or Linux unless I get this to work.

---

