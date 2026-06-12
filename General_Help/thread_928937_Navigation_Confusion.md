---
title: "Navigation Confusion"
date: 2008-09-24
forum: General Help
---

### Post by apocalypsxx on 2008-09-24
Hi..
Well I`ve been trying out some of the most basic commands today in Terminal.
pwd   ls   

etc...

I can move into a Directory from /home/me/Music
for example..
I use the ls command & it shows the sub folders I have in there..so I know
I`m in the correct directory
but when I try to access a sub folder I get File/Directory not known...

eg... 
 
me@n30:~$ pwd
/home/me
me@n30:~$ ls
BACKUP00.XM  Examples       lmms                    nvram      me
cfg          gnash-dbg.log  MAMEUI32.ini            Pictures   me
Desktop      ini            Music                   Public     Templates
Documents    Keyb.cfg       nautilus-debug-log.txt  Skale.cfg  Videos
me@n30:~$ cd ~/Music
me@n30:~/Music$ pwd
/home/me/Music
me@n30:~/Music$ ls
001  DNB001.xm  DRUMNBASS- -BREAKCORE- - IDM
me@n30:~/Music$ cd ~/001
bash: cd: /home/me/001: No such file or directory
me@n30:~/Music$ 
me@n30:~/Music$ 

any help much appreciated..:(

---

### Post by Ryadt on 2008-09-24
Sorry but is 001 a directory?

---

### Post by Steveway on 2008-09-24
You should type cd 001 instead of ~/001.
Because ~ is a short way to type in the directory of your home folder, so with  cd ~/001 you are actually going to /home/username/001 and not /home/username/Music/001.

---

### Post by apocalypsxx on 2008-09-24
> **Steveway said:**
> You should type cd 001 instead of ~/001.
Because ~ is a short way to type in the directory of your home folder, so with  cd ~/001 you are actually going to /home/username/001 and not /home/username/Music/001.

Haha...
Hooray...thnx steveway...

:guitar:

---

### Post by jigsaws on 2008-09-24
Try
ls -l
to be sure of full name.

Other way is
cd 001*
pwd

---

