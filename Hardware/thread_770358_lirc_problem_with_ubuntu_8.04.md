---
title: "lirc problem with ubuntu 8.04"
date: 2008-04-27
forum: Hardware
---

### Post by caotico on 2008-04-27
Hi!
I have lirc installed in my system. It's a Avermedia98 pci with ir. I just did:
# DEBIAN_FRONTEND=gnome sudo apt-get install lirc
I selected Avermedia98 and /dev/input/event6 for the ir inputs. Now if I press the volume up key, ubuntu(gnome) responds and turn up the volume.

If I do:
# cat /dev/input/event6
and I press the remote keys, some characters appears at the screen.

But... when I execute the irw command and press the keys, nothing appears in the screen. And, in the other hand, if I configured the .lircrc with mythubuntu-lirc-generator, programs (xine, mplayer, totem) dont respond to the remote keys.

What could be the problem? I dont know what I sould look. Everything seems properly configured but the received signal from /dev/input/event6 it is not being mapped to the correct key and the applications dont react to it. Only ubuntu(gnome) react.

Thanks!

---

