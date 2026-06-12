---
title: "Is ATI Fire GL2 compatible with Ubuntu hardy Heron?"
date: 2008-08-28
forum: Hardware
---

### Post by melolontha-melolontha on 2008-08-28
I already posed this question on [http://www.ubuntu-forum.de](http://www.ubuntu-forum.de), but I got no answer so far. Now I continue asking my question to a larger audience here.

I have a Dell Precision Worksation (built in 2001). It was used for CAD purposes under Windows 2000 before.

Now I want to use this old computer to try out Ubuntu. First I used the Ubuntu 8.04 LTS-32 Bit Live-CD from the German Book by Kofler.

The computer is equipped with a Fire GL2 graphics card from ATI Inc. Somewhere the year 2000 is printed on this board.This is an AGP-type of graphics adapter.

The Ubuntu Live CD does not recognize this graphics adapter correctly.

During start, the Ubuntu logo shows up on the screen for short time and vanishes again, then the start process runs in text mode only. There are many messages, all ending in [ok], at least the last ones which stay on the screeen.

Hitting ALT-F1 etc leads me to some command lines. But what do I have to enter in order to make the Gnome system start up in a proper VGA Mode?

The keyboard is not recognized either. Albeit being a german one, it reacts as an UA-ASCII keyboard. Since the graphical system does not start properly, I can not select tke keyboard type "German".

Alternatively, I tried the "Alternate CD" ubuntu-8.04.1-alternate-i386.iso. Now the keyboard reacts properly, but the graphics mode does not.

After reading [http://wiki.ubuntuusers.de/XServer_einrichten](http://wiki.ubuntuusers.de/XServer_einrichten) I followed the hints given there in order to configure the X-Server (sudo dpkg-reconfigure xserver-xorg). This was not sucessfull, however. First there came a question, if switching graphics shall be done via the Kernel-Framebuffer-device (whatever this is). For the first try I accepted the default <NO>. Then, the questions about the keyboard layout are risen, the question which I expected at that moment about automatic recognition of the graphics adapter did not come up.  Also I had no chance, to tell the manufacturer or type of graphics adapter.
If I answer the framebuffer-device question with <YES>, everything is alike! 

Now I am at the end of my knowledge of Latin. What to try out next? Is there any chance to get Ubuntu running on the system described above?

---

### Post by editus on 2012-03-03
Did you get it to work with Fire GL2?

---

