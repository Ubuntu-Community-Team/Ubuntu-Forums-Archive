---
title: "Projector suddenly disconnects in Ubuntu 17.04"
date: 2017-10-19
forum: Hardware
---

### Post by jander on 2017-10-19
Hey guys!

I have an LG laptop I use for my lectures. Ubuntu is the only installed OS.

Everything seems to work fine when I plug the projector. It has VGA input and I use an HDMI/VGA adapter, as my laptop lacks the VGA output. My usual setup is to mirror the laptop display. I use evince ou pympress to show PDF slides (beamer).

The problem is that without any warning or message Ubuntu stops recognizing the projector, as if I had pulled off the HDMI cable. When I check the displays in the configuration panel, only the built in display is available. After several seconds, it is recognized again. The issue usually starts happening after 10 to 30 minutes of presentation, but it's unpredictable.

I tried to extend the display instead of mirroring, but it stills disconnects. I also tried all sort of changes in resolution (for the projector AND the main screen) without success. The problem occurs with different projectors (LG and Epson were tested). I replaced the adapter too.

Never tested on a projector with HDMI input.

Can anyone point me to a solution or guide me where to look for logs that could help understand what's going on?

Thanks in advance.

---

### Post by jander on 2017-11-09
A 'bump' with syslog entries:

```
Nov  9 14:57:32 doryctinae gnome-shell[1368]: remove: i0x1920y0w1920h1080
Nov  9 14:57:32 doryctinae gnome-shell[1368]: pi:0
Nov  9 14:57:32 doryctinae gnome-shell[1368]: i:0 x:0 y:0 w:1920 h:1080
Nov  9 14:57:40 doryctinae gnome-shell[1368]: new: i0x1920y0w1920h1080
Nov  9 14:57:40 doryctinae gnome-shell[1368]: pi:1
Nov  9 14:57:40 doryctinae gnome-shell[1368]: i:0 x:1920 y:0 w:1920 h:1080
Nov  9 14:57:40 doryctinae gnome-shell[1368]: i:1 x:0 y:0 w:1920 h:1080
```

But there was no actual disconnection of the HDMI plug.

Could it be a hardware failure?

---

