---
title: "svn: Unrecognized URL scheme..."
date: 2008-10-14
forum: General Help
---

### Post by RATM_Owns on 2008-10-14
```
andy@compy386 ~ $ svn co http://svn.gnewsense.svnhopper.net/gnewsense/builder/trunk builder
svn: Unrecognized URL scheme for 'http://svn.gnewsense.svnhopper.net/gnewsense/builder/trunk'
```

It's been doing that for everything.

I'm pretty sure it's a HTTP error and I need to do --with-ssl when configuring.
So maybe that's the answer.

```
andy@compy386 ~ $ ./configure --with-ssl
...
   svn co \
    http://svn.apache.org/repos/asf/apr/apr-util/branches/0.9.x \
    apr-util

configure: error: no suitable apr found
andy@compy386 ~/subversion-1.5.3 $    svn co \
>     http://svn.apache.org/repos/asf/apr/apr-util/branches/0.9.x \
>     apr-util
svn: Unrecognized URL scheme for 'http://svn.apache.org/repos/asf/apr/apr-util/branches/0.9.x'
```

BZZT! So basically, I'm stuck here without SVN.

Any help? Maybe tarring up the APR stuff and uploading somewhere?

---

### Post by geirha on 2008-10-14
What's the output of these?
```
svn --version
type -a svn
```

svn from the subversion package in the repository should have the proper module to handle http.

---

### Post by RATM_Owns on 2008-10-14
svn --version
```
andy@compy386 ~ $ svn --version
svn, version 1.5.3 (r33570)
   compiled Oct 12 2008, 19:28:20

Copyright (C) 2000-2008 CollabNet.
Subversion is open source software, see http://subversion.tigris.org/
This product includes software developed by CollabNet (http://www.Collab.Net/).

The following repository access (RA) modules are available:

* ra_svn : Module for accessing a repository using the svn network protocol.
  - handles 'svn' scheme
* ra_local : Module for accessing a repository on local disk.
  - handles 'file' scheme
```

type -a svn
```
andy@compy386 ~ $ type -a svn
svn is /usr/local/bin/svn
svn is /usr/bin/svn
svn is /usr/bin/X11/svn
```

---

### Post by geirha on 2008-10-14
Apparently you have a self compiled (?) version of svn in /usr/local that does not support http. If you use /usr/bin/svn it should work.

---

### Post by RATM_Owns on 2008-10-14
```
sudo rm /usr/local/bin/svn
```
Worked. Yay.

---

### Post by placrsaeed on 2010-01-26
> **geirha said:**
> Apparently you have a self compiled (?) version of svn in /usr/local that does not support http. If you use /usr/bin/svn it should work.

I removed /usr/local/bin/svn but now I'm getting the error; 

saeed@boris:/home$ svn co [http://localhost/svn/tubescraper](http://localhost/svn/tubescraper) tubescraper --username saeed
bash: /usr/local/bin/svn: No such file or directory

How do I tell the system which version of SVN to use? I'm a beginner to Linux so any help is greatly appreciated.

Saeed

---

### Post by geirha on 2010-01-26
> **placrsaeed said:**
> I removed /usr/local/bin/svn but now I'm getting the error; 

saeed@boris:/home$ svn co [http://localhost/svn/tubescraper](http://localhost/svn/tubescraper) tubescraper --username saeed
bash: /usr/local/bin/svn: No such file or directory

How do I tell the system which version of SVN to use? I'm a beginner to Linux so any help is greatly appreciated.


Bash has hashed the last location it used for svn. Either start a new shell (e.g. by opening a new terminal), or type ```
hash -r
``` To make the current shell instance forget all hashes.

---

### Post by placrsaeed on 2010-01-26
Thanks dude.

---

### Post by stevenaaus on 2010-05-24
Just posting about how to install subversion from source with http support.
After unpacking subversion (and probably  apr  apr-util), do

wget [http://www.webdav.org/neon/neon-0.27.2.tar.gz](http://www.webdav.org/neon/neon-0.27.2.tar.gz)
tar xzf neon-0.27.2.tar.gz
mv neon-0.27.2 neon
configure --with-ssl
make install

Crappy build process, i know :<
Big waste of time, just to upgrade my svn client, and you'll still have to resolve whether you install into /usr or /usr/local.

---

### Post by abaa.endless on 2011-10-05
> **geirha said:**
> Bash has hashed the last location it used for svn. Either start a new shell (e.g. by opening a new terminal), or type ```
hash -r
``` To make the current shell instance forget all hashes.

after I remove the usr/local/bin/svn
I got this ERROR "/home/devserve/usvn-1.0/files/svn/testproject/hooks/post-commit: line 49: svn: command not found", I already do the "hash -r" how can i make the svn command. Do I need to reinstal the subversion? It might affects my current repository?  I'am a newbee please help thanks

---

### Post by nothingspecial on 2011-10-05
Rather than digging up an old thread. Please start one of your own.

Closed.

---

