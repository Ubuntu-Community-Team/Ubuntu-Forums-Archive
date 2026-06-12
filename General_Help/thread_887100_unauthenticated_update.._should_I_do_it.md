---
title: "unauthenticated update.. should I do it?"
date: 2008-08-11
forum: General Help
---

### Post by dskyracer on 2008-08-11
I am getting an update notification in gutsy gibbon that tells me the following updates can't be authenticated. Should I go ahead and install the updates anyway? Here is what it's saying can't be authenticated.

ffmpeg (version 3:0.cvs20070307-5ubuntu4.1) will be upgraded to version 3:0.cvs20070307-5ubuntu4.1+medibuntu1
libavcodec1d (version 3:0.cvs20070307-5ubuntu4.1) will be upgraded to version 3:0.cvs20070307-5ubuntu4.1+medibuntu1
libavformat1d (version 3:0.cvs20070307-5ubuntu4.1) will be upgraded to version 3:0.cvs20070307-5ubuntu4.1+medibuntu1
libavutil1d (version 3:0.cvs20070307-5ubuntu4.1) will be upgraded to version 3:0.cvs20070307-5ubuntu4.1+medibuntu1
libpostproc1d (version 3:0.cvs20070307-5ubuntu4.1) will be upgraded to version 3:0.cvs20070307-5ubuntu4.1+medibuntu1
libswscale1d (version 3:0.cvs20070307-5ubuntu4.1) will be upgraded to version 3:0.cvs20070307-5ubuntu4.1+medibuntu1

 I appreciate any advice here. I've never gotten this type of activity regarding unauthenticated updates outside of swift weasel.

---

### Post by Fixman on 2008-08-11
Yes you should.

---

### Post by dskyracer on 2008-08-11
Ok but why can't it be authenticated? I'd feel better if I didn't get such doubts about doing an update like this.

---

### Post by brian_p on 2008-08-11
> **dskyracer said:**
> Ok but why can't it be authenticated? I'd feel better if I didn't get such doubts about doing an update like this.

Do you have the keyring package for that repository installed? I don't know its name but you can check what is available with

```
apt-cache search key repository
```

---

### Post by dskyracer on 2008-08-12
This morning I went ahead and installed the updates anyway..this time when I did  I wasn't shown a message saying the updates weren't able to be authenticated..afterwards I ran the code given in the previous post and this is what it showed which didn't mean much to me..I remain a noob but hope to keep learning as time goes by..

devscripts - Scripts to make the life of a Debian Package maintainer easier
xkb-data - X Keyboard Extension (XKB) configuration data
jed-extra - collection of useful Jed modes and utilities
knowledgetree - web-based Knowledge Management
slbackup-php - A web-based administration tool for slbackup written in php
medibuntu-keyring - GnuPG key of the Medibuntu repository



 In any case I am very satisfied with Ubuntu for I can do pretty much everything I want to do with a computer, ie, email, photos, music, video, spreadsheets, word processing..thanks for making it all possible.

---

### Post by Joeb454 on 2008-08-12
It's because you didn't have the key for the medibuntu repo's. Though it seems that you now have that key :)

---

