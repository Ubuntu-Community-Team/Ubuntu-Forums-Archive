---
title: "can't install a package - &quot;Starting administrati...&quot; then nothing"
date: 2008-08-29
forum: General Help
---

### Post by marble3636 on 2008-08-29
I was really excited to get started with ubuntu but I hit a brick wall right out of the gate.

I tried to install opera - downloaded the package, no problem. Clicked on the .deb file, package install manager thing loaded. Great. I tell it to install...

I get an item in my taskbar that says "Starting Administrati..." then nothing happens. No password prompt, no errors anywhere I can see, nothing.

*** I have googled and found many people have this problem when the cause is an extra domain suffix on their machine name in their hosts file - this is NOT what my problem is, I have checked this and it is as it should be ***

I found one thread somewhere where a person was having the issue as I am (where it was NOT the hosts file issue) and there was no resolution, so I have no idea where to go from here.

Any help would be greatly appreciated.

---

### Post by amedac on 2008-08-29
open terminal and type opera. You should get some errors, then google or write errors here, someone will help

---

### Post by 3rdalbum on 2008-08-29
I'm not sure what the problem is, but if you can open Synaptic package manager, you should enable the "Partner" repository. Opera is available in there.

If you want to install that Debian package, you could go to a terminal and type:

```
sudo dpkg -i *.deb
```

which will manually install all the Debian packages that are in your home directory. But I believe it will probably throw up some error messages that will be of help fixing the real problem.

---

### Post by phoenix116 on 2008-08-29
you should generally install programs by synaptic or from the command line with "sudo apt-get install [program]".

If you cant find opera, just do what 3rdalbum said

---

