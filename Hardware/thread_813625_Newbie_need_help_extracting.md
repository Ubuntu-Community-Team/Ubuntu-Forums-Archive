---
title: "Newbie need help extracting"
date: 2008-05-31
forum: Hardware
---

### Post by FOBoi1122 on 2008-05-31
Hello All,

I've been trying to set up the tablet function on my T4220, and i'm having trouble figuring out how to extract the ubuntu files from [http://fjbtndrv.wiki.sourceforge.net/packages](http://fjbtndrv.wiki.sourceforge.net/packages) 

it says that:
hardy
To get access to the repository, open a terminal and and run these commands:

wget -O - [http://home.versanet.de/~khnz15/archive.key](http://home.versanet.de/~khnz15/archive.key) | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/fjbtndrv.list [http://home.versanet.de/~khnz15/hardy.list](http://home.versanet.de/~khnz15/hardy.list)

I don't really know what to do after that? The instructions want me to compile those files, but i'm not sure what that requires.

My reference site is this: [https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)

---

### Post by Nepherte on 2008-05-31
Those commands will add the package list to apt. Now you have to update your list with:
```
sudo apt-get update
```

You can now install the packages from that repository with:
```
sudo apt-get install packagename
```

Or you can use synaptic as well, if you want a graphical way. This requires knowing the package names you want to install of course.

---

