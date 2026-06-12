---
title: "Make rtorrent move files when done?"
date: 2008-09-16
forum: General Help
---

### Post by _sAm_ on 2008-09-16
I use rtorrent and want it to move the downloaded file when it is finished downloading. Right now rtorrent downloads to:/home/sam/downloads/torrent/ and I want it to move the file to /home/sam/downloads when its done. 

How should this line look like to get it as I want:

```
# When the torrent finishes, it executes "mv -n <base_path> ~/Download/"
# and then sets the destination directory to "~/Download/". (0.7.7+)

on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,~/Download/ ;d.set_directory=~/Download/"
```

Thanks for any help

---

### Post by mali2297 on 2008-09-17
Change all occurrences of [color=red]~/Download/[/color] to [color=red]~/downloads/[/color].

You need rtorrent version 0.7.7 or later for this to work.

---

