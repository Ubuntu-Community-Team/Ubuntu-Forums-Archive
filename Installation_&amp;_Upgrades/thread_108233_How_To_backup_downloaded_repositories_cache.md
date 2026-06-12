---
title: "How To backup downloaded repositories cache"
date: 2005-12-25
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2005-12-25
Hi all,
         Read the manual which giives this :-
```

mkdir -p $HOME/backup/var/lib/
sudo cp -R /var/lib/apt/ $HOME/backup/var/lib/
mkdir -p $HOME/backup/var/cache/
sudo cp -R /var/cache/apt/ $HOME/backup/var/cache/
mkdir -p $HOME/backup/etc/apt
sudo cp -R /etc/apt/ $HOME/backup/etc/
sudo chown -R $USER $HOME/backup/
``` 
Now will be doing this but would like to know what the $ is for? This was my question but while doing it it's some kind of an environment variable  which resolves to the user who's giving the commands. The real questions are :-

Q1. This is one-time deal now all the downloads I do get backup now or something has to be done when I download new stuff.
Q2. Now all this backuped files of the archive. If I wanna make an CD2 or local repositery what else do I have to do?
Q3.  How can I come to know from when the archive is functioning. I did an apt-get clean sometime back, but is there anyway to know from when the archive is functioning?
Q4. How can I know the size of the whole thing when I burn it on the CD.  I'm sure there's a good HOWTO of Q2 but haven't been able to find it. Thanx in advance.

---

### Post by az on 2005-12-25
[QUOTE=shirishag75]Hi all,
         Read the manual which giives this :-
```

mkdir -p $HOME/backup/var/lib/
sudo cp -R /var/lib/apt/ $HOME/backup/var/lib/
mkdir -p $HOME/backup/var/cache/
sudo cp -R /var/cache/apt/ $HOME/backup/var/cache/
mkdir -p $HOME/backup/etc/apt
sudo cp -R /etc/apt/ $HOME/backup/etc/
sudo chown -R $USER $HOME/backup/
``` 
Now will be doing this but would like to know what the $ is for? This was my question but while doing it it's some kind of an environment variable  which resolves to the user who's giving the commands. The real questions are :-

Q1. This is one-time deal now all the downloads I do get backup now or something has to be done when I download new stuff.
Q2. Now all this backuped files of the archive. If I wanna make an CD2 or local repositery what else do I have to do?
Q3.  How can I come to know from when the archive is functioning. I did an apt-get clean sometime back, but is there anyway to know from when the archive is functioning?
Q4. How can I know the size of the whole thing when I burn it on the CD.  I'm sure there's a good HOWTO of Q2 but haven't been able to find it. Thanx in advance.[/QUOTE]

1.  You will have to run this script to backup the stuff you dowload.  There is no way for this script to know when you download something new.
2.  Forget about this and see [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)
3.  Are you asking if all the dependancies are still there, on your hard drive?  Well if you did apt-get clean, no.
4.  du -h $HOME/backup/

---

