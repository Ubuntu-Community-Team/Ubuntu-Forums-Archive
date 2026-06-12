---
title: "rhythmbox doesn't play after upgrade"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by prezbedard on 2009-03-31
I'm not sure if this is related to my upgrade to 8.04 LTs which I did less then a week ago but now of having a number of different issues this being another.

When I try to play a file in rhythmbox no matter it be mp3 or ogg what happens is it says its playing but there is no sound ,the progress slider doesn't move, and the time elapsed counter stays at 0:00. When I run rhythmbox in a terminal here is what I get.

```
greg@gregnix:~$ rhythmbox song.mp3
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory

(rhythmbox:6880): Rhythmbox-WARNING **: Could not open device /dev/radio0

(rhythmbox:6880): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed



```
I have no real idea what the radio device would be. It's just a standard built in sound card.
I have tried reinstalling. no luck.
Checked all sound setting. Looks fine.

The sound otherwise seems to work for th most part.

Thanks!

---

### Post by Evelyn on 2009-04-01
I have the exact same problem!  I upgraded quite a while ago, don't remember when, but I'm running 8.04 also.  I reported this as a bug today.  Here is a link to the bug report. [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/353566](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/353566)

---

### Post by prezbedard on 2009-04-02
I have resolved this though hadn't had a chance to update.

Here is what I did.

> ok I did a bit of what I know how to do. I checked the services via gui under administration and the service named Audio Setting alsa-utils was unchecked. I checked and it worked!! Also I did notice that it appears the radio station I listen to via a website conflicts however that didn't seem to be the case when the service wasn't running.

---

### Post by Evelyn on 2009-04-02
"ok I did a bit of what I know how to do. I checked the services via gui under administration and the service named Audio Setting alsa-utils was unchecked. I checked and it worked!! Also I did notice that it appears the radio station I listen to via a website conflicts however that didn't seem to be the case when the service wasn't running."

I have alsa-utils already installed.

rie-rie@Rie-rie:~$ rhythmbox --debug
(21:49:55) [0x80dc408] [rb_debug_init_match] rb-debug.c:153: Debugging enabled
(21:49:55) [0x80dc408] [main] main.c:184: initializing Rhythmbox 0.11.5
(21:49:55) [0x80dc408] [rb_threads_init] rb-util.c:460: GMutex isn't recursive
(21:49:55) [0x80dc408] [main] main.c:192: going to create DBus object
(21:49:55) [0x80dc408] [main] main.c:346: THE END
rie-rie@Rie-rie:~$

Does this help?

---

### Post by prezbedard on 2009-04-03
I did too. Make sure the service is running.


> **Evelyn said:**
> "ok I did a bit of what I know how to do. I checked the services via gui under administration and the service named Audio Setting alsa-utils was unchecked. I checked and it worked!! Also I did notice that it appears the radio station I listen to via a website conflicts however that didn't seem to be the case when the service wasn't running."

I have alsa-utils already installed.

rie-rie@Rie-rie:~$ rhythmbox --debug
(21:49:55) [0x80dc408] [rb_debug_init_match] rb-debug.c:153: Debugging enabled
(21:49:55) [0x80dc408] [main] main.c:184: initializing Rhythmbox 0.11.5
(21:49:55) [0x80dc408] [rb_threads_init] rb-util.c:460: GMutex isn't recursive
(21:49:55) [0x80dc408] [main] main.c:192: going to create DBus object
(21:49:55) [0x80dc408] [main] main.c:346: THE END
rie-rie@Rie-rie:~$

Does this help?

---

