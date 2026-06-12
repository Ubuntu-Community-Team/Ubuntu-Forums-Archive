---
title: "Rythmbox not working"
date: 2005-11-23
forum: General Help
---

### Post by pappo on 2005-11-23
I am running 5.10 Breezy and all other media apps are working (xmms, real player10) but when I try to run rythmbox the gui appears and then nothing happens.
I cannot select any menu items at all.

Has anyone got rythmbox working under Breezy Badger ??

Thanks

Pappo

---

### Post by gapplewagen on 2005-11-23
Mine worked fine after install (had to install gstreamer0.8-mad to get mp3 but whatever).  Try running it from a terminal and see what happens.  You can also run it from a termnal with the -d switch to enable debug mode.

```
$ rhythmbox -d
```

Should at least show you where it's hanging.

---

### Post by pappo on 2005-11-23
Thanks for the reply.
I do have gstreamer0.8-mad installed as well.

Here is what I get when I ran rhythmbox -d, and tried to play an mp3 file:

[0x80f5060] [rb_shell_player_open_location] rb-shell-player.c:955 (12:37:46): Opening file:///home/pappo/Bytes of Bluegrass and Bluegrass Gospel/05_Nothin_Fancy_Do_Not_Pass_Me_By-.mp3...
[0x80f5060] [rb_player_sync_pipeline] rb-player-gst.c:454 (12:37:46): syncing pipeline
[0x80f5060] [rb_player_sync_pipeline] rb-player-gst.c:466 (12:37:46): PAUSING pipeline
[0x80f5060] [rb_player_sync_pipeline] rb-player-gst.c:454 (12:37:48): syncing pipeline
[0x80f5060] [rb_player_sync_pipeline] rb-player-gst.c:456 (12:37:48): PLAYING pipeline
Got error opening "file:///home/pappo/Bytes%20of%20Bluegrass%20and%20Bluegrass%20Gospel/05_Nothin_Fancy_Do_Not_Pass_Me_By-.mp3": Could not start pipeline playing
[0

---

