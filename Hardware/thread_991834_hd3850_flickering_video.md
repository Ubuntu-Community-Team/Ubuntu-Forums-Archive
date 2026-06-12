---
title: "hd3850 flickering video"
date: 2008-11-24
forum: Hardware
---

### Post by superuser on 2008-11-24
Hello!

It's been a while since I droped my last post here -- with everything working you can't really complain, can you?

I do have one problem now, though. In my desktop computer I've got an ATI/AMD HD3850 (Hd 3850) video card. I installed the latest fglrx drivers using the Ubunut-stock-method that comes with ubuntu 8.10.

When watching video, I get horrible flickering using compiz and less so when de-activating it. But there is still a considerable flickering (or horizontal lines when the camera moves fast for example) in videos which used to display just fine on my notebook.

Thanks for your help
su

---

### Post by gatman3 on 2008-11-24
I experience the same thing with the HD 3650.  I think the problem is the Xv driver and how compiz does DRI, but I just have a vague understanding of these issues.  The only workaround I have found is to use X11 as the output driver for mplayer video (-vo x11).  The downside is that, at least on my machine, the X11 driver isn't fast enough to show full screen video.  Perhaps there is a way to configure your favorite video player to disable the desktop effects when playing in full screen mode?  I'll tune in here and see if anyone has any suggestions.

---

### Post by chastrell70 on 2008-11-24
I Don't know if will help. I have a HP ze5700 that the screen would flicker in certain conditions like Autum screen saver and other 3D graphics. I believe in not overlooking the simple things. after finding all the hidden screws I disassembled case around LCD. unplugged and reconnected the cable to the LCD and the problem stopped for about a month. I did the same and haven't had that problem since. Been 6 months now. hope this helps. Very small connection problems can cause big headaches, and are usually very easy to fix.

---

### Post by superuser on 2008-11-24
> **gatman3 said:**
> I experience the same thing with the HD 3650.  I think the problem is the Xv driver and how compiz does DRI, but I just have a vague understanding of these issues.  The only workaround I have found is to use X11 as the output driver for mplayer video (-vo x11).  The downside is that, at least on my machine, the X11 driver isn't fast enough to show full screen video.  Perhaps there is a way to configure your favorite video player to disable the desktop effects when playing in full screen mode?  I'll tune in here and see if anyone has any suggestions.

As I said, I'm _not_ using compiz, but video playback still isn't perfect. mplayer -vo x11 doesn't work in fullscreen mode for me.

gatman3, thanks for your tip. I tried an analogous cable, but the problem still exists. And it only exists in Linux, I have to say.

Anyone tried the radeonhd drivers for 3850-ish cards yet?

su

---

### Post by gatman3 on 2008-11-25
You might also try the newer pre-released fglrx driver.  To enable it, go into synaptic, find Setting->Repositories->Updates and click Pre-released updates.  Then click Reload and see if there is a newer fglrx than the one you are using, and try installing it and see if it helps.

---

