---
title: "Updating, small problem with 2 files"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by ronxp2000 on 2009-08-29
I got the Ubuntu CD in the mail with the latest version.   It installs fine, works great, and is very nice.

It did 217 updates after installation.  All of which I think went well.

I went to do a manual update the next day

and I get this message below about the 2 files listed.

Any ideas?  Thanks.

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

libavc1394-0
libdb4.3

---

### Post by Moop on 2009-08-29
You will get that message if you've added any repositories and didn't add the key for them too. It's usually not a problem to install the packages anyway but it's outside the bounds of good security. 

Have you added any repositories like medibuntu, etc?

---

### Post by ronxp2000 on 2009-08-29
Well the only thing I did with this new install, was I went to play an MP3 file.

It said it had to download some files, so I let it do it.

It was the player that comes with Ubuntu.

So can I undo this, and get that KEY (this is new to me).

Or how do I remove the error?  Or just don't worry about it?

---

### Post by Moop on 2009-08-29
It's ok. You don't need to undo anything. Go to System-Administration-Software Sources and enable the restricted and multiverse repositories, if they aren't already checked. 

That may take care of the error. Either way it's nothing to worry about.

---

