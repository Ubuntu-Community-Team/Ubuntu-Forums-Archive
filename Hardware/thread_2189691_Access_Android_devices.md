---
title: "Access Android devices"
date: 2013-11-23
forum: Hardware
---

### Post by manudo on 2013-11-23
I need to access the file contents in my Android phone like I do in Windows, I connect my phone and nothing happens, how do I mount it?
Thanks in advance. :)
Got precise, by the way.

---

### Post by frogeyedan on 2013-11-24
you could try wifi transfer pro from the android market depending on what you mean by access

---

### Post by manudo on 2013-11-24
> **frogeyedan said:**
> you could try wifi transfer pro from the android market depending on what you mean by access

Well, good idea.
I mean access like getting music, photos. Transfer, you know, the usual.

---

### Post by manudo on 2013-11-26
When I connect my phone in Windows it sees the two memories, the internal storage and the SD Card and can get archives, delete, whatever I want.
Can I see the files like that? With nautilus or other software?

---

### Post by rackit on 2013-11-26
When I connect to my ubuntu box, assuming my phone is set to "Mass Storage", it shows up as "Kyocera USB Modem" and opens to the root of the SD Card. I'm running ubuntu 13.10 unity desktop. I did have to make sure that the cable was fully seated.

---

### Post by Mark Phelps on 2013-11-27
To the OP: if your phone is running Android ICS or newer -- it will not HAVE the Mass Storage option, as Google removed that from Android with the ICS update.

---

### Post by manudo on 2013-11-27
> **Mark Phelps said:**
> To the OP: if your phone is running Android ICS or newer -- it will not HAVE the Mass Storage option, as Google removed that from Android with the ICS update.

I wonder why, but if you say so, I'll do that with Wi-Fi transfer...
Thanks.

---

### Post by efflandt on 2013-11-28
I installed SSHServer, AndFTP (which can do sftp), and ConnectBot (ssh client) apps on my Samsung S3 and put my ssh keys on it, so I can sftp or scp from either end to copy files over WiFi (and ssh to/from the phone). I could not get any of the mtp things to work properly from 12.04 on the USB cable.

---

### Post by manudo on 2013-11-29
> **efflandt said:**
> I installed SSHServer, AndFTP (which can do sftp), and ConnectBot (ssh client) apps on my Samsung S3 and put my ssh keys on it, so I can sftp or scp from either end to copy files over WiFi (and ssh to/from the phone). I could not get any of the mtp things to work properly from 12.04 on the USB cable.

Wait, wait, wait. What?
What ssh keys?

---

### Post by SeijiSensei on 2013-11-29
Decent support for the MTP protocol doesn't appear before 13.04.  For mass file transfers I suggest Acrosync, an rsync app for Android, over wifi. If you want use a USB cable, you'll need to upgrade Ubuntu.

---

### Post by partloer on 2013-12-01
I have a similar problem I transfer files over bluetooth while not ideal it does work (assuming you have bluetooth on your computer).

---

### Post by manudo on 2013-12-01
I'll upgrade Ubuntu, thanks.

---

### Post by manudo on 2013-12-01
> **partloer said:**
> I have a similar problem I transfer files over bluetooth while not ideal it does work (assuming you have bluetooth on your computer).

I use a custom ROM that has bugs with Bluetooth, so, no.

---

### Post by viaciofano on 2014-05-04
i have 12.04 lts version and would like to transfer files from my android phone. so is this possible on leter versions from what you mention?

---

