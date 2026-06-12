---
title: "What's the best way to watch a DVD movie?"
date: 2005-11-24
forum: General Help
---

### Post by cayblood on 2005-11-24
After installing some of the non-free codecs and such, I'm able to use mplayer to play a dvd movie.  However, when I try to increase the size of the movie window, the window changes but the actual portion where the movie is being played doesn't change size at all.  So, for example, if I set it to fullscreen mode all I get is a big black screen with a small movie window in the center.  Is this a configuration error or is mplayer just lacking in this regard?  What do others recommend as the best player to use to watch dvds?

---

### Post by Bachstelze on 2005-11-24
To fix this issue with Mplayer, go to the Configuration panel > Video > set the output device to 'xv'.

However, I think VLC is a much better player.

---

### Post by RAOF on 2005-11-24
Totem also works pretty well.  If you want to use it for playing dvds, though, you'll need the totem-xine backend.  The totem-gstreamer backend doesn't handle dvd menus well at all.

---

### Post by SuperMike on 2005-11-24
[QUOTE=RAOF]Totem also works pretty well.  If you want to use it for playing dvds, though, you'll need the totem-xine backend.  The totem-gstreamer backend doesn't handle dvd menus well at all.[/QUOTE]

This is exactly the info I got from a Brazilian coworker I have. I took his advice and was well-pleased. This is solution is what I recommend.

---

### Post by bored2k on 2005-11-24
What's the best way to watch a DVD movie? with the monitor **on**.

I'd recommend VLC&Mplayer once it's on.

---

### Post by Xian on 2005-11-24
[QUOTE=HymnToLife]However, I think VLC is a much better player.[/QUOTE]
VLC, Xine, Totem, and Mplayer will all do the job. The one you prefer will likely have something to do with individual preferences. The nice thing about VLC is that it works just as good in Windows, and I love to promote an application that can perform equally well in Linux and MSoft.

---

### Post by Bachstelze on 2005-11-24
In fact, Mplayer won't eactly do the job for me, since I have a laptop with widescreen (16:9 ratio) and when I want to see a 4:3 video fullscreen, it is too much "full" (i.e. the video takes the WHOLE screen, so it's kind of streched). I don't have this problem with VLC, nor with Totem.

---

### Post by cayblood on 2005-11-24
I couldn't figure out how to get VLC to play my dvd.  I chose file -> open disc -> DVD (with menu) and then clicked play but nothing happened.  I was able to get mplayer and totem working.  Thanks for the tips.

---

### Post by Bachstelze on 2005-11-24
To get VLC read the DVD, you have to enter the mounting point of your drive in the "Location" area. For me it is /media/cdrom0. But if Mplayer works for you, you won't need VLC.

---

