---
title: "[SOLVED] Any way to get a list of files included in a torrent to a text file?"
date: 2008-08-01
forum: General Help
---

### Post by kung fu buntu on 2008-08-01
Is there any way to get a list of files included in a torrent to a text file?


I need to grep my way out in a torrent with hundreds of files.

The perfect solution would be a search/filter in the torrent client. But I'm just too accustomed to azureus.
So having a way to do, in the command line, a listing of files included in a torrent file, would be nice.


Thanks.

---

### Post by happyhamster on 2008-08-01
- I don't know about azureus, but it's possible with the package "transmission-cli":

sudo apt-get install transmission-cli

- Navigate to where the torrentfile is, and run:

transmissioncli -i filename.torrent

- Or, to put the text directly in a textfile:

transmissioncli -i filename.torrent > files.txt

- For some info on the package, see: [http://linux.die.net/man/1/transmissioncli](http://linux.die.net/man/1/transmissioncli)

- A completely different way of doing this is just opening the .torrent file in a hex-editor and search for the filenames manually.

Good luck

---

### Post by kung fu buntu on 2008-08-02
Thanks.
Meanwhile I also found out about the btshowmetainfo in the torrent cli package.

---

