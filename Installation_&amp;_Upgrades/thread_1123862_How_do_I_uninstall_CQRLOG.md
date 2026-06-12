---
title: "How do I uninstall CQRLOG?"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by bart1452 on 2009-04-12
I installed third-party CQRLOG with it's included installer. Dpkg, apt-get and the Synaptics Package Manager don't see it. I used <locate> to see where it's files are, but how do I remove them all? It appears most are in a folder I created but I don't want to leave any orphans around. I don't care about the log file it created because I still rely on a Windows program for now.

There is a new version with some bug fixes and I would like to set it up in some sort of repository and use the apt-get installer or synaptics package manager to handle the new version so I don't repeat the problem.

Dave

---

### Post by tommcd on 2009-04-12
Did you install using one of the .tar.gz installers from here:
[http://www.cqrlog.com/?q=node/4](http://www.cqrlog.com/?q=node/4)
What is the output of: **locate cqrlog**?
Did you install it using: ./configure && make && sudo make install? Or dod you install it as a regular user without sudo.
Hopefully it all went to one directory that you can just remove.

In the future, you can use **checkinstall** instead of "make install" when compiling from source. This will install it as a .deb package that you can remove with dpkg, apt-get, or synaptic:
[https://help.ubuntu.com/community/forum/software/CheckInstall](https://help.ubuntu.com/community/forum/software/CheckInstall)

---

### Post by bart1452 on 2009-04-12
Thank you Tommcd,

It's been a few months since I installed it so I don't remember any details, except that I used the installer from the website you show a link to, though the program version was different. The output of locate is way too big to post here. But it's all mostly in two files: trash and a folder in my user account. A couple more show up in the nautilus meta files. It might just be a matter of deleting the trash and the folder and then clearing the nautilus files. But I'm not sure that's all there is to it. Does the installer simply make a folder and unpack everything there? I don't know how those things work. I'm still fairly new to Linux.

---

### Post by tommcd on 2009-04-13
With a .tar.gz source code installer, usually you would install it like this:
```

tar -xzf cqrlog.tar.gz

```
This would create a folder named cqrlog. Then you would cd into that folder and run:
```

./configure
make
sudo make install

```
Usually, a program installed this way would go to /usr/local/cqrlog, with a symlink to the executable in /usr/bin/cqrlog or /usr/local/bin/cqrlog.
If you did not install it with sudo, then it would go in your home directory. Is this what you mean by:
> But it's all mostly in two files: trash and a folder in my user account..
Anything in trash can be safely deleted.
Anything in your home directory can be safely deleted.
Look in the folder for the program in your home directory. Usually there will be a **readme** or **install** file in there. It may tell you how to uninstall it. But since you say it is in your home directory (if I read your post right) the uninstaller (if there is one) may not apply to your situation anyway.

As for the nautilus meta files, do you mean they are in ~/.nautilus/metafiles? If so, then you can delete those as well. Open nautilus and select view > show hidden files. Navigate to ~/.nautilus/metafiles and delete them. They are harmless anyway afaik.
 Don't delete *everything* in ~/.nautilus/metafiles. Just anything for cqrlog if you want to.
 See these 2 threads about nautilus meta files:
[http://ubuntuforums.org/showthread.php?t=1068084](http://ubuntuforums.org/showthread.php?t=1068084)
[http://ubuntuforums.org/showthread.php?t=671838](http://ubuntuforums.org/showthread.php?t=671838)

---

### Post by bart1452 on 2009-04-14
Thank you! I opened the install file with a text editor and it only contained this:

No installation required, just untar into your home folder and run cqrlog.sh. 
Hamlib is the only dependency, it must be installed even if no radio control
required.
Also libstdc++5 library is required!.

I didn't realize it was basically a readme file. The readme file only said the program was free. You described the meta files perfectly. If it runs from Cqlog.sh, then does that complicate installing the new version the way you said?

Thanks for the instructions on how to install a tar ball with so it can be uninstalled with a package manager.

---

### Post by tommcd on 2009-04-15
> **bart1452 said:**
> perfectly. If it runs from Cqlog.sh, then does that complicate installing the new version the way you said?

If the cqrlog directory is only contained within your home directory, and you delete that, then it should not pose a problem if you install a newer version of cqrlog.
You may also have a ~/,cqrlog directory in your home directory that would have your saved preferences in it. It should be ok to just save it, so your preferences would be retained. Or you could just delete that also if you want.

---

