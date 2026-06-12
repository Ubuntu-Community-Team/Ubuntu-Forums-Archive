---
title: "More serial mouse problems"
date: 2005-12-02
forum: General Help
---

### Post by KaiZen on 2005-12-02
I know that this question repeats itself over and over, but I searched the forum and found no answer that helps me.

I have an serial Genius netscroll mouse that doesn't work properly. Cursor is frozen. i tried:

sudo dpkg-reconfigure xserver-xorg

and it only asked about emulating 3 button and enabling scroll, nothing about port i'm using. It made xorg.conf like i'm using PS/2 mouse. Mouse doesn't work. Next thing I tried: loging in as root from terminal and editing 

pico (nano ;) ) /etc/X11/xorg.conf

an changing parameters "/dev/input/mouse" to "/dev/ttyS0" and Protocol PS/2 or something (can't recall, i'm not surfing from home) to "Auto". Didn't worked. Tried ttyS1 but still nothing.

I'm new to Ubuntu and Linux OS's.

Thanx in advance.

---

### Post by phil123 on 2005-12-19
I too have this identical problem. Any pointers will be well received. I was using Hoary Hedghog and when I upgraded to Breezy Badger bang went all my settings. Last time I will do that without strict supervision!!
phil123

---

