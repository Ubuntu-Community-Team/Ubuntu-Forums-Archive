---
title: "Which filesystem?"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by apparle on 2009-04-20
which filesystem should I choose

EXT3: Have been using it till now
EXT4: Coming in 9.04
XFS: Many say it's got speed.


Please tell me various features of above all and which to choose and why?

---

### Post by Guitar John on 2009-04-20
Read [this]("http://ubuntulinuxtipstricks.blogspot.com/2009/04/ext3-4-and-dataguarded.html").

---

### Post by apparle on 2009-04-20
> **Guitar John said:**
> Read [this]("http://ubuntulinuxtipstricks.blogspot.com/2009/04/ext3-4-and-dataguarded.html").

TEll something which a normal person can understand.......not something for a filesystem maker

---

### Post by Guitar John on 2009-04-20
Actually, I *am* a normal person, the last time I checked.

I suggested that article because I thought it would explain it better than I could.  I barely understand this myself, but I thought I would give it a shot since nobody more knowledgeable was chiming in (and still hasn't).

According to Wikipedia, [Metadata]("http://en.wikipedia.org/wiki/Metadata") is data about other data.  So according to our blogger:

> only writes the metadata to the journal—not the *actual* data

which means - as I understand it - you could potentially experience data loss in the event of a crash.

---

### Post by 00b00nt00 on 2009-04-21
EXT3

1) It's stable.

2) It's the default for Ubuntu.

3) No reason to change.

---

