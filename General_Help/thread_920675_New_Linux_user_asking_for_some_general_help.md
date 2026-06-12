---
title: "New Linux user asking for some general help"
date: 2008-09-15
forum: General Help
---

### Post by TheGoose91 on 2008-09-15
Hey everyone!

I'm new to this forum as well as Linux. Although I've been pondering to install a Linux distro quite a while, I didn't do so until last Friday, when I installed Ubuntu Studio.

As I'm a quite experienced computer user I've been doing pretty well, although some questions have stacked up.

1. In the lib/modules folder, there's two folders: 2.6.24-19-rt and 2.6.24-19-general.

As far as I understand, the -rt one should contain a build folder. It doesn't. Only the -general folder does.

2. How can I check if a package is installed? I know this may sound stupid but I'm not really sure whether the build-essential package is installed.

3. As I'm used to Windows, I realize that this might partly be because I'm unused to Gnome, but I think the computer is much worse organized in Ubuntu. I want total control over my files and folders, and the system seems so messy. Also, when a package is downloaded, I don't even know where it gets. If I extract a tarball, where should I put it? I don't want programs and stuff lying around in my home folder.

Thanks in advance!

---

### Post by TheLions on 2008-09-15
> **TheGoose91 said:**
> Hey everyone!

I'm new to this forum as well as Linux. Although I've been pondering to install a Linux distro quite a while, I didn't do so until last Friday, when I installed Ubuntu Studio.

As I'm a quite experienced computer user I've been doing pretty well, although some questions have stacked up.

1. In the lib/modules folder, there's two folders: 2.6.24-19-rt and 2.6.24-19-general.

As far as I understand, the -rt one should contain a build folder. It doesn't. Only the -general folder does.

2. How can I check if a package is installed? I know this may sound stupid but I'm not really sure whether the build-essential package is installed.

3. As I'm used to Windows, I realize that this might partly be because I'm unused to Gnome, but I think the computer is much worse organized in Ubuntu. I want total control over my files and folders, and the system seems so messy. Also, when a package is downloaded, I don't even know where it gets. If I extract a tarball, where should I put it? I don't want programs and stuff lying around in my home folder.

Thanks in advance!

2. go to synaptec in System->Administration and in search thype the name of package, green box means installed

3. You can always try KDE... 
about tarballs, create some special folder in /home/$username (eg. tarballs)where you'll extract it

---

### Post by TheGoose91 on 2008-09-15
> **TheLions said:**
> 2. go to synaptec in System->Administration and in search thype the name of package, green box means installed

3. You can always try KDE... 
about tarballs, create some special folder in /home/$username (eg. tarballs)where you'll extract it

Thanks... I knew that I could see if I had a package through Synaptec, but I rather wondered if there was a command. I recall I've seen something like checkinstall or so.

About KDE:
I heard from a friend he though it would be more structured... what's your opinions on it? Better or worse? What's the differences? Are there something similiar to Compiz for it?

---

### Post by bingoUV on 2008-09-15
No. 3 is partly the fault of Firefox. I guess you are using the Firefox browser. It downloads everything to Desktop by default. To regain total control, in Firefox, Edit -> Preferences -> Main -> Downloads -> Always ask me where to save files

---

### Post by TheGoose91 on 2008-09-15
> **bingoUV said:**
> No. 3 is partly the fault of Firefox. I guess you are using the Firefox browser. It downloads everything to Desktop by default. To regain total control, in Firefox, Edit -> Preferences -> Main -> Downloads -> Always ask me where to save files



I am indeed, although I don't think that's where the problem is as I usually move my files.

I just don't know where I should "untar" them to... but I guess a decent solution would be to create a folder in the home folder for tars.

---

### Post by koenn on 2008-09-15
> **TheGoose91 said:**
> 

I just don't know where I should "untar" them to... but I guess a decent solution would be to create a folder in the home folder for tars.

You can keep your tarbals wherever you like : somewhere in home if you intend to keep them, or in /tmp if you want to get rid of them after untarring

you'll untar them in 'current directory', so the trick is to go to the destination directory, and untar from there,
like, you have a tarbal in /tmp and you want it unpacked in /usr/bin

