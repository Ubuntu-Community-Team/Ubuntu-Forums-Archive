---
title: "4L Does Not Detect Labelflash Drive"
date: 2008-08-05
forum: Hardware
---

### Post by kaoskorruption on 2008-08-05
I just installed "LaCie LightScribe Labeler" (4L) using this guide: [https://www.blogger.com/comment.g?blogID=886509866299451420&postID=4043822394727437597](https://www.blogger.com/comment.g?blogID=886509866299451420&postID=4043822394727437597)

Everything worked fine until I went to "Print Options" and it did not detect my DVD drive with Labelflash.

I don't know if this means anything, but I also noticed that whenever I clicked on "Print Options" I saw "Using /etc/lightscribe.rc".

One person suggested adding two library files to /usr/lib32, which I tried with no success.

Does anyone have any idea how to fix this?

---

### Post by UbMax on 2009-01-03
Use terminal window and try "4L-gui" (use sudo if needed). You should see something like "error while loading shared libraries: libstdc++.so.5 bla bla....". Close the application. Now, search the missing library with "find" (in my case it was in "/opt/lightscribeApplications/common/Qt/" directory) and copy in /usr/lib dir. Restart 4L-gui (this time you can use gksu) and try to detect the drive. It worked fine for my LG drive (Ubuntu 8.10). Hope can help.


Provate ad utilizzare la finestra terminale per lanciare il programma "4L-gui" e segnate l'eventuale messaggio d'errore. Dovrebbe dire qualcosa come "error while loading shared libraries: libstdc++.so.5 ecc.". Chiudete il programma se è partito e cercate la libreria in questione con find (io l'ho trovata in "/opt/lightscribeApplications/common/Qt/"); copiatela in /usr/lib e lanciate il programma. Se non ci sono altri messaggi d'errore dovreste trovare il vostro drive in Print Options (Ubuntu 8.10, drives LG TSSTcorp CDDVDW SE-S224Q (USB) e DH16A1L KH15 (internal))

---

