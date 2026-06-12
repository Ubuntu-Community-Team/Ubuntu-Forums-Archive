---
title: "Intel i7 for running 2 powerful X sessions"
date: 2010-06-14
forum: Hardware
---

### Post by nolanpro on 2010-06-14
Just wondering what people's thoughts are on this. I need both a new desktop and a media center PC. So I said, hey, why not save some money and make them the same system.

I'd like to get an i7 system and run 2 different X sessions, one for the desktop and one for the media center. Both would have their own keyboard and mouse, graphics card has 2 dvi ports.

I need to be able to decode/playback 1080p x264 etc (mplayer or vlc). on the media center while at the same time running somewhat resource intensive processes on the desktop side.

Can (or 'should') a single i7 machine handle this? Is Ubuntu's linux kernal optimized for the i7? Should I install x86 or 64 bit Ubuntu?

Just looking for ideas or gotchas for this potential setup before I go drop some cash. Thanks!

---

### Post by uOpt on 2010-06-14
People did that just fine with Pentium-Pros. Any 2.4 GHz Phenom will do it just fine.

Be aware, however, that neither the binary NVidia drivers nor the binary ATI drivers support dual-console, aka have more than one keyboard/mouse in one X11 server with different inputs assigned to different screens.

If anything the Xorg drivers support this but as you might be aware, Xorg is completely dropping classic dual-screen support (in favor of xrandr). Xorg might still work when you have two graphics cards.

---

### Post by nolanpro on 2010-06-14
Thanks for the info, I'm definitely going to have to do my homework on the NVidia drivers, with a possible work around being 2 separate video cards rather than one dual head card. Thanks again

---

### Post by uOpt on 2010-06-15
> **nolanpro said:**
> Thanks for the info, I'm definitely going to have to do my homework on the NVidia drivers, with a possible work around being 2 separate video cards rather than one dual head card. Thanks again

To make that clear: the binary nvidia drivers don't support this even with 2 video cards. With 2 video cards you might have a chance with pure Xorg drivers.

---

