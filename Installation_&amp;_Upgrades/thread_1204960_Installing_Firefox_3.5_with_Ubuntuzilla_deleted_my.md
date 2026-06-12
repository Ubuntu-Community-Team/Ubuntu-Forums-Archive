---
title: "Installing Firefox 3.5 with Ubuntuzilla deleted my plugins, application associations"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2009-07-05
EDIT: Wow, I should have read the Ubuntuzilla site more closely. They provide instructions for uninstalling Firefox 3.5 and reverting to the version in the repositories. I did so and it restored everything, including my plugins. I'm not sure what the problem is with installing Firefox 3.5, but I guess I'll find a different way to do it. Forum admin, please mark this thread solved or delete it (not much use in archiving it, the solution is on the Ubuntuzilla site).

I really want to run Firefox 3.5 in Ubuntu, not only for the features but also to use Weave to sync by stuff between Firefox in Ubuntu and Vista (I dual-boot). It seemed the easiest way to do this was to use Ubuntuzilla, which I thought would install the newer version alongside the already-installed Firefox 3. It appears to have done that, somehow, without listing any new packages in Synaptic. 
The browser runs fine, but for some reason all of my plugins (flash, etc.) got erased and my application associations (open with...) reset. The backup folder that Ubuntuzilla created does not have a "Plugins" directory in it, which should be there (right?), so I can't copy my old stuff manually. Also, for some reason I can't manually launch "firefox-3.0" via terminal; it starts the compatibility checker and tells me Weave won't work (Firefox 3.5 only) and then when Firefox tries to start it fails with: ```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

```Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
At this point, I'm afraid to do any more without knowing exactly what I'm doing. Can anyone give me advice as to how to get my plugins re-installed (preferably without doing it manually)? The application associations are a bit tricky, but I can probably just set them again.
Alternatively, I'll gladly go back to using Firefox 3.0 if anyone can give an easy way to do so.

---

