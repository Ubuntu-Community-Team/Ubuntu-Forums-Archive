---
title: "Command line torrent creator"
date: 2008-07-20
forum: General Help
---

### Post by antm88 on 2008-07-20
So basically I have a folder containing about 300 folders, each one i want to be a separate torrent. I REALLY REALLY don't want to have to manually add each one to deluge so does anyone know of a command for creating a torrent?

(all I need is torrent name = folder name, torrent contents = folder contents, nothing else fancy like trackers)

I can write the script to batch create if someone gives me an example way of doing it for a single folder

thanks very much for any help!!

ant

---

### Post by ajmorris on 2008-07-22
hi there,
have you tried the "CreateTorrent" application? It is a command line tool to create torrent files...

AJ

---

### Post by toastguy on 2008-09-07
The only problem with CreateTorrent, you're only able to add one TRACKER. It does not have the ability to handle more than one tracker.

---

### Post by hyper_ch on 2008-09-07
for adding more trackers you can then use [http://www.torrenteditor.com](http://www.torrenteditor.com)

---

### Post by toastguy on 2008-09-07
I think you missed the point of this thread. We're looking for a COMMAND-LINE torrent creator. You're link is something that IS NOT command line.


**However I did find a working solution** using BitTornado ([www.bittornado.com]("http://www.bittornado.com")). The linux download is a python application . All you must do to properly install is have Python running on your system of 2.3.x or higher(Ubuntu should have it already installed).

1) Install BitTornado.
2) and Configure the command like file btmakemetafile.py







> **hyper_ch said:**
> for adding more trackers you can then use [http://www.torrenteditor.com](http://www.torrenteditor.com)

---

### Post by hyper_ch on 2008-09-08
toastguy/antm88: you use two different forum accounts?

---

