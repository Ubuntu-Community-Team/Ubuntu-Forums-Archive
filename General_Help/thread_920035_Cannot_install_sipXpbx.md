---
title: "Cannot install sipXpbx"
date: 2008-09-14
forum: General Help
---

### Post by Cowpoke on 2008-09-14
Hello masters!

I added repositories to my sources.list file, I d/l'd the unmet dependencies pckg's from scm.calivia.com (I manually moved them to the /var/cache/apt/archives directory).  I executed ```
apt-get update
``` and ```
apt-get autoremove
```  Still, everytime I try to run ```
apt-get install sipXpbx
``` I get feed back like this:
```
The following packages have unmet dependencies:
  sipxpbx: Depends: libsipxcommserver1 but it is not going to be installed
           Depends: sipxregistry (>= 3.6) but it is not going to be installed
           Depends: sipxproxy (>= 3.6) but it is not going to be installed
           Depends: sipxpublisher (>= 3.6) but it is not going to be installed
           Depends: sipxvxml (>= 3.6) but it is not going to be installed
E: Broken packages

```

Please help me resolve this -- I am at the end of my line! ](*,)
And thx in advance!

---

### Post by cariboo on 2008-09-14
You will have to install the dependancies manually using either gdebi or dpkg. Double clicking on the file will bring up gdebi, which is probably the easiest way to install a .deb

Jim

---

### Post by Cowpoke on 2008-09-16
> **cariboo907 said:**
> You will have to install the dependancies manually using either gdebi or dpkg. Double clicking on the file will bring up gdebi, which is probably the easiest way to install a .deb

Jim

Thanks for the tip!

Try as I might, my efforts are not improving though...  I now have a problem with a ***very bad or inconsistent state***.  Here is the result of my manual install attempt:
```

$ sudo su
$ dpkg -i sipxpbx_3.8.0-1_i386.deb 
(Reading database ... 178420 files and directories currently installed.)
Preparing to replace sipxpbx 3.8.0-1 (using sipxpbx_3.8.0-1_i386.deb) ...
Unpacking replacement sipxpbx ...
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing sipxpbx_3.8.0-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 sipxpbx_3.8.0-1_i386.deb

```

I do not know how to clean this up.  The box suggests that sipxpbx should be reinstalled, but it cannot find an archive for it...

Am I perhaps using a less stable or outdated release?  I am quite at sea with this right now :frown:.

Thanks again for your quick response!

---

