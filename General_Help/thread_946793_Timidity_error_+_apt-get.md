---
title: "Timidity error + apt-get"
date: 2008-10-13
forum: General Help
---

### Post by Gezzy on 2008-10-13
Hi, I hope someone can help me :)

Cant really remember what i did to make this start but
everytime I use add/remove programs, synaptic package manager or apt-get
i get this error : 

```
Setting up timidity (2.13.2-19ubuntu1) ...
   ...fail!
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I am clueless as to what to do, I tried removing, reinstalling timidity without luck.

---

### Post by Gezzy on 2008-10-13
bump? :)

---

### Post by Gezzy on 2008-10-15
I've tried a few things without luck.

synaptic package manager - edit - fix broken packages

and

sudo dpkg --configure -a
sudo apt-get install -f

which I found in this forum, but neither of those helped me :\

I did manage to uninstall timidity, but then I found out I 
need it to play skulltag :)

So, timidity is reinstalled, and making these errors again.


I hope someone can help me with this issue, cause I find it really annoying :)

---

### Post by Gezzy on 2008-10-16
no one ? :(
oh well, guess i'll just reinstall *sigh* :D

---

### Post by christophermluna on 2008-10-18
I have the same error.  I wonder what could be the matter.  When I reinstall, it just gives me the same error, whether I do it through the package manager or the terminal.

The strange thing is, the program itself seems to work, rendering midi just fine.  It just spouts errors.

---

### Post by VoiceOvGod on 2008-10-28
I get the error too.

Looks like *somebody* knows about it:

[https://bugs.launchpad.net/ubuntu/+bug/270582](https://bugs.launchpad.net/ubuntu/+bug/270582)

---

