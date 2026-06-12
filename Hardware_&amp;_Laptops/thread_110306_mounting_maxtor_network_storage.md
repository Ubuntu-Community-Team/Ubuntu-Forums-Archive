---
title: "mounting maxtor network storage"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by thumper on 2005-12-30
I have a 200 gig network storage drive from maxtor.

It is configured through a web interface and shares space through windows network shares, which I currently mount using smbfs.

I am trying to backup to it using rsync.  The drive seems to loose all the file permissions and won't backup symbolic links.

I have suspicions that it actually uses linux on the inside and I was wondering if there is another way to mount it.

---

### Post by abovett on 2005-12-30
If the Maxtor drive really is a Linux box, I guess it's going to depend on what network file system servers are running on it. I suspect that by default it will only be Samba. I know some Linux based external drives can be hacked to add extra capabilities but I don't know about the Maxtor one.

Andy B

---

### Post by thumper on 2005-12-31
Yeah, I heard that too.

I think the Linksys one has been hacked, but I couldn't find any references to the Maxtor one.  I was hoping someone here may have known something though.

---