cd /usr/bin
tar xvzf /tmp/archive.tar.gz


----
as to where you ***should*** untar them : if it's installing programs from tarbals you're talking about, /usr/bin or /usr/local are 2 reasonable locations.

---

### Post by koenn on 2008-09-15
> **TheGoose91 said:**
> Hey everyone!

I'm new to this forum as well as Linux. Although I've been pondering to install a Linux distro quite a while, I didn't do so until last Friday, when I installed Ubuntu Studio.

As I'm a quite experienced computer user I've been doing pretty well, although some questions have stacked up.

1. In the lib/modules folder, there's two folders: 2.6.24-19-rt and 2.6.24-19-general.

As far as I understand, the -rt one should contain a build folder. It doesn't. Only the -general folder does.

2. How can I check if a package is installed? I know this may sound stupid but I'm not really sure whether the build-essential package is installed.

3. As I'm used to Windows, I realize that this might partly be because I'm unused to Gnome, but I think the computer is much worse organized in Ubuntu. I want total control over my files and folders, and the system seems so messy. Also, when a package is downloaded, I don't even know where it gets. If I extract a tarball, where should I put it? I don't want programs and stuff lying around in my home folder.

Thanks in advance!

sounds like you're planning for compiling source code etc.
just so you know : most software is available in binary forms from the repos (through the package manager), so you shouldn't worry about compiling souce from tarbals, unless you really want to, or you have compelling reasons nod to use the packages from the repos.

---

### Post by TheGoose91 on 2008-09-15
> **koenn said:**
> sounds like you're planning for compiling source code etc.
just so you know : most software is available in binary forms from the repos (through the package manager), so you shouldn't worry about compiling souce from tarbals, unless you really want to, or you have compelling reasons nod to use the packages from the repos.


The game DEFCON, for example, was downloaded as a tarball. I just had to untar it but it annoys me as it's untared, thus stored in /home/tars/DEFCON/
and I'd like to have it in some sort of programs folder like XP. But that might be just because I'm used to Windows.

---

### Post by koenn on 2008-09-15
> **TheGoose91 said:**
> The game DEFCON, for example, was downloaded as a tarball. I just had to untar it but it annoys me as it's untared, thus stored in /home/tars/DEFCON/
and I'd like to have it in some sort of programs folder like XP. But that might be just because I'm used to Windows.

ah, games, the one thing I know nothing about  :)

There actually is a "programs" folder on Linux, it's called /bin (as in binaries). There are some differences with Windows, though :
sysadmin tools go to /sbin (~ super-user binaries ?)
(allmost) all configuration files  are in /etc, log files and other data often ends up in /var, and so on. You can compare this with windows programs that have keys in several parts of the windows registry, and have some dll's and similar files in the windows or windows\system32 folder.

/usr/bin,  /usr/local, or /opt are often used for self-made or compiled software that isn't part of the installed distribution, so those are reasonable locations for anything you add from tarballs and the likes

---

### Post by caljohnsmith on 2008-09-15
To see if a package is installed, and if it is, it will give you the version and other info:
```
apt-cache policy <package name>
```
Is that maybe what you are looking for?

---

### Post by TheGoose91 on 2008-09-15
> **koenn said:**
> ah, games, the one thing I know nothing about  :)

There actually is a "programs" folder on Linux, it's called /bin (as in binaries). There are some differences with Windows, though :
sysadmin tools go to /sbin (~ super-user binaries ?)
(allmost) all configuration files  are in /etc, log files and other data often ends up in /var, and so on. You can compare this with windows programs that have keys in several parts of the windows registry, and have some dll's and similar files in the windows or windows\system32 folder.

/usr/bin,  /usr/local, or /opt are often used for self-made or compiled software that isn't part of the installed distribution, so those are reasonable locations for anything you add from tarballs and the likes

Thanks a lot; that was very helpful! :)
[QUOTE="caljohsmith"]
To see if a package is installed, and if it is, it will give you the version and other info:
```


apt-cache policy <package name>

```
Is that maybe what you are looking for? [/QUOTE]

Also very helpful, thank you, and thank you everybody taking time helping me. This is a very friendly and helpful community and I'm sure I'll enjoy my future forum browsing and ubuntu using a lot. :)

---

