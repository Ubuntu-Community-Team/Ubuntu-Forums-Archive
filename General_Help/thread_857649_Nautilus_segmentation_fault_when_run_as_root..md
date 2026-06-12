---
title: "Nautilus segmentation fault when run as root."
date: 2008-07-12
forum: General Help
---

### Post by u-slayer on 2008-07-12
I just installed a new copy of the 64-bit ubuntu 8.04.1 When I try to run nautilus as root I get this error:

```
root@slayer:~# nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
Segmentation fault
```

---

### Post by u-slayer on 2008-07-12
Im still faulting here. I can get krusader to work, but I don't know how to unzip files with it.

---

### Post by steve8track on 2008-07-12
Sorry noone has given an answer yet.  My best guess is maybe it has something to do with the Seahorse module.  Did you install some extra plugin?  Try uninstalling Seahorse and see if that helps.

What do you need to do in nautilus as root anyway?  Maybe there is another way.  If you only need to unzip something, you could browse to the directory using cd (you could ssh to a remote location too), and then run this command:

```
unzip fileName.zip
```

To access a remote machine, the syntax is:

```
ssh userName@hostName
```

Then use your user's password.  To get to a directory, use:

```
cd /directory/address/
```

Sorry if I'm giving too many little details, I figure it will help people who have never used a command line.

I hope this helps.

Steve

---

### Post by u-slayer on 2008-07-13
I was able to unzip the 7z file already in the command line, but I still want to be able to use nautilus as root. To answer your question, no, I have not installed any funky nautilus extras.:) I'm running on a brand new install of ubuntu 8.04.1 

I need to run nautilus as root because sometimes stuff I mount gets mounted as root and only root can change it. It also makes it easier to work with system files.

---

### Post by ghost_ryder35 on 2008-07-13
are you logging into the box as root?
perhaps
```

sudo nautilus

```
might work better.....

havent had a chance to browse these but a quick google revelaed them
[http://ubuntuforums.org/showthread.php?t=820564&page=6](http://ubuntuforums.org/showthread.php?t=820564&page=6)  (this one says it might be hardware)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg909998.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg909998.html)

---

