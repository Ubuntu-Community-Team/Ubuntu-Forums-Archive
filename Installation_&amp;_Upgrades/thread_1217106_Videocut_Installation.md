---
title: "Videocut Installation"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by qwertyz123 on 2009-07-19
I'm trying to install [Videocut]("http://www.kde-apps.org/content/show.php?content=60826") so that I can make thumbnail previews of videos into one image (see the page for a example)
However I keep getting Floating Point Exception error in terminal once I open a file with it.

So I was wondering if anyone could show step by step how to install it properly, including the extra libs.

I'm using Jaunty (9.04)
Thanks beforehand :)

---

### Post by ZhuaSD on 2009-07-21
Yeah me too, it just closes out when opening an .avi file on 9.04

---

### Post by ZhuaSD on 2009-08-10
QFrameCatcher works.

I tried to install following some guide on the web, sorry I have no idea where now.

And it didn't work, so I didn't post about it.  Then later, it worked.

Its alright, could use some improvement.

---

### Post by keikoh on 2009-08-10
I get the same error too.

(6029) findLibraryInternal: plugins should not have a 'lib' prefix: "libkfilemodule.so"
(6029) KPluginLoader::load: The plugin "libkfilemodule" doesn't contain a kde_plugin_verification_data structure
[wmv3 @ 0x1bf7d20]Extra data: 16 bits left, value: 401F
Floating point exception

It was running fine before. 

Any idea how to fix this?

Thx

---

### Post by keikoh on 2009-08-10
Silly me. I got it fixed on my system. It works fine if I use it for more than 1 frame. Crash whenever I use to capture only a single frame.

Dunno if this could be the same problem mentioned here earlier.

---

### Post by shusai on 2010-01-04
The installation of these libraries with Synaptic fixed it for me:

libxine1-plugins
libxine1-all-plugins

I think, libexine1-gnome and libxine1-ffmpeg also were needed dependencies.

---

### Post by mike_tyrell on 2011-12-09
> **shusai said:**
> The installation of these libraries with Synaptic fixed it for me:

libxine1-plugins
libxine1-all-plugins

I think, libexine1-gnome and libxine1-ffmpeg also were needed dependencies.

I had the same problem it crashes when i add a video but I installed the above libs and its fine now. thanks for the fix ppl

---

### Post by Midnighter on 2011-12-15
Thanks muchly, your suggestion got it working for me also. Annoying that i turned out to be so simple, but glad to have it figured out. Much thanks for the advice. Cheers. :)

---

