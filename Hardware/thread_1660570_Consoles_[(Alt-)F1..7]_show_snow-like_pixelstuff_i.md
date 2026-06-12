---
title: "Consoles [(Alt-)F1..7] show snow-like pixelstuff instead of a readable console font"
date: 2011-01-05
forum: Hardware
---

### Post by Mickey S. on 2011-01-05
Hi!

I'm having the same problem with my Ubuntu Linux 10.04 Lucid 64 bit installation like outlined there:

  [http://ubuntuforums.org/showthread.php?t=330628](http://ubuntuforums.org/showthread.php?t=330628)

All my forum search pretty much ended up with a link in one way or another to this thread.

Unfortunately, removing the "quiet" and "splash" options like they suggested didn't fix the problem for me. I have configured grub to start in 640x480 vga mode (this first screen, however, can be read). My machine is an HP Pavilion dv8 (intel i7).

The motivation is I'm trying to update my nVidia driver. The process is only gonna work when the X-server isn't active and the machine is not in runlevel 1. But switching to a non-X-mode or -runlevel hangs my machine or renders the screen unreadable. Anyway, I'm pretty much stuck in this regard.

Anyone to tell me how to configure text mode consoles the right way?


Thanks,

 -Mike

---

### Post by Mickey S. on 2011-01-06
Hi!

After some desperate hours of continuously searching the web on how to fix the console problem ;o) it turned out that I would have to find an appropriate textmode for the consoles myself.

So, finally after changing the following line of the grub2's linux boot section into something like this:

  linux    /boot/vmlinuz-2.6.32-27-generic... vga=891

I've been successful setting the framebuffer to a resolution that obviously matches my hardware / display making the consoles readable again. Vga mode 891 relates to 1280x720x24, a true color 16:9-AR one, that seems to work there.


Thanks,

 -Mike

---

