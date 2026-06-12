---
title: "error with traceroute and iputils-tracepath when upgrading in 9.10"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by sverre76 on 2009-10-23
Hi!

I have been upgrading to 9.10 development version and I am now having issues with the update manager. Every time I run the manager it exits with the following messages:

(trying to translate this from swedish)
> Configuring iputils-tracepath (3:20071127-1build1) ...
update-alternatives: error: the alternative link /usr/bin/traceroute6 is already handled by traceroute6.before_restore_2009-03-02_22.32.44.435893.
dpkg: error handling iputils-tracepath (--configure):
 subprocess installed post-installation-script exited with error status 2
Configuring traceroute (2.0.12-2) ...
update-alternatives: error: the alternative link /usr/bin/traceroute6 is already handled by traceroute6.before_restore_2009-03-02_22.32.44.435893.
dpkg: error handling traceroute (--configure):
 subprocess installed post-installation-ckript exited with error status 2
Error occured handling:
 iputils-tracepath
 traceroute
E: Sub-process /usr/bin/dpkg returned an error code (1)


Is there a way to remove or reinstall these packages without jeopardizing the entire system?

---

### Post by zvacet on 2009-10-23
```
sudo dpkg --configure -a
```

---

### Post by sverre76 on 2009-10-23
Thanks for the reply!

I get the exact same error message as above when running sudo dpkg --configure -a

So that doesn't seem to do it....

Anything else I can try?

Regards
Daniel

---

### Post by sverre76 on 2009-10-26
Bump. Anyone else have an idea about how to solve the post-process errors  described above?

It seems as I can not remove the packages and then install them again without affecting (and removign) the entire ubuntu-desktop package. So is there another way?

Regards
Daniel

---

