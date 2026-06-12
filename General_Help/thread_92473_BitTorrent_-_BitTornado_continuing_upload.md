---
title: "BitTorrent - BitTornado continuing upload"
date: 2005-11-19
forum: General Help
---

### Post by Henc on 2005-11-19
Using BitTorrent - BitTornado gui, 
So I download a file, and it keeps uploading till I close the window.
Then I close the window or switch the computer off.

The question is - how can I continue to upload the file after I have turned on the computer again.

Is it possible with this client at all?

---

### Post by Matt Houston on 2005-11-20
Was wondering the same thing

---

### Post by samir85 on 2005-11-20
Well you need to execute the torrent with BitTornado again.
After that you will be asked where the files should be saved there you give the location where you downloaded the files.

---

### Post by Henc on 2005-11-21
[QUOTE=samir85]Well you need to execute the torrent with BitTornado again.
After that you will be asked where the files should be saved there you give the location where you downloaded the files.[/QUOTE]

you mean - the *.torrent file? (afaik, they are in temp directory; after finishing download they are gone  ..somewhere)
Can you please give more precise instructions?

---

### Post by bored2k on 2005-11-21
You open BitTornado, load the file.torrent, when it asks you for a downloading directory, point it to the same place it was downloading before.

By the way, the updated BitTorrent (the one NOT on the repositories) already has a queue manager.

---

### Post by Henc on 2005-11-21
I used my `logical` skills and figured out why *.torrent   file is in temp directory.. 
only because when I open it with internet browser i choose to open it with a program not to save on the disk and than execute (yes, i managed to find out how to do that, too). I just had imagined that the client manages to deal with the torrent in sensible way (like some of Win clients did.. )


I did installed BitTorrent from here - [http://www.bittorrent.com/](http://www.bittorrent.com/) . But cannot run it. (from where? is this the same ?)

---

### Post by bored2k on 2005-11-21
Download the .tar.gz and run bittorrent.py.

---

### Post by Henc on 2005-11-22
[QUOTE=bored2k]Download the .tar.gz and run bittorrent.py.[/QUOTE]

it worked as I wanted! Thank you.

(first i installed from the debian package; yet dont care why it didnt work  :)

---

