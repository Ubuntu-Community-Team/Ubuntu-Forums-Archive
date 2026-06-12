---
title: "rtorrent prob (cant open .torrent files)"
date: 2008-07-14
forum: General Help
---

### Post by Me+ on 2008-07-14
Hi

So i download .torrent files to the desktop.

Fire up rtorrent. return>tab>desktop/

When it goes to open the .torrent file it says it is invalid.

How do i fix this? Could something be wrong in my config?

Thanks

---

### Post by shirilover on 2008-07-14
Keep in mind that desktop and Desktop are two different locations.
Have you tried to open the torrent file with another client to see if there is a problem with the file?

I prefer using .rtorrent.rc to watch a specific directory for torrents to load.

```

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/shirilover/torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

```

---

### Post by Me+ on 2008-07-14
hi
thx for the reply.

there must be something wrong with the way i am opening torrents.

The torrent is fine when i enter the browser location of the torrent file but no when i try to open it from the machine.

What is the correct way to do it, in real simple terms please

Thanks

---

