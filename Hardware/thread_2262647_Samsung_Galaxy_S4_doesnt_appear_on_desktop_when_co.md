---
title: "Samsung Galaxy S4 doesnt appear on desktop when connected via USB cable"
date: 2015-01-26
forum: Hardware
---

### Post by matkobrcko on 2015-01-26
When I connect my phone to one of my usb ports it doesnt appear on desktop panel or anywhere else. Ive tried to plug in different ports but same result. Can anyone help please???

---

### Post by QIII on 2015-01-26
Hello!

Do you have the phone set to "charge only"?

I have an S4 that works fine.  Give me a second to check my settings.

---

### Post by matkobrcko on 2015-01-26
Hello
no it says connected as media device

---

### Post by QIII on 2015-01-26
OK.  Which release of Ubuntu are you using?  Where are you looking for the mount?

---

### Post by matkobrcko on 2015-01-26
12.04, on desktop panel and in home folder.

---

### Post by ajgreeny on 2015-01-26
12.04 was not very good with android mounting and it took me a long time to get my Acer Iconia A210 to show up, and then for no good reason I could find it stopped mounting and I just couldn't be bothered to keep working on it.

Now with 14.04, and by following the info at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702), it mounts automatically and I can do anything I need to regarding drag/drop adding and deleting files and folders.  If it is essential to you to be able to mount your phone, it could be worth upgrading or clean installing to Trusty; your choice.

---

### Post by QIII on 2015-01-26
Don't know why you aren't getting notification, but it won't mount in your home.  Ajgreeny's explanation is probably as good as any.

Try /mnt or /media.  Most likely the latter.

---

### Post by matkobrcko on 2015-01-26
probably do that thank you

---

### Post by efflandt on 2015-01-27
I gave up trying to get at files on my S3 in 12.04 because I could not get it to work at all even trying other MTP things. It would automatically show root directories of internal storage and microSD, but nothing under that, so could not get to any files. With my S3 in PTP mode it would show internal storage, but not microSD at all (where I keep my photos). So I resorted to using ConnectBot (ssh client), AndFTP (sftp client), and SSHServer apps on my phone to be able to scp or sftp either way (using my Linux ssh keys) over WiFi.

My S3 connected fine when I installed 13.10 (now obsolete) on my laptop. And since I did a fresh install of 14.04.1 on my desktop a couple of weeks ago, my S3 connects to that by USB no problem. Although, to open files from Linux I first need to copy them to Linux.

USB tethering (to use mobile data or as a WiFi client) worked fine without configuring anything in Ubuntu, even in 12.04. That came in handy when my DSL acted up temporarily.

---

