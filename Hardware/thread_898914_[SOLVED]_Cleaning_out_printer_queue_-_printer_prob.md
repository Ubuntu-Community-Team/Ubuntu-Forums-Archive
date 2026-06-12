---
title: "[SOLVED] Cleaning out printer queue - printer problems!!!"
date: 2008-08-23
forum: Hardware
---

### Post by zachthejones on 2008-08-23
Got a new printer because my old hp kicked the bucket...a nice Deskjet F4280. I plugged it in, turned it on, and in Kubuntu KDE 4.1 it was detected automatically and installed (using the drivers for the Deskjet F4280 - which is exactly what was used on my wife's Vista machine when i installed the same printer on it).

Everything seemed great except I went to print and....nothing. I tried to do a test page, and it said the job was submitted as number "77" or some crazy number. And still nothing happens.

My thought is that there are a bunch of print jobs left in the printer queue from when I was trying to print on my previous printer before I decided to get this one. Now all the jobs I'm sending are getting stuck behind these older jobs which have errors or something holding them in the queue.

Is there a Printer queue in Ubuntu i can access and purge?

If not, any suggestions on what I can do to get my nice new printer to work?

---

### Post by zachthejones on 2008-09-06
Okay. Since nobody out there seems to have any idea how to fix this, here's what I did that finally solved the issue:

Went to the HPLIP site:
[http://hplip.sourceforge.net/]("http://hplip.sourceforge.net/")

Downloaded the [latest version]("http://hplip.sourceforge.net/downloads.html") and followed the [installation instructions]("http://hplip.sourceforge.net/install/install/index.html").

the command to install is in the installation instructions. I did a custom install so I could oversee the options and in the end the test page printed out just like it was supposed to.

The main issue was, it seems, that the HPLIP availible in the archives isn't the latest. Does anyone out there know if there is a repo which might be more up-to-date?

---

