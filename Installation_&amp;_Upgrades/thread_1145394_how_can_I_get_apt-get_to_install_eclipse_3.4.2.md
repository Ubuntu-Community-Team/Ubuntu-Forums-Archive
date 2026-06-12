---
title: "how can I get apt-get to install eclipse 3.4.2"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by amadain17 on 2009-05-01
I have Jaunty Jackalope and wanted to upgrade my eclipse install to 3.4.2 using apt-get. 
The only eclipse apt-get will install is eclipse 3.2.2 and after that it states ' eclipse is already the newest version' when you try to upgrade it to the latest version. 
I want to upgrade my eclipse rather than uninstalling it and reinstalling eclipse 3.4.2 as I have many different plugins and settings I want to keep. 
Any suggestions?

---

### Post by gocek on 2009-05-01
As far as I know there's no such possibility. I read somewhere that there's not enough manpower to keep eclipse packages up to date. So you probably won't get 3.4.2 in the repositories anytime soon. 
But... installing it manually means literally place somewhere one file. Not sure how it goes with the plugins unfortunatelly.

---

### Post by stretch427 on 2009-05-01
Have you tried updating?
```

 sudo apt-get update
sudo apt-get install eclipse
sudo apt-get upgrade

```

---

### Post by Sense on 2009-06-01
> **stretch427 said:**
> Have you tried updating?
```

 sudo apt-get update
sudo apt-get install eclipse
sudo apt-get upgrade

```

That wouldn't make a difference since 3.4 just isn't in the repository. Unless you add a repository that does contain the newest version it has no use to try to update it using apt.

One such repository is the PPA of the Eclipse Team: [https://launchpad.net/~eclipse-team/+archive/ppa](https://launchpad.net/~eclipse-team/+archive/ppa)
Unfortunately its 64bit build failed, so you'll have to use the official downloads at [www.eclipse.org](www.eclipse.org), which are the directories with already compiled executables. You can just execute the included binaries.

---

