---
title: "Video Player problem in Lenovo T400"
date: 2009-07-19
forum: Hardware
---

### Post by sbaroi on 2009-07-19
I can't see any DVD or VCD in my Laptop : Lenovo T400. 
It has a builtin Intel Graphics Card.

I have VLC player, but still it doesn't work. 
My laptop just stucked ( hang ).. when I try to play any Video File.

I'm using Ubuntu 8.04 LTS

- SIMON

---

### Post by sarfarazkazi on 2009-07-19
Have you tried installing all the necessary multimedia codecs? Do you get any error message before the machine hangs?

---

### Post by sbaroi on 2009-07-19
Yes, I have install all the codecs. Also successfully installed VLC.
But still its not working.

One thing I should mention here, when I start the Hardware testing at the Video Testing time, my Laptop hang again.... So I think there is something in my AGP/Video Card.

- SIMON

---

### Post by vinutux on 2009-07-19
open synaptic
[B]
system>Administration>synaptic[/B] search gstreamer and install following plugins

gstreamer0.10-plugins-bad

gstreamer0.10-plugins-bad-multiverse

gstreamer0.10-plugins-ugly

gstreamer0.10-plugins-ugly-multivers

libdvdnav4




and install additional libdvdcss2 from mediubuntu repo [[COLOR="DarkGreen"]**www.medibuntu.org/**[/COLOR]]("www.medibuntu.org/")

---

### Post by sbaroi on 2009-07-19
No still its not working........

:(

What I'll do ???

- SIMON

---

### Post by sbaroi on 2009-07-19
I can see videos from Youtube....
Why I can't see movie with VLC or other player ?
I have restarted my laptop 2-3 times... but still no change...

---

### Post by vinutux on 2009-07-19
check you are able to open some avi or mpeg.

---

### Post by sbaroi on 2009-07-19
nothing with VLC.....

How can I see that, Ubuntu got the right graphics card for my.
my laptop has Intel GMA 4500 HD graphics card.

- SIMON

---

### Post by vinutux on 2009-07-20
in vlc **Tools>preferences>Video output** change output options save and restart....check one by one...

---

