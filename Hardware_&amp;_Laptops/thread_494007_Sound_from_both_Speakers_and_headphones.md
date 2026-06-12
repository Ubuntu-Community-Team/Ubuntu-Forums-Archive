---
title: "Sound from both Speakers and headphones"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by Maverynthia on 2007-07-06
I've looked at some of the threads here however they haven't been any help.

Basically I get to the  "edit modprobe.conf" the only problem is that I don't have that file NOR do I have the modules.conf that some have said to modify.

I also found another one that said to stop the sound drivers and uninstall them... how do I do that? That also wasn't explained... :(

I'm on a Toshiba Satellite trying to get the hda-intel driver to work.

---

### Post by DagMan on 2007-07-07
instead of modprobe.conf try the options in the /etc/modprobe.d/alsa-base, at the bottom and commenting any other referances down there to the module if you find any.
This is what worked on my satellite, post number 8 of this thread, but there are other things to put in the file as options which you will find looking around.  auto seems to me like a good place to start.  There are a lot of threads and a lot of different options that worked for people if you search for toshiba sound in the forum.  I wouldn't worry about compililng the alsa driver until you've searched and exhausted all other options.

---

