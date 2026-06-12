---
title: "[SOLVED] Compiling Pidgin Help"
date: 2008-10-15
forum: General Help
---

### Post by SirSigma on 2008-10-15
Okay, I followed the instructions I read throughout this thread:

[http://ubuntuforums.org/showthread.php?t=667770](http://ubuntuforums.org/showthread.php?t=667770)

I'm trying to install the Purple Plugins download pack, so I extracted the .tar.gz file to my desktop, extracted, and renamed it to not have numbers in the file name (so I can get there more easily in Terminal).

I did the following first before going to the directory.

```
sudo aptitude install build-essential pidgin-dev checkinstall
```

And then I went to the directory and it seemed to be going fine. But when I tried to configure the first time, it told me I had to get "intltool" installed. I went into Synaptic File Manager to get it.

I tried configure, make, and sudo checkinstall.

This is where I'm confused. Now I get the following and I'm at a loss of what to do next.

```
sigma@sigma-laptop:~/Desktop/purple-plugin_pack$ sudo checkinstall
[sudo] password for sigma: 

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "plugin_pack" is not a
*** Warning: debian policy compliant one. Please specify an alternate one
```

Any suggestions?

Also on a side note, this is my first time trying to compile anything.

---

### Post by Sef on 2008-10-15
What version of Ubuntu do you have?

---

### Post by SirSigma on 2008-10-15
I'm using the latest version. 8.04.

---

### Post by bigbrovar on 2008-10-16
running ```
sudo apt-get build-dep pidgin
``` would install all the dependencies needed for compiling pidgin

---

### Post by Yellow Pasque on 2008-10-16
The warning message is because you put an underscore '_' in the name. This goes against Debian policy.

I was able to build the p-p-p.

Before you try and build/configure, make sure you:
```
sudo apt-get build-dep pidgin
sudo apt-get build-dep pidgin-plugin-pack
```

---

### Post by SirSigma on 2008-10-16
Thanks for the replies.

I solved the problem when I found out the plugins were on Synaptic Manager.

But now I tried to delete the downloaded files just now. But I can't delete them all. They sit in my trash can and they tell me permission denied. Can anybody help me with this now?

Also, thanks for telling me about underscores. I plan to add plugins I can't get from Synaptic Manager.

---

### Post by SirSigma on 2008-10-17
Okay, I hate to bump a post like this, but this is really bothering me.

There are certain files in my "purple-plugin_pack" that won't delete from my trash bin. No matter how hard I try they stay there.

Is there some kind of method of *uncompiling* that I need to do first? I'm only asking because I'm afraid if I delete the file I may end up unwillingly harming something in my system.

I'll provide a screenshot if necessary.

---

### Post by Yellow Pasque on 2008-10-17
[http://ubuntuforums.org/showthread.php?t=885666](http://ubuntuforums.org/showthread.php?t=885666)

---

### Post by SirSigma on 2008-10-17
> **Temüjin said:**
> [http://ubuntuforums.org/showthread.php?t=885666](http://ubuntuforums.org/showthread.php?t=885666)

Thank you! That really helped! Now the file is gone and everything (as far as I know) seems to be working fine.:)

---

### Post by Sef on 2008-10-17
> Okay, I hate to bump a post like this, but this is really bothering me.

Only bump a thread after 24 hours have gone by without a reply.

---

