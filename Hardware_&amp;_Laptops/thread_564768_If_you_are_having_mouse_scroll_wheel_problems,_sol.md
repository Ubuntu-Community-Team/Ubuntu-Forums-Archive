---
title: "If you are having mouse scroll wheel problems, solution!"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by AstarothCY on 2007-10-01
Especially applies if your problems began after a distro upgrade (to Feisty or Gutsy).

My problem was that my scroll wheel was now working as forward and back instead of scroll up and down. The solution ended up being rather simple:

Open Synaptic Package Manager
search for package "imwheel" and completely remove
search for package "xbindkeys" and completely remove
if you have installed btnx then go to the setup directory and "sudo make uninstall" (same for btnx-config)
then reconfigure X (or manually edit xorg.conf, up to you)

This will obviously remove any app-specific settings you had in imwheel or your xbindkeys settings. This is for your own good. You will find that after you remove these, your mouse should work as normal. If you then want to customize it again, install these packages one by one and change only one thing at a time.

Sorry for the crudeness of this post but this problem has been frustrating me for a few days and I just want to get the solution out there.

---

### Post by atomicthumbs on 2007-10-01
My scroll wheel problem is that my crappy laptop has a complete lack of anything scroll-related, save the area on the right side of the touchpad.

But I use the trackpoint, not the touchpad. :(

---

