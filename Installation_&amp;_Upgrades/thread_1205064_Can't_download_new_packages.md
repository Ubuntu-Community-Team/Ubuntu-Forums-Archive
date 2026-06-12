---
title: "Can't download new packages"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by MalcolmCowen on 2009-07-05
I try to download a new package (bash documentation) using Synaptic Package Manager.
When I press Apply I get 
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/bash/bash-doc_3.2-0ubuntu11_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/bash/bash-doc_3.2-0ubuntu11_all.deb)
  404 Not Found


Notes:
1: I have previously done downloads on this system with no problem.
2: Another Linux system also fails to download anything.

Has the address of the update server changed?

---

### Post by taurus on 2009-07-05
Maybe that specific server is down.  Try using another server in System -> Administration -> Software Sources.

---

### Post by tachuela on 2009-07-05
Check your connection too; just in case.

---

### Post by MalcolmCowen on 2009-07-05
> **tachuela said:**
> Check your connection too; just in case.

First thing I thought of.
Firefox still works OK, and I can reach these fora.

---

### Post by drs305 on 2009-07-05
That file no longer exists on the current servers. I checked the gb and us servers. I did locate it at:
[http://old-releases.ubuntu.com/ubuntu/pool/main/b/bash/](http://old-releases.ubuntu.com/ubuntu/pool/main/b/bash/)

It's the "11" version that isn't available anywhere but on the 'old-releases' server. Other versions are available on the server you are trying to obtain it from.

---

### Post by sanderj on 2009-07-05
> **MalcolmCowen said:**
> I try to download a new package (bash documentation) using Synaptic Package Manager.
When I press Apply I get 
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/bash/bash-doc_3.2-0ubuntu11_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/bash/bash-doc_3.2-0ubuntu11_all.deb)
  404 Not Found


Notes:
1: I have previously done downloads on this system with no problem.
2: Another Linux system also fails to download anything.

Has the address of the update server changed?

Which Ubuntu version are you using? That file bash-doc_3.2-0ubuntu11_all.deb was provided with gutsy / 7.10, which is not supported anymore.

---

### Post by MalcolmCowen on 2009-07-06
I'm using Gutsy, and the other system I tried was using Jaunty.

How would I get at the sources on [http://old-releases.ubuntu.com/ubuntu/pool/main/b/bash/](http://old-releases.ubuntu.com/ubuntu/pool/main/b/bash/) ?
I assumed Admin / Software Sources ( or repositories ) would do it.
but I can't see a way to specify a URL, just choose one from a list of sites.

---

### Post by drs305 on 2009-07-06
> **MalcolmCowen said:**
> How would I get at the sources on [http://old-releases.ubuntu.com/ubuntu/pool/main/b/bash/](http://old-releases.ubuntu.com/ubuntu/pool/main/b/bash/) ?

One way, without command line instructions, would be to use a text editor and search replace your /etc/apt/sources.list, changing all the references from the current repository to old-releases. Here is a sample entry:


```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.current
gksudo gedit /etc/apt/sources.list

```

> 
find: 
[http://**us.archive](http://**us.archive)**.ubuntu.com/ubuntu/             # or your current server if different
replace:
[http://**old-releases](http://**old-releases)**.ubuntu.com/ubuntu/ 

---

### Post by MalcolmCowen on 2009-07-08
Thanks folks.
That answers the question for my server running Gutsy - I should update it!

The other server with similar issues is running Hardy Heron.
I looked for copies of package files for this release, but could not find them.

eg 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.8-1ubuntu0.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.8-1ubuntu0.5_i386.deb)
  404 Not Found

Any idea where I could find these?

Malcolm

---

