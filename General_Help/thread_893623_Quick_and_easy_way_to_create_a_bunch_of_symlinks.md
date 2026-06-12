---
title: "Quick and easy way to create a bunch of symlinks?"
date: 2008-08-18
forum: General Help
---

### Post by i.wanna.corndog on 2008-08-18
Hey everybody,

I have a quick question. I currently have a collection of music (various formats, e.g. mp3, ogg, flac) that is organized in a folder structure with artist and album. I would like to create a single folder that has symlinks to all of my music files without the folder structure.

Is there any sort of way to do this in a quick and easy fashion? Is there any sort of script or software that could be used to monitor my music library to automatically add symlinks when new songs are added?

Thanks!

---

### Post by kpatz on 2008-08-18
To build the symlinks:

```

find $HOME/dir_to_search -type f ! -type l -exec ln -s  \{\} $HOME/dir_to_put_symlinks_in \;
touch $HOME/.symlinksmade

```

The touch command creates a file whose date stamp will control this next script.

To update the symlinks with newly created files:
```

find $HOME/dir_to_search -newer $HOME/.symlinksmade -type f ! -type l -exec ln -s  \{\} $HOME/dir_to_put_symlinks_in \;
touch $HOME/.symlinksmade

```

The -type f searches for regular files (so things like directories, sockets, etc. are excluded).  ! type l means exclude symbolic links.  So you won't create links to links (especially handy if dir_to_put_symlinks_in is part of the directory structure you're searching. ;)

Obviously you'll want to change $HOME/dir_to_search to the base directory where your music files are, and $HOME/dir_to_put_symlinks_in to the directory where you want the symlinks placed.  You can also change the name of $HOME/.symlinksmade to whatever you like, as long as you change it in all places it's referenced.

---

### Post by i.wanna.corndog on 2008-08-18
Thanks! That was EXACTLY what I was looking for!

I'm going to assume I can add the update commands to cron, right?

---

