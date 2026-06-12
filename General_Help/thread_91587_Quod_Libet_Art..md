---
title: "Quod Libet Art."
date: 2005-11-17
forum: General Help
---

### Post by denisesballs on 2005-11-17
Has anyone gotten albumart working for Quod Libet? It wasn't in the repos, but i built it from source and still no good. Is it somewhere in the preferences or something?

---

### Post by Dr. Nick on 2005-11-17
As far As I know quod libet wont download the art for you, you have to do it manually and it will pick it up from the album directory, Mine displays the art built into the mp3 or the jpeg in the directory.

---

### Post by bugmenot on 2005-11-18
[http://www.sacredchao.net/quodlibet/wiki/Guide/Library](http://www.sacredchao.net/quodlibet/wiki/Guide/Library)

Adding Album Covers

To add an album cover to a group of songs, put a file named .folder.jpg or .folder.png in the same directory as the songs. Quod Libet also recognizes other file names containing cover or front as album covers, but folder is supported by many other programs as well. 

If you have many songs in a directory and want them to have different cover images, name the image after the song's labelid tag. If the song's labelid is RBR-003 for instance, you want to name the image RBR-003.jpg. Some tools can also embed cover images in MP3 files, and Quod Libet will also use those if it can't find an image in the directory. 

The Album Art plugin (which depends on the amazon.py module) will find album cover art for you.

---

