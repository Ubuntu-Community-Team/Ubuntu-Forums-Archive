---
title: "update-grub wrecked my menu.lst"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by Muzer on 2009-07-30
I did an update when I had modified my menu.lst slightly. When the installation asked me whether or not I wanted to replace my current one, I happened to be in another tty. When I switched back to the installation, I think I must have pressed enter or something (though I swear I only pressed down), since it selected "keep my current configuration file" and went on. So, after the installation, I checked my menu.lst, and sure enough it hadn't been updated with the new kernel. So, I ran sudo update-grub. It didn't change anything. I ran it again, and it REMOVED ALL OF THE KERNELS from the list!

How would I go about getting it to regenerate the file from scratch?


EDIT: Note that I haven't (yet) rebooted - I don't dare to (it's a netbook and it would take a few hours to make a new USB image with all my USB sticks being crap) - so I'm waiting patiently for what to do!

#EDIT2: Resolved - just backed it up, deleted and ran update-grub again.

---

