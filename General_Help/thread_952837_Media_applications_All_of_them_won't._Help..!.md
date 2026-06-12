---
title: "Media applications All of them won't. Help..!"
date: 2008-10-19
forum: General Help
---

### Post by wetinwales on 2008-10-19
Hi All
I've come unstuck BIG TIME on media applications:-
As per Synaptics:- Tovid, Open Movie Editor, Dvdrip  do not work - either properly - or at all.
 
eg. Dvdrip installs but will not run, giving a list of applications/packages not installed ... oh yes they are.

Tovid is a pile of crashes and won't burn a dvd with picture and sound in sync.

Open Movie Editor looks fantastic but does not yet play images which are useable.

So.. I'm beginning to wonder whether I have a machine which is not quite up to snuff. Graphics card wrong? ASEUS not up to it???
 
Ubuntu 	Release 8.04(hardy)

	Kernel Linux 2.6.24-19-generic

	GNOME 2.22.3

HARDWARE:-
        Graphics Card NVidia 5900 (from memory)

	Memory:-	1.5GiB

	Processor:-	AMD Athlon(TM) XP 2100+
 
Does any of the above ring any bells. After all, this stuff is working for other people. Just not me. But basic Ubuntu is working well in sooo many good ways.

Thanks
Daf

---

### Post by shawnrgr on 2008-10-19
```
sudo apt-get install nvidia-glx nvidia-settings && sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup && sudo nvidia-xconfig
```

restart x (ctrl+alt+back)

---

