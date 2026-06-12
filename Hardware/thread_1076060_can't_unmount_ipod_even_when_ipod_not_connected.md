---
title: "can't unmount ipod even when ipod not connected"
date: 2009-02-20
forum: Hardware
---

### Post by v1nsai on 2009-02-20
Owning an iPod suddenly became an option when I realized you don't need iTunes to use it with linux, so now that I'm up and running with ubuntu + gtkpod, ubuntu seems to get along so well with my iPod that it won't unmount it.  I've got 2 different icons sitting on my desktop actually, unmount commands do nothing.  They're not hurting anything, it's just kind of annoying.

I've tried 'sudo chmod +s /usr/bin/eject' and also 'sudo eject nameOfIpod' but neither have done anything.  Is there any way I can get rid of these?

---

### Post by v1nsai on 2009-02-21
Fixed some configuration problems with gtkpod and after I got it syncing properly through that my mount/eject problems went away too.  If anyone else is having this problem try configuring your management software if it returning any errors.  My issue was solved by 'sudo apt-get install'ing 'lame' and 'flac'.

---

