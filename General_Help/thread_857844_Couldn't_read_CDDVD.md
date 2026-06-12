---
title: "Couldn't read CD/DVD"
date: 2008-07-12
forum: General Help
---

### Post by cf1709 on 2008-07-12
I have Sony DRU-820A and when I insert a data CD, the contents would be displayed but the contents (opening media files with codecs already installed) couldn't be opened. I tried to copy the contents onto the desktop but I'm getting an "input/output error".

I tried doing the same thing in Windows and nothing goes wrong. Is there something wrong with Ubuntu on how it reads CDs? How can I change it? I hope somebody can help. Thanks.

---

### Post by logos34 on 2008-07-12
with the data cd mounted, what does this show

ls -l /media/cdrom0

?

(or maybe it's cdrom1)

---

### Post by cf1709 on 2008-07-12
> **logos34 said:**
> with the data cd mounted, what does this show

**ls -l** /media/cdrom0

?

(or maybe it's cdrom1)

It's "cdrom0"

I don't understand the thing in bold as I didn't see it anywhere.

---

### Post by logos34 on 2008-07-13
its a command--run it in the terminal

---

### Post by PGScooter on 2008-07-13
```
ls -l
``` simply tries to list the files of the subsequent folder using a long listing format

---

### Post by fenian on 2008-07-13
run this command and post the results...

>  gedit /etc/udev/rules.d/70-persistent-cd.rules

---

### Post by logos34 on 2008-07-13
> **PGScooter said:**
> ```
ls -l
``` simply tries to list the files of the subsequent folder using a long listing format

no, the whole thing:

**ls -l** /media/cdrom0

---

### Post by ghost_ryder35 on 2008-07-13
> **cf1709 said:**
> I have Sony DRU-820A and when I insert a data CD, the contents would be displayed but the contents (opening media files with codecs already installed) couldn't be opened. I tried to copy the contents onto the desktop but I'm getting an "input/output error".

I tried doing the same thing in Windows and nothing goes wrong. Is there something wrong with Ubuntu on how it reads CDs? How can I change it? I hope somebody can help. Thanks.
what type of files are these (mp3's, video)?  if it is mp3's and so forth try installing the gstreamer plugins to help decode this.

---

