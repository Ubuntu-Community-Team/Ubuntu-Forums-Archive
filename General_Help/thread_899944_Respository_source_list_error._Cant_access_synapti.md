---
title: "Respository source list error. Cant access synaptic"
date: 2008-08-24
forum: General Help
---

### Post by Horacioklm on 2008-08-24
Hi. i got this problem while trying open the synaptic package manager:

E: Tipo '--18:07:02--' desconocido en la línea 1 de lista de fuentes /etc/apt/sources.list.d/medibuntu.list
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.
E: _cache->open() failed, please report.

(sorry... is spanish =P i'll translate it)

E: type '--18:07:02--' unknown in line 1 of source list /etc/apt/sources.list.d/medibuntu.list
E: could not read source list.
Go to repository dialog to correct the problem.
E: _cache->open() failed, please report.

------------------------------------------------------------------

I ran this in the terminal to see what was in the list but after that i didnt know what to do to solve the problem:

cat /etc/apt/sources.list

and the result was this:

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
deb-src [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy main restricted
deb-src [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-updates main restricted
deb-src [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy universe
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy multiverse
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-security main restricted
deb-src [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-security universe
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://tezcatl.fciencias.unam.mx/ubuntu/](http://tezcatl.fciencias.unam.mx/ubuntu/) hardy-security multiverse

-----------------------------------------------------------------------

Thanks for your advises and counsels

Really need help here, i cant continue installing programs anymore

---

### Post by mssever on 2008-08-24
Please post the contents of /etc/apt/sources.list.d/medibuntu.list

---

### Post by drs305 on 2008-08-24
It looks like a medibuntu source problem. If you use hardy, the way to include the Medibuntu repository changed with the introduction of Hardy. If you used old commands to add it the medibuntu.list may not be correct. The following will install  the Medibuntu Repository following the guidance from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). 

```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-old 
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by Elfy on 2008-08-24
Open the file to edit it - delete all the contents of the file and save it. Open a terminal and run 

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

Once save run these commands seperately```

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Horacioklm on 2008-08-24
Hi, thanks for passing by. I check it... but is empty =(.... dont know why

---

### Post by Horacioklm on 2008-08-24
Well, i think yo are right drs305. I think i used old commands.

Forestpixie, i did as you said until the running commands stage. I just tryed to erase the list contents but, as i post before is was empty already.

Should i continue executing the other commands??

---

### Post by drs305 on 2008-08-24
Horacioklm

If you run the three lines in my post in order it should restore a working sources.list and allow access to medibuntu (if you are using hardy)

---

### Post by Horacioklm on 2008-08-24
then i will run them and let you know the results. Thanks

---

### Post by Horacioklm on 2008-08-24
WOW THANKS A LOT MAN!!! it is solved now. I really appreciate your help.



By the way. How can i learn more about commands in linux. I just started use ubuntu a week ago but the part of commands is just 98% unknown to me.

---

### Post by mssever on 2008-08-24
> **Horacioklm said:**
> WOW THANKS A LOT MAN!!! it is solved now. I really appreciate your help.Glad you got it sorted out. Now you can mark this thread as solved.
> By the way. How can i learn more about commands in linux. I just started use ubuntu a week ago but the part of commands is just 98% unknown to me.Time and experience. :) Use [FONT=Courier New]man command[/FONT] and [FONT=Courier New]command --help[/FONT] for documentation on specific commands. Use apropos to search for commands (though the search isn't the greatest). Google for Linux commands and bash.

---

### Post by drs305 on 2008-08-24
> **Horacioklm said:**
> WOW THANKS A LOT MAN!!! it is solved now. I really appreciate your help.

By the way. How can i learn more about commands in linux. I just started use ubuntu a week ago but the part of commands is just 98% unknown to me.

I've learned the most by having problems! ;-) That led to helping other people solving their problems, where I learn every day. There are a lot of online guides but the way I've learned is to google whatever specific thing I need to know about. I've got lots of bookmarks, but most of them deal with a specific topic (fstab, grub, etc) and were written by regular users in non-technical english.

I generally search these forums first, then go to google if I can't find the answer I'm looking for. 

For specific commands, each one has a *man* page that contains information about what the command does and the options associated with it. Some man pages are better than others about explaining the command.  To access the man page, just type "man" and the command in a terminal (example:  man find ). 

Anyway, glad the commands worked. Welcome to ubuntu!

---

### Post by Horacioklm on 2008-08-24
> **drs305 said:**
> I've learned the most by having problems! ;-) That led to helping other people solving their problems, where I learn every day. There are a lot of online guides but the way I've learned is to google whatever specific thing I need to know about. I've got lots of bookmarks, but most of them deal with a specific topic (fstab, grub, etc) and were written by regular users in non-technical english.

I generally search these forums first, then go to google if I can't find the answer I'm looking for. 

For specific commands, each one has a *man* page that contains information about what the command does and the options associated with it. Some man pages are better than others about explaining the command.  To access the man page, just type "man" and the command in a terminal (example:  man find ). 

Anyway, glad the commands worked. Welcome to ubuntu!

Ohh, i see, thanks a lot again. I am just affraid of spoiling the system up by experimenting with the commands =P

But i'll try as you did. Thanks a lot again pal, thanks for the welcome to ubuntu. I am starting to love it XD

---

### Post by drs305 on 2008-08-24
> **Horacioklm said:**
> 

I felt like my answer was inadequate. Here are some of my standard references. A lot of good people have volunteered their time to produce them for our use:

[Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

[Ubuntu Chat/IRC]("https://help.ubuntu.com/community/InternetRelayChat")

[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

[Linux Online Courses]("http://www.linux.org/lessons/")

[How to Install Anything]("http://monkeyblog.org/ubuntu/installing/")

There are lots of great sites out there, you can even search this forum as I've seen pages of recommended sites for beginners.

---

