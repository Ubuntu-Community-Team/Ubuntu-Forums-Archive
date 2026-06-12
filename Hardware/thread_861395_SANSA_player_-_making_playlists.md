---
title: "SANSA player - making playlists"
date: 2008-07-16
forum: Hardware
---

### Post by marie-p on 2008-07-16
Hi,

I am thinking of getting a new sansa mp3 player (the clip one) and I know it is possible to have playlists created with Windows Media Player. Is there a way to make the playlists in ubuntu?

---

### Post by bubieyehyeh on 2008-08-30
> **marie-p said:**
> Hi,

I am thinking of getting a new sansa mp3 player (the clip one) and I know it is possible to have playlists created with Windows Media Player. Is there a way to make the playlists in ubuntu?

If you running in MSC mode (ie mounted as a usb drive). You can copy m3u playlist files to the player, the filename need to be relative to the directory containing the m3u file and have windows directory seperators

e.g.

/media/SANSA_CLIP/file.3u
/media/SANSA_CLIP/Music/file.mp3

in file.m3u Music\file.mp3

I use fapg (ubuntu package) with w and b flags to create the m3u files.

---

### Post by shane2peru on 2008-09-12
> **bubieyehyeh said:**
> If you running in MSC mode (ie mounted as a usb drive). You can copy m3u playlist files to the player, the filename need to be relative to the directory containing the m3u file and have windows directory seperators

e.g.

/media/SANSA_CLIP/file.3u
/media/SANSA_CLIP/Music/file.mp3

in file.m3u Music\file.mp3

I use fapg (ubuntu package) with w and b flags to create the m3u files.

I'm trying to figure this out too, and found this post.  Can you explain a little more on that?  I mean, make is so simple that I can understand it. :)  The m3u file should look like this:
```

Music\songname.mp3
```
or should that slash be the other way?  Also, can you just give an example of how you use fapg?  Looks like a very interesting app, and I'm reading the man on it, but if you can give an example that would be great! Thanks!

Shane

---

