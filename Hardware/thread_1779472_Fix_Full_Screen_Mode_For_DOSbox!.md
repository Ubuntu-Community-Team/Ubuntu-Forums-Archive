---
title: "Fix Full Screen Mode For DOSbox!"
date: 2011-06-10
forum: Hardware
---

### Post by TFrog on 2011-06-10
I just recently loaded Natty Narwhal after experimenting with several other Debian variants.  My only complaint was the DOSbox application for running games.  Let me explain.  I'm currently running some very old hardware as you'll note in my signature.  This HP laptop has an Intell GM855 graphics subsystem so this fix may not work for everyone.

1)     Open up your dosbox.conf file found in /home/<username>/.dosbox folder with your favorite editor.

2)     Go to the section labeled [sdl].

3)     Locate the entry "fullresolution" and change it to the native resolution of your screen (my laptop is 1024x768.  Your screen may be different.).

4)     Locate the entry "output" and change it to "overlay".

5)     Go to the section labeled [render].

6)     Locate the entry "aspect" and change it to "true".

7)     Save your dosbox.conf file.

8)     Open up DOSbox application.

9)     Type "alt+enter" or "alt+return" depending on your keyboard to get to full screen mode.

10)    Spin up your favorite DOS game and see if it fixes the issue.  If not you'll have to tinker with your settings more.  I'm sorry if this doesn't help everyone.

---

