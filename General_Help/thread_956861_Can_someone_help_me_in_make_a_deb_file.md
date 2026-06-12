---
title: "Can someone help me in make a deb file?"
date: 2008-10-23
forum: General Help
---

### Post by cchester on 2008-10-23
Hello,

I am looking for some help on this program I just installed.

I have the source files I think and the creator said he wasn't able to make a deb file himself so i thought i would give it a shot.

The program is TV-Viewer from this site [http://home.arcor.de/saedelaere/download_eng.html]("http://home.arcor.de/saedelaere/download_eng.html") .

It was a little of a pain to get installed and I ended up having to install TCL from source. I would like to have a .deb file that would take care of everything instead and make it easier to install.

If possible even a script to install it and everything required would even work.

Any ideas to make it more automated would be great.

So if anyone could help me out that would be great and I would post the .deb files for others wanting it.

Thanks for any help.

---

### Post by spiderbatdad on 2008-10-23
[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

---

### Post by xtracool_protik on 2008-10-23
How about "alien". I've successfully converted few rpms to deb but I have not tried using it for packaging. you can give it a try even I will like to see the results.
So if I can I'll try to make a package and will let u know

---

### Post by spiderbatdad on 2008-10-23
> **xtracool_protik said:**
> How about "alien". I've successfully converted few rpms to deb but I have not tried using it for packaging. you can give it a try even I will like to see the results.
So if I can I'll try to make a package and will let u know

Alien is not for converting source code to deb. It is a hack for converting rpm to deb...and not a good one. To simply install source as deb ( for easy removal, and inclusion in synaptic package manager ) use "checkinstall:"  
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

The links in the previous post are concerned with actual packaging for archiving and distribution...something the op expressed an interest in doing.

---

### Post by cchester on 2008-10-23
Hello,

I forgot to say the only thing for installing the program once it is extracted is a ./configure. It doesn't include any make files and such like other programs you install from source.

So I guess i would actually need to know how to build a deb file to be able distribute from a ./configure file, maybe?

Any more help would be great, Thanks.

Also spiderbatdad is this "checkinstall:"https://help.ubuntu.com/community/CheckInstall
 a web site you were suggesting I go to or something else?

Thanks for the reply just need some clearing up on what you were saying to do.

---

