---
title: "ASUS TFP201 support"
date: 2012-10-22
forum: Hardware
---

### Post by Synoc on 2012-10-22
I am nut sure where to put this so:

I have an Asus Transformer prime 201 running android 4.1. every time I connect it it connects as a media device. Is there native ubuntu drivers for these? I would very much like stop playing FTP softball with my network and just connect the two via USB. 

running ubuntu 10.10

---

### Post by Synoc on 2012-10-26
bump

---

### Post by DuckHook on 2012-10-27
> **Synoc said:**
> Is there native ubuntu drivers for these?

...running ubuntu 10.10

You may wish to check out this thread:

[http://ubuntuforums.org/showthread.php?t=1785650&highlight=samsung+galaxy+tab](http://ubuntuforums.org/showthread.php?t=1785650&highlight=samsung+galaxy+tab)

The solution was for a Galaxy Tab, but might work with yours as well.

If that doesn't work you may wish to consider upgrading to 12.04 or 12.10 in the hope that a new kernel or modules will be preinstalled.

---

### Post by Synoc on 2012-10-27
that didn't do anything unfortunately but it gave me a jumping off point. found this 

[http://www.omgubuntu.co.uk/2011/08/asus-transformer-file-sync-mount-ubuntu](http://www.omgubuntu.co.uk/2011/08/asus-transformer-file-sync-mount-ubuntu)

gMPT did not work. not even available in he repos for 10.10... or at least for me.. but the latter one worked; "mptfs" in addition to not have to type it in multiple times i cheated and wrote a script to mount and unmount it. 

I would LIKE to click a launcher to run the script, but since it needs sudo privileges, I can't get it to work unless I use Application in Terminal so it will prompt me for a password. Is there a  way I can run it without sudo privs?

Addition:
If you try to edit a file on the tablet, you cannot again save it to that file. I had to save it to the PC then delete file from the tablet, then put it back on from the computer. I assume this is because it is MTP and not designed for editing files.

---

