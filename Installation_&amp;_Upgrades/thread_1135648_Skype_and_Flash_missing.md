---
title: "Skype and Flash missing ?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by dj.dule on 2009-04-24
Hi all,

I just installed 9.04 netbook remix. It is claimed for Desktop edition ([http://www.ubuntu.com/news/ubuntu-9.04-desktop](http://www.ubuntu.com/news/ubuntu-9.04-desktop)) they support skype:

“With every release, we see Ubuntu Desktop Edition make significant steps forward in appealing to mainstream computer users. With access to the latest office productivity suite, support for Skype and Adobe Flash..."

But both of them are missing. Am I making a mistake somewhere or ? I just added flash from tar.gz, but I suppose there is some better way to install it (.deb downloaded from Adobe site claims some dependencies problem). 

Same with Skype, dependencies problem. Should I install static version ?

---

### Post by Partyboi2 on 2009-04-26
Have you added the 3rd party repo to install skype?
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

With adobe flash make sure you have the multiverse repo enabled in Software Sources (System>Admin>Software Sources>1st Tab)
then search for flashplugin-nonfree in synaptic or open a terminal and install with
```
sudo apt-get install flashplugin-nonfree
```

---

