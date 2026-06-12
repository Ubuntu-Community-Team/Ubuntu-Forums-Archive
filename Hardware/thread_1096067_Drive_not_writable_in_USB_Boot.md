---
title: "Drive not writable in USB Boot"
date: 2009-03-14
forum: Hardware
---

### Post by gluxon on 2009-03-14
So I've got ubuntu 8.10 installed to my SanDisk Cruzer Micro 8gb through the usb startup utility in System --> Administration --> Make usb startup disk

But whenever I boot up, my drive is mounted in /cdrom and not writable through me.

However the user root can write to it.

So I have to open up a terminal and type "sudo nautilus" whenever I want to write to my flash drive.

But... I also have wine 1.0.1 and whenever I try running an application in wine that needs to open up a file from my flash drive it doesn't have the right permission to write the file.

Normally in a normal Linux application (like OpenOffice.org) I just type "sudo openoffice -impress" and it opens up Impress... and it has the permissions necessary to write a file in my flash drive.

I've tried typing "sudo wine "/cdrom/PortableApps/FirefoxPortable/FirefoxPortable.exe" and it gives me "Wine is not owned by you" or something like that. I've also tried mounting my drive again in "/home/gluxon/USB". No change, wine applications still can't write to it.

So... there are two solutions. Get wine working with root or make my flash drive writable by me.

If anybody can tell me how to do this, I would deeply appreciate it.

Thanks.

---

### Post by gluxon on 2009-03-15
Bump.

I still need help.

---

### Post by gluxon on 2009-03-21
bump

---

### Post by gluxon on 2009-03-22
Bump

---

### Post by gluxon on 2009-04-05
bump, anybody?

---

