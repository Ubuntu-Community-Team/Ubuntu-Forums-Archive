---
title: "No Flash even Ubuntu Extras + Flash plugins are installed"
date: 2008-11-03
forum: General Help
---

### Post by rem on 2008-11-03
Hello,

I just upgraded to Intrepid Ibex from Hardy, everything seems to be ok, I am using the beta Nvidia plugin. I have the flash plugin installed, Ubuntu extras as well but no flash plugin showing in about: plugins and no flash playing on Youtube, etc ...

I tried to remove the plugin and the extras, then reinstall them again, also tried to install the plugin using the installer and the .deb provided by the Adobe download, tried to copy the libflashplayer.so in .mozilla/plugins and nothing ... can you help please?

Thanks!

---

### Post by DagMan on 2008-11-03
I had to uninstall flashplugin-nonfree and install adobe-flashplugin

---

### Post by rem on 2008-11-03
> **DagMan said:**
> I had to uninstall flashplugin-nonfree and install adobe-flashplugin

thanks for the tip but forgot to tell i already tried that as well...i noticed that everytime i am customizing my firefox appearance, the settings pops back into default mode when i restart it... it might be something to do with that?

---

### Post by rem on 2008-11-03
the output from the terminal is

```
LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-nonfree/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]

```

---

### Post by rem on 2008-11-04
The problem is solved!

I don't know under what circumstances, libnss3 was not changed to intrepid version hence the problem with Flash and maybe other troubles I didn't noticed yet. I had to force version to Intrepid for libnss3 and now everything works great!

:guitar:

---

### Post by tonybaqain on 2008-11-04
try this
```

sudo apt-get install libnss3-tools libnss3-dev

```

have fun :)

---

### Post by rem on 2008-11-04
> **tonybaqain said:**
> try this
```

sudo apt-get install libnss3-tools libnss3-dev

```

have fun :)

it was indeed libnss3 but not the tools or dev headers ... good it is fixed!

---

### Post by cactusrat on 2008-11-04
Thanks for the posts, I had been pulling my hair out the last couple of days to get this fixed.  I went the easy way through Synaptic.  Found the libnss3-1d and then Package -> Force Version and selected Intrepid version....and now I have Flash video w/sound.  Again, thanks.....

---

### Post by rem on 2008-11-04
> **cactusrat said:**
> Thanks for the posts, I had been pulling my hair out the last couple of days to get this fixed.  I went the easy way through Synaptic.  Found the libnss3-1d and then Package -> Force Version and selected Intrepid version....and now I have Flash video w/sound.  Again, thanks.....

i am glad it works for you too ...

---

### Post by Man of Kent on 2009-10-16
Just to let people know that I was having exactly the same problem and that this solution also worked for me :-)

---

