---
title: "mount mac os x install disc in linux"
date: 2008-10-22
forum: General Help
---

### Post by jeffhollon on 2008-10-22
can someone tell me how to mount a mac os x install disc in ubuntu?  I am trying just to make an iso of the disc so i can use it with vmware or virtualbox.  i have installed hfsutils and run sudo hmount /dev/scd0 /media/cdrom0  and get this error.  hmount: /dev/scd0: not a Macintosh HFS volume (Invalid argument)

I have no idea where to go from here.  

I am kind of new so need some step-by-step instructions on how to make these isos from the install discs.  File manager in ubuntu shows the title of the install discs correctly, but will not mount no matter what i do.

thanks,

Jeff

---

### Post by Woody1987 on 2008-10-22
im not sure about this but im assuming that a Mac OSX install disc isnt formatted with a Mac OSX file system. You should only use hmount when mounting a drive or partition that is formatted as a HFS volume. What happens when you just stick the disc in the try? Doesnt it automount? If not try use just the mount command:

```
sudo mount /dev/scd0 /media/cdrom0
```

---

### Post by Woody1987 on 2008-10-22
I should add, if you use virtualbox and presumably vmware then you wont need a disc image if you already have the actual disc, you can install directly from the disc.

---

### Post by niteshifter on 2008-10-22
Hi,

Try installing the package hfsplus.

---

### Post by kellemes on 2008-10-22
OS/X requires Apple hardware.
Installing it on something else is illegal, and probably not even possible.

---

### Post by earthpigg on 2008-10-22
> **kellemes said:**
> OS/X requires Apple hardware.
Installing it on something else is illegal, and probably not even possible.

[it is possible]("http://en.wikipedia.org/wiki/Hackintosh"), and it is merely a violation of the EULA... **not **illegal :)

> The following Leopard 10.5 builds: 9A466, 9A499, 9A527, 9A559 (all pre-release developer builds, the earliest from the WWDC); 9A581 (the 10.5.0 release build), 9B13 (developer), and 9B18 (10.5.1 release build) were successfully installed onto conventional PC hardware. The contributions trickled down into various Mac OSx86 installers, readily available on the internet.

One programmer created one of the first patching processes which made it convenient for users to install Mac OS X onto 3rd party hardware by using a legally obtained, retail version of Apple Mac OS X. It was utilizing the "BrazilMac" patch that many effortless distros of Mac OSx86 came to fruition.



---

### Post by phidia on 2008-10-22
> **earthpigg said:**
> [it is possible]("http://en.wikipedia.org/wiki/Hackintosh"), and it is merely a violation of the EULA... **not **illegal :)

I don't know what the status of running OS X in a virtual environment is, but there are forums. elsewhere, that do discuss these issues.

A violation of a EULA is in fact illegal and threads that discuss **that** here are almost always locked.

---

### Post by bapoumba on 2008-10-23
Good points in posts #5 and 7. Thread closed.

---

